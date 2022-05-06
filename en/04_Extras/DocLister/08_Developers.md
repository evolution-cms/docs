## Controllers

The class name located in the php file must end in DocLister, and the class itself must be inherited from the abstract DocLister class.

In the dir parameter, you can specify let from the site root to the folder with the controller.

## Extenders

Extenders can be loaded from the controller or by using the extenders parameter, which lists the *.extender.inc file names from the /core/extender/ folder

The extender to be loaded must be a class whose name must begin with the name of the extender and end with the _DL_Extender. In addition, the loadable extender must inherit from the abstract extDocLister class.

## Filters

Filtering rules can be found in the *.filter file.php by filter name from the /core/filter/ folder. The class in the file must inherit from the abstract glass filterDocLister, and the name itself must end in _DL_filter.

## Reproduction of tv parameter types

#### Example in the site_content controller:
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

## Construction of the DocLister object

This can be handy when the same list needs to be templated 2 times.
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
/** Or through the substitution of the config to use extenders and full-time training of placeholders */
$_DL->setConfig(array(
   'tpl' => '@CODE: [+title+]<br />'
));
$out2 = $_DL->render();
return implode("<hr />", array($out1, $out2));
```
Or, for example, you need to get an array of IDs of documents that are involved in the output
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
## Use of the DocLister template engine in your snippets By connecting the DLTemplate class, you can already use a template engine that:

* Understands inline templates
* Able to create placeholders from multidimensional arrays
* Automatically activates phx when needed
* Allows you to render a document using any template (both with and without the use of events)

The most successful practice is to create a templating device in the tpl variable on the object $modx. To avoid doing this all the time, it's best to use a small plugin on the OnWebPageInit and OnPageNotFound events.
```
require_once(MODX_BASE_PATH.'assets/snippets/DocLister/lib/DLTemplate.class.php');
$modx->tpl = DLTemplate::getInstance($modx);
```
### Standard templating
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
### Substition template for the document 
The most successful example is the printable version. Sometimes it is easier to make a minimal template of each type and customize the output as needed than to play with CSS.

To simplify the perception, the whole process of setting up TV parameters will be missed. So let's imagine that we have:

* CfgTV plugin with prefix for cfg_ settings.
* TV option with a list of IDs of possible templates for printing (for each document you can choose a different template)
* Links to the printable version are displayed as [[id]]?save=print
Creating a plugin for the OnLoadWebDocument and OnLoadWebPageCache events
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
Using template substitution can be convenient if you are editing the site hot (without deploying development versions).
