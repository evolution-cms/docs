##Controllers

Имя класса расположенного в файле php файле должно заканчиваться на DocLister, а сам класс должен быть унаследован от абстрактного класса DocLister.

В параметре dir можно указать пусть от корня сайта к папке с контроллером.

##Экстендеры

Экстендеры могут загружаться из контроллера или с помощью параметра extenders, в котором перечислены имена файлов *.extender.inc из папки /core/extender/

Загружаемый экстендер должен быть классом имя которого должно начинаться с имени экстендера и заканчиваться на _DL_Extender. Помимо этого, загружаемый экстендер должен быть унаследован от абстрактного класса extDocLister.

##Фильтры

Правила фильтрации можно найти в файле *.filter.php по имени фильтра из папки /core/filter/. Класс в файле должен быть унаследован от абстрактного гласса filterDocLister, а само имя должно заканчиваться на _DL_filter.

##Приведение типов TV-параметров

####Пример в контроллере site_content:
```
public function changeSortType($field, $type)
    {
        $type = trim($type);
        switch (strtoupper($type)) {
            case 'TVDATETIME':
            {
                $field = "STR_TO_DATE(" . $field . ",'%d-%m-%Y %H:%i:%s')";
                break;
            }
            default:
                {
                $field = parent::changeSortType($field, $type);
                }
        }
        return $field;
    }
```


##Сохранение объекта DocLister

Это может быть удобно, когда один и тот же список необходимо шаблонизировать 2 раза.

```
$out1 = $modx->runSnippet('DocLister', array(
    'idType' => 'parents',
    'parents' => 0,
    'tpl' => '@CODE: [+pagetitle+]<br />',
    'saveDLObject' => '_DL'
));
$_DL = $modx->getPlaceholder('_DL');
$out2 = $_DL->docsCollection()->reduce(function($out, $data) use ($_DL, $modx){
    $data['title'] = empty($data['menutitle']) ? $data['pagetitle'] : $data['menutitle'];
    $data['url'] = $modx->makeUrl($data['id']);
    return $out.$_DL->parseChunk('@CODE: [+title+]<br />', $data);
});
/** Либо через подмену конфига, чтобы задействовать экстендеры и штатную подготовку плейсхолдеров */
$_DL->setConfig(array(
   'tpl' => '@CODE: [+title+]<br />'
));
$out2 = $_DL->render();
return implode("<hr />", array($out1, $out2));
```

Или, например, нужно получить массив ID документов, которые задействованы в выводе

```
$out = $modx->runSnippet('DocLister', array(
    'saveDLObject' => '_DL'
));
$_DL = $modx->getPlaceholder('_DL');
$ids = $_DL->getOneField('id');
/** или через коллекцию */
$ids = $_DL->docsCollection()->map(function($val){
    return $val['id'];
})->toArray();
```

##Использование шаблонизатора DocLister в своих сниппетах
Подключив класс DLTemplate вы уже можете пользоваться шаблонизатором, который:

 - Понимает inline шаблоны
 - Умеет создавать плейсхолдеры из многомерных массивов
 - Автоматически активирует phx при необходимости
 - Позволяет отрендерить документ применив любой шаблон (как с применением событий, так и без них)

 
Наиболее удачная практика - создание шаблонизатора в переменной tpl у объекта $modx. Чтобы не делать это постоянно, лучше всего воспользоваться небольшим плагином на событиях OnWebPageInit и OnPageNotFound
```
require_once(MODX_BASE_PATH.'assets/snippets/DocLister/lib/DLTemplate.class.php');
$modx->tpl = DLTemplate::getInstance($modx);
```

###Обычная шаблонизация 
```
$data = array(
    array('id' => 1, 'text' => 'hello', 
        'info' => array(
            'phone' => '01',
            'site' => 'http://example.org'
        )
    ),
    array('id' => 2, 'text' => 'world', 
        'info' => array(
            'phone' => '02',
            'site' => 'http://example.com'
        )
    )
);
$out = '';
foreach($data as $item){
    $out .= $modx->tpl->parseChunk('@CODE: <strong>[+id+]</strong>. [+text+] ([+info.phone+], [+info.site+])', $item);
}
return $out;
```

###Подмена шаблона у документа
Наиболее удачный пример - версия для печати. Порой бывает проще сделать минимальный шаблон каждого типа и настроить вывод так, как нужно, нежели играться с CSS.

Для упрощения восприятия, весь процесс настройки ТВ параметров будет упущен. Поэтому представим, что у нас имеется:

 - Плагин cfgTV с префиксом для настроек cfg_.
 - ТВ параметр со списком ID возможных шаблонов для печати (для каждого документа можно выбрать свой шаблон)
 - Ссылки на версию для печати выводятся в виде [~[*id*]~]?save=print
 
Создаем плагин для событий OnLoadWebDocument и OnLoadWebPageCache
```
if(isset($modx->print)) return;

$defaultTPL = $modx->getConfig('cfg_printTPL');
$modx->print = true;

if(isset($_GET['save']) && $_GET['save']=='print' && !empty($modx->documentObject)){
        $tpl = !empty($modx->documentObject['printTPL'][1]) ? $modx->documentObject['printTPL'][1] : $defaultTPL;
        if(!empty($tpl)){
                $modx->print = $modx->tpl->renderDoc($modx->documentObject['id'], true, (int)$tpl);
        }else{
                $modx->print = false;
        }
}

if($modx->print){
    if($modx->print !== true){
        echo $modx->print;
        die();
    }
}else{
    $modx->sendErrorPage();
}
```
Использовать подмену шаблонов может быть удобно, если вы редактируете сайт на горячую (без разворачивания девелоперских версий).
