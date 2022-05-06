## DLLastViews: Most Recently Viewed Documents
A snippet to display the most recently viewed documents, for example, you can display viewed products for stores.
There are two parameters in the snippet properties:

* Cookie storage time. Set in seconds, default 30 days
* How many documents should I remember? Default: 5
Author: Maxim

### Installation:
* Create a new snippet and paste the code there
* Tick "Analyze DocBlock" and save
```
<?php
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
if (!isset($params['tpl'])) $params['tpl'] = '@CODE: ';
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
```
### Use:
On pages that you want to remember, write a non-cached call without parameters
```
[!DLLastViews!]
```
Where you need to display a list of viewed documents, write a non-cached call with parameters. All parameters like The DocLister (except idType, it is hard-coded in the snippet) and add the parameter &mode='show'
```
[!DLLastViews? 
    &mode=`show`
    &ownerTPL=`
[+dl.wrap+]
`
    &tpl=`@CODE: <li><a href="[+url+]">[+title+]</a></li>`
!]
````
