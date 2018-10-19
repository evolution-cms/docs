## Описание сниппета
Предназначен для вывода ссылок на соседние документы с форматированием вида выводимых ссылок. Для работы необходим установленный [Doc Lister](http://docs.evo.im/04_extras/doclister.html).

## Установка
1. Создайте новый сниппет с именем DLPrevNext и вставьте в него код ниже: 
```
<?php
if (! defined('MODX_BASE_PATH')) {
    die('HACK???');
}

$ID = $modx->documentObject['id'];
$params = is_array($modx->Event->params) ? $modx->Event->params : array();
$params = array_merge($params, array(
        'api'   => 1,
        'debug' => '0'
    ));

$json = $modx->runSnippet("DocLister", $params);
$children = jsonHelper::jsonDecode($json, array('assoc' => true));
$children = is_array($children) ? $children : array();
$self = $prev = $next = null;
foreach ($children as $key => $data) {
    if (! empty($self)) {
        $next = $key;
        break;
    }
    if ($key == $ID) {
        $self = $key;
        if (empty($prev)) {
            $prev = end($children);
            $prev = $prev['id'];
        }
    } else {
        $prev = $key;
    }
}
if (empty($next)) {
    reset($children);
    $next = current($children);
    $next = $next['id'];
}
if ($next == $prev) {
    $next = '';
}

$TPL = DLTemplate::getInstance($modx);
return ($prev == $ID) ? '' : $TPL->parseChunk($prevnextTPL, array(
    'prev' => empty($prev) ? '' : $TPL->parseChunk($prevTPL, $children[$prev]),
    'next' => empty($next) ? '' : $TPL->parseChunk($nextTPL, $children[$next]),
));
?>

```
## Параметры и примеры использования
В нужном месте шаблона вставьте вызов сниппета, параметры вызова аналогичные [параметрам](http://docs.evo.im/04_extras/doclister/parameters.html) **Doclister**.

**&prevnextTPL** — чанк вывода ссылок на соседедние документы, должен содержать 2 плейсхолдера **[+prev+]** и **[+next+]**

**&prevTPL** — чанк в котором задается внешний вид плейсхолдера **[+prev+]**

**&nextTPL** — чанк в котором задается внешний вид плейсхолдера **[+next+]**

Чтобы не создавать лишних чанков, можно использовать структуру ``` &nextTPL=`@CODE: ваш_html ```


#### Простейший вызов
```
[[DLPrevNext? &idType=`parents` &prevnextTPL=`@CODE: [+prev+] | [+next+]` &prevTPL=`@CODE: <a href="[+url+]">&larr; [+title+]</a>` &nextTPL=`@CODE: <a href="[+url+]">[+title+] &rarr;</a>`]]

```
#### Вызов с учетом родительской папки (удобно для вывода соседних документов в каталогах)
```
[[DLPrevNext? &idType=`parents` &parents=`[*parent*]` &prevnextTPL=`@CODE: [+prev+] | [+next+]` &prevTPL=`@CODE: <a href="[+url+]">&larr; [+title+]</a>` &nextTPL=`@CODE: <a href="[+url+]">[+title+] &rarr;</a>`]]

```
