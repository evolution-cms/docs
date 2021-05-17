
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>DLLastViews: останні переглянуті документи </h3>
Сніпет для виведення останніх переглянутих документів, наприклад можна для магазинів виводити переглянуті товари.
<p>У властивостях сніпета є два параметри:</p>
<ol>
	<li>Час зберігання cookie. Здається в секундах, за замовчуванням 30 днів</li>
	<li>Скільки документів запам'ятовувати? За замовчуванням: 5</li>
</ol>
<p>Автор: <i class="fa fa-modx text-iners"></i> <a href="http://modx.im/profile/media_kot/" rel="nofollow" target="_blank">Максим</a></p>
<h3 class="sub-header">Установка:</h3>
<ol>
	<li>Створити новий сніпет і вставити туди код</li>
	<li>Поставити галочку «Аналізувати DocBlock» і зберегти</li>
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
<h3 class="sub-header">Використання:</h3>
<p>На сторінках, які потрібно запам'ятовувати написати не Кешована виклик без параметрів</p>
<pre class="brush: html;">[!DLLastViews!]</pre>
<p>Там де потрібно виводити список переглянутих документів написати некешований виклик з параметрами. Всі параметри, як у DocLister'а (крім idType, він жорстко заданий в сніпеті) і додати параметр <span class="text-bold">&mode=`show`</span></p>
<pre class="brush: html;">
[!DLLastViews? 
    &mode=`show`
    &ownerTPL=`<ul>[+dl.wrap+]</ul>`
    &tpl=`@CODE: &lt;li>&lt;a href="[+url+]">[+title+]&lt;/a>&lt;/li>`
!]
</pre>
