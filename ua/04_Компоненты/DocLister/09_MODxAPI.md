##Вступ
MODxAPI це спроба реалізувати патерн [Data mapper](https://en.wikipedia.org/wiki/Data_mapper_pattern).
Спочатку проектувалося як заміна бібліотеки DocManager, але в підсумку оптимізовано код і закладений потенціал для створення обгортки з довільної логікою для будь-яких таблиць.

###Підтримувані моделі
*modResource* - Документи (дані з таблиці site_content і site_tmplvar_contentvalues)
*modUsers* - Веб-користувачі (дані з таблиць web_users иі web_user_attributes)
*modCategories* - Категорії (дані з таблиць categories)
*modChunk* - Чанки (дані з таблиць site_htmlsnippets)
*modModule* - Модулі (дані з таблиць site_modules)
*modPlugin* - Плагіни (дані з таблиць site_plugins
*modSnippet* - Сніппети (дані з таблиць site_snippets)
*modTV* - ТВ параметри (дані з таблиць site_tmplvars)
*modTemplate* - Шаблони (дані з таблиць site_templates)

При бажанні можна швидко створити свою модель для будь-якої таблиці. Для цього існує заготівля класу autoTable. У самому примітивному випадку досить вказати лише назву вашої таблиці. Погляньте на приклад створення моделі для таблиці з ім'ям tests:
```
<?php
include_once(MODX_BASE_PATH. "assets/lib/MODxAPI/autoTable.abstract.php");
class modTests extends autoTable
{
    protected $table = "tests";
}
```

### Приклади використання
Методи create, edit, delete, save актуальні для всіх моделей. Але як приклад будемо розглядати модель modResource.

```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
$doc = new modResource($modx);

/** 
* Підготувати створення документа з наступними даними:
* ID шаблона = 10
* Як батька використовувати документ з ID = 1
* pagetitle заголовок документа = example
*/
$doc->create(array(
	'pagetitle' => 'example',
	'template' => 10,
	'parent' => 1
));

/** 
* змінити pagetitle заголовок документа на new title 
*/
$doc->set('pagetitle', 'new title');

/*
* Зберегти документ викликавши події OnBeforeDocFormSave OnDocFormSave,
* але не виробляти скидання кешу.
* ID нового документа помістити в змінну id
*/
$id = $doc->save(true, false);

/** 
* Відкрити на редагування документ з ID = 10 
*/ 
$doc->edit(10);

/** 
* Міняємо батька батька документа
*/
$doc->set('parent', 0);


/*
* Зберігаємо документ не викликаючи події OnBeforeDocFormSave OnDocFormSave,
* Але при цьому виробляємо соброс кеша.
* ID документа зберігається в змінної $id
*/
$id = $doc->save(false, true);

/***
* Видалити всі документи помічені на видалення.
* При цьому викликати події OnBeforeEmptyTrash і OnEmptyTrash
* Якщо значення параметра змінити з true на false, то події викликані не будуть, хоча документи видаляться
*/
$doc->clearTrash(true);

/** 
* Видалити документ з ID = 5, минаючи кошик
* При цьому події OnBeforeEmptyTrash і OnEmptyTrash, будуть викликані.
*/
$doc->delete(5, true);
```

За допомогою модель modUsers можна проводити не тільки запис і отримання даних, але ще і проводити маніпуляції з авторизацією:
```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$user = new modUsers($modx);

/**
* Авторизуватись від імені веб-користувача з ID = 1
*/
$user->authUser(1);

/**
* Перевірити статус блокування веб-користувача з ID = 1 
* Даний метод повертає значення типу boolean
* true - заблокований
* false - активний
*/
$flag = $user->checkBlock(1);

/**
* Перевірити пароль myPassword для веб-користувача з ID = 1 
* Після чого виконати перевірку статусу блокування. Якщо навіть пароль вказано вірний, а користувач заблокований, то даний метод поверне значення false. У разі, якщо змінити значення 3 параметра на false, то статус блокування перевірятися не буде.
* Даний метод повертає значення типу boolean
* true - вірний пароль
* false - пароль не коректний
*/
$flag = $user->testAuth(1, 'myPassword', true);

/**
* Примусово разлогініть веб-користувача
*/
$user->logOut();
```


###Практичне застосування
*modUsers*
Наступний плагін для подій OnWebPageInit і OnPageNotFound, дозволяє виробляти моментальне застосування блокування. Це буває корисно, коли користувач начебто забанили, але продовжує проявляти активність, тому що сесія не закінчилася.
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
Наступний сніпет дозволяє послідовно отримувати значення полів одного і того ж документа не виконуючи при цьому повторюючи SQL запит.
```
/**
* <h5>[[DocInfo? &id=`6` &field=`pagetitle`]]</h5>
* <img src="[[DocInfo? &id=`6` &field=`image`]]" />
* З даними сніпетів буде виконаний всього 1 SQL запит
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
