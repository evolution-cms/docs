## Опис сніпета
Призначений для виведення посилань на сусідні документи з форматуванням виду виведених посилань. Для роботи необхідний встановлений [Doc Lister](http://docs.evo.im/04_extras/doclister.html).

## Установка
1. Створіть новий сніпет з ім'ям DLPrevNext і вставте в нього код нижче: 
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
## Параметри і приклади використання
У потрібному місці шаблону вставте виклик сніпета, параметри виклику аналогічні [параметрам](http://docs.evo.im/04_extras/doclister/parameters.html) **Doclister**.

**&prevnextTPL** — ім'я чанка або код (через @CODE :) виведення посилань на соседедніе документи, содержмт 2 плейсхолдера **[+prev+]** і **[+next+]**

**&prevTPL** — ім'я чанка або код (через @CODE :) в якому задається зовнішній вигляд плейсхолдера **[+prev+]**

**&nextTPL** — ім'я чанка або код (через @CODE :) в якому задається зовнішній вигляд плейсхолдера **[+next+]**

Щоб не створювати зайвих чанкі, можна використовувати структуру ``` &nextTPL=`@CODE: ваш_html` ```


#### Найпростіший виклик
```
[[DLPrevNext? &idType=`parents` &prevnextTPL=`@CODE: [+prev+] | [+next+]` &prevTPL=`@CODE: <a href="[+url+]">&larr; [+title+]</a>` &nextTPL=`@CODE: <a href="[+url+]">[+title+] &rarr;</a>`]]

```
#### Виклик з урахуванням батьківської папки (зручно для виведення сусідніх документів в каталогах)
```
[[DLPrevNext? &idType=`parents` &parents=`[*parent*]` &prevnextTPL=`@CODE: [+prev+] | [+next+]` &prevTPL=`@CODE: <a href="[+url+]">&larr; [+title+]</a>` &nextTPL=`@CODE: <a href="[+url+]">[+title+] &rarr;</a>`]]

```
