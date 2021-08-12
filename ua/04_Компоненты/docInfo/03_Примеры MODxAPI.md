
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Приклад DocInfo на базі modResource MODxAPI </h3> 
Тепер сніпет DocInfo НЕ буде навантажувати сторінку повторними SQL запитами при багаторазовому отриманні значень з одного і того ж документа.	
<br>
<p>Вміст сховища розміщується в папці <span class="text-bold">/assets/lib/MODxAPI/</span></p>
<p>Створюється плагін на події <span class="text-bold">OnWebPageInit</span>, <span class="text-bold">OnManagerPageInit</span> і <span class="text-bold">OnPageNotFound</span> з кодом:</p>
<pre class="brush: php">include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
if(!isset($modx->doc)){
 $modx->doc = new modResource($modx);
}</pre>

<h3>Після чого створюється сніпет допустимо DocInfo</h3>
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
<p><span class="text-bold">Profit!</span> Тепер сніпет DocInfo не буде навантажувати сторінку повторними SQL запитами при багаторазовому отриманні значень з одного і того ж документа</p>
