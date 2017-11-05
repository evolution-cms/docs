
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Пример DocInfo на базе modResource MODxAPI</h2>

<p>Содержимое репозитория размещается в папке <span class="text-bold">/assets/lib/MODxAPI/</span></p>
<p>Создается плагин на событиях <span class="text-bold">OnWebPageInit</span>, <span class="text-bold">OnManagerPageInit</span> и <span class="text-bold">OnPageNotFound</span> с кодом:</p>
<pre class="brush: php">include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
if(!isset($modx->doc)){
 $modx->doc = new modResource($modx);
}</pre>

<h3>После чего создается сниппет допустим DocInfo</h3>
<pre class="brush: php">$id = isset($id) ? (int)$id : $modx->documentObject['id'];
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
        $out = $modx->doc->edit($id)->get($field);
    }
}
return (string)$out;</pre>
<p><span class="text-bold">Profit!</span> Теперь сниппет DocInfo не будет нагружать страницу повторными SQL запросами при многократном получении значений из одного и того же документа</p>