
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLLastViews</h2>

<p>В свойствах сниппета есть два параметра:</p>
<ol>
	<li>Время хранения cookie. Задается в секундах, по умолчанию 30 дней</li>
	<li>Сколько документов запоминать? По умолчанию: 5</li>
</ol>
<p>Автор: <i class="fa fa-modx text-iners"></i> <a href="http://modx.im/profile/media_kot/" rel="nofollow" target="_blank">Максим</a></p>
<h3 class="sub-header">Установка:</h3>
<ol>
	<li>Создать новый сниппет и вставить туда код</li>
	<li>Поставить галочку «Анализировать DocBlock» и сохранить</li>
</ol>
<pre class="brush: php;">
&lt;?php
/**
 * DLLastViews
 *
 * Conclusion viewed products with DocLister.
 *
 * @category    snippet
 * @version     1.1
 * @internal    @properties &expired=Время хранения cookie;text;2592000;2592000;по умолчанию: 30 дней &maxDocs=Сколько документов запоминать;text;5;5
 * @internal    @modx_category Content
 * @internal    @installset base
 * @author      Created By mkot, optimization Pathologic
 * 
 * @lastupdate  04/09/2017
 */

if (!isset($params['mode'])) $params['mode'] = 'register';
if (!isset($params['tpl'])) $params['tpl'] = '@CODE: <a href=""></a>';
$maxDocs = isset($maxDocs) ? $maxDocs : 5;
$expired = isset($expired) ? $expired  : 2592000;
$params['idType'] = 'documents';
$item = array();

if (isset($_COOKIE['last_view']) and $_COOKIE['last_view'] != '') {
    $params['documents'] = $_COOKIE['last_view'];   
        $item = explode(',', $_COOKIE['last_view']);   
}

switch ($params['mode']) {
    case 'register':
        if (!in_array($modx->documentIdentifier, $item)) {
            array_unshift($item, $modx->documentIdentifier);
            array_slice($item, 0, $maxDocs - 1);
            setcookie('last_view', implode(',', $item), time()+$expired, '/');
        }
    break;
    
    case 'show':      
        if (!empty($item)) {
                        return $modx->runSnippet('DocLister',$params);
                }
    break;
        default:
        break;
}
</pre>
<h3 class="sub-header">Использование:</h3>
<p>На страницах, которые нужно запоминать написать не кэшируемый вызов без параметров</p>
<pre class="brush: html;">[!DLLastViews!]</pre>
<p>Там где нужно выводить список просмотренных документов написать некэшируемы вызов с параметрами. Все параметры, как у DocLister'а (кроме idType, он жестко задан в сниппете) и добавить параметр <span class="text-bold">&mode=`show`</span></p>
<pre class="brush: html;">
[!DLLastViews? 
    &mode=`show`
    &ownerTPL=`<ul>[+dl.wrap+]</ul>`
    &tpl=`@CODE: &lt;li>&lt;a href="[+url+]">[+title+]&lt;/a>&lt;/li>`
!]
</pre>