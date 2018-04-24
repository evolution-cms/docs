##Введение
MODxAPI это попытка реализовать паттерн [Data mapper](https://en.wikipedia.org/wiki/Data_mapper_pattern).
Изначально проектировалось как замена библиотеки DocManager, но в итоге оптимизирован код и заложен потенциал для создания обертки с произвольной логикой для любых таблиц.

###Поддерживаемые модели
*modResource* - Документы (данные из таблицы site_content и site_tmplvar_contentvalues)
*modUsers* - Веб-пользователи (данные из таблиц web_users и web_user_attributes)
*modCategories* - Категории (данные из таблиц categories)
*modChunk* - Чанки (данные из таблиц site_htmlsnippets)
*modModule* - Модули (данные из таблиц site_modules)
*modPlugin* - Плагины (данные из таблиц site_plugins
*modSnippet* - Сниппеты (данные из таблиц site_snippets)
*modTV* - ТВ параметры (данные из таблиц site_tmplvars)
*modTemplate* - Шаблоны (данные из таблиц site_templates)

При желании можно быстро создать свою модель для любой таблицы. Для этого существует заготовка класса autoTable. В самом примитивном случае достаточно указать лишь название вашей таблицы. Взгляните на пример создания модели для таблицы с именем tests:
```
<?php
include_once(MODX_BASE_PATH. "assets/lib/MODxAPI/autoTable.abstract.php");
class modTests extends autoTable
{
    protected $table = "tests";
}
```

### Примеры использования
Методы create, edit, delete, save актуальны для всех моделей. Но в качестве примера будем рассматривать модель modResource.

```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
$doc = new modResource($modx);

/** 
* Подготовить создание документа со следующими данными:
* ID шаблона = 10
* В качестве родителя использовать документ с ID = 1
* pagetitle заголовок документа = example
*/
$doc->create(array(
	'pagetitle' => 'example',
	'template' => 10,
	'parent' => 1
));

/** 
* зменить pagetitle заголовок документа на new title 
*/
$doc->set('pagetitle', 'new title');

/*
* Сохранить документ вызвав события OnBeforeDocFormSave OnDocFormSave,
* но не производить сброс кеша. 
* ID нового документа поместить в переменную id
*/
$id = $doc->save(true, false);

/** 
* Открыть на редактирование документ с ID = 10 
*/ 
$doc->edit(10);

/** 
* Меняем родителя родителя документа
*/
$doc->set('parent', 0);


/*
* Сохраняем документ не вызывая события OnBeforeDocFormSave OnDocFormSave,
* Но при этом производим соброс кеша.
* ID документа сохраняется в переменной $id
*/
$id = $doc->save(false, true);

/***
* Удалить все документы помеченые на удаление.
* При этом вызвать события OnBeforeEmptyTrash и OnEmptyTrash
* Если значение параметра изменить с true на false, то события вызваны не будут, хотя документы удалятся
*/
$doc->clearTrash(true);

/** 
* Удалить документ с ID = 5, минуя корзину
* При этом события OnBeforeEmptyTrash и OnEmptyTrash, будут вызваны.
*/
$doc->delete(5, true);
```

При помощи модели modUsers можно производить не только запись и получение данных, но еще и производить манипуляции с авторизацией:
```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$user = new modUsers($modx);

/**
* Авторизоваться от имени веб-пользователя с ID = 1
*/
$user->authUser(1);

/**
* Проверить статус блокировки веб-пользователя с ID = 1 
* Данный метод возвращает значение типа boolean
* true - заблокирован
* false - активен
*/
$flag = $user->checkBlock(1);

/**
* Проверить пароль myPassword для веб-пользвоателя с ID = 1 
* После чего выполнить проверку статуса блокировки. Если даже пароль указан верный, а пользователь заблокирован, то данный метод вернет значение false. В случае, если изменить значение 3 параметра на false, то статус блокировки проверяться не будет.
* Данный метод возвращает значение типа boolean
* true - верный пароль
* false - пароль не корректен
*/
$flag = $user->testAuth(1, 'myPassword', true);

/**
* Принудительно разлогинить веб-пользователя
*/
$user->logOut();
```


###Практическое применение
*modUsers*
Следующий плагин для событий OnWebPageInit и OnPageNotFound, позволяет производить моментальное применение блокировки. Это бывает полезно, когда пользователь вроде бы забанен, но продолжает проявлять активность, т.к. сессия не истекла.
```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$modx->user = new modUsers($modx);
if($modx->isFrontend() && $modx->getLoginUserID('web')){
	$modx->user->edit((int)$modx->getLoginUserID('web'));
	if(!$modx->user->getID() || $modx->user->checkBlock()){
		$modx->user->logOut();
	}
}
```

*modResource*
Следующий сниппет позволяет последовательно получать значения полей одного и того же документа не выполняя при этом повторый SQL запрос.
```
/**
* <h5>[[DocInfo? &id=`6` &field=`pagetitle`]]</h5>
* <img src="[[DocInfo? &id=`6` &field=`image`]]" />
* С данным сниппетом будет выполнен всего 1 SQL запрос
*/
if(empty($modx->doc)){
	include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
	$modx->doc = new modResource($modx);
}
$id = isset($id) ? (int)$id : $modx->documentObject['id'];
$field = isset($field) ? (string)$field : 'id';
if($field == 'id'){
    $out = $id;
}else{
    if($modx->documentObject['id'] == $id){
        $out = isset($modx->documentObject[$field]) ? $modx->documentObject[$field] : '';
        if(is_array($out)){
           $out = isset($out[1]) ? $out[1] : '';
        }
    }else{
		$doc = clone $modx->doc;
        $out = $doc->edit($id)->get($field);
    }
}
return (string)$out;
```