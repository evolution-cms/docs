
Чаще всего полученные данные выводятся не в чистом виде. Например, требуется выполнение при выводе каких-либо условий или обработок (вывод превью для картинки, пересчет цены, форматирование значений). 

Традиционным способом в MODX является вызов сниппетов в шаблонах вывода или использование модификаторов (phx). Такой подход часто используется новичками в силу простоты, но при этом увеличивается нагрузка на парсер и базу данных.

В DocLister предусмотрена возможность предварительной обработки данных средствами PHP с помощью параметра prepare.

Значением параметра prepare может быть:

* имя сниппета;
* вызов метода заранее загруженного класса;
* анонимная функция.

Можно задавать несколько значений для последовательных обработок.

## Использование сниппетов

Сниппет обрабатывает значения массива $data после обработки возвращает массив $data или false. В последнем случае данные выводиться не будут, т.е. можно использовать prepare таким образом для фильтрации данных.

Также в сниппете можно использовать объекты $_DocLister и $_extDocLister.

Объект $_DocLister дает возможность обращаться к методам и свойствам контроллера. Например, можно подменить текущий шаблон вывода:

```
$_DocLister->renderTPL = "@CODE:[+pagetitle+]";
```

В объекте $_extDocLister доступны методы getStore и setStore. setStore сохраняет, а getStore, соответственно, извлекает данные из памяти. Как только DocLister завершил свою работу, сохраненные блоки удаляются из памяти.

## Использование методов класса

```
class DLprepare {
    public static function prepare(array $data = array(), DocumentParser $modx, $_DL, prepare_DL_Extender $_extDocLister) {
        return $data
    }
}
```
Значение параметра в этом случае: DLprepare::prepare

Аналогичным образом можно использовать анонимные функции.

## Примеры из блога Agel Nash

### Пример 1

Итак, представим, что у нас есть некий вызов DocLister'a:

```
[[DocLister? &tpl=`tplChunk` &parents=`1`]]
```

Где tplChunk это ни что иное, как:

```
<a href="[+url+]">[[if? &is=`[+longtitle+]:notempty` &then=`[+longtitle+]` &else=`[[snippet? &text=`[+pagetitle+]`]]`]]</a>
```

Внутри чанка tplChunk имеется вложенный вызов if (допустим тот, что был указан в начале топика). Что мы делаем?

Добавляем к вызову DocLister параметр &prepare=`test` (можно и не тест, а любое другое значение). 

Создаем сниппет с именем test (ну или с тем именем, которое было указано в параметре prepare)

В сниппете пишем такой код:

```
<?php
if(!empty($data['longtitle'])){
    $data['longtitle'] = $modx->runSnippet("snippet", array('text'=>$data['pagetitle']));
}
return $data;
```

Вы конечно можете вместо runSnippet написать и:

```
$data['longtitle'] = "[[snippet? &text=`".$data['pagetitle']."`]]";
```
Но еще раз вспомним почему это плохо: pagetitle может содержать символы об которые запнется парсер modx. Так можно написать только в том случае, если pagetitle может содержать вызов сниппета (но это оооочень редкий случай + есть другие способы для обработки вложенных modx тегов)! Но вернемся к нашим баранам.

Избавившись от вложенного сниппета теперь можно спокойно избавиться от чанка tplChunk и вынести шаблон прямо в вызов DocLister'a:

```
[[DocLister? &tpl=`@CODE:<a href="[+url+]">[+longtitle+]</a>` &parents=`1`]]
```

Теперь можно подвести итог: Проверка условий средствами php (при помощи сниппета prepare) позволяет избежать ненужных вызовов вложенных сниппетов (вложенных вызов происходит только тогда, когда условие true). А еще, на мой скромный взгляд, inline шаблоны это очень удобно, т.к. наглядно виден и сам вызов и шаблон - все в 1 месте.

### Пример №2

Этот пример будет сложнее для понимания. Но он еще более наглядно демонстрирует преимущество параметра prepare.

На сайте имеются несколько групп товаров (телефоны, телевизоры, магнитофоны). В каждой группе соответственно свои позиции, которые пользователь добавляет в корзину. На странице оформления заказа все выбранные позиции должны еще иметь подпись (к какой группе товаров они принадлежат). Помимо каждый товар в корзине имеет такие характеристики, как кол-во заказываемого товара, стоимость товара и общая стоимость с учетом количества. Так же нужно посчитать общее ИТОГО в виде полной суммы заказа.

Упростим немного эту задачку переместив в TV-параметр count заказываемое количество позиций. А саму корзину выведем точным перечислением ID документов. Таким образом вызов принимает следующий вид:

```
[!DocLister? 
  &documents=`5133, 5132, 5135, 5131, 5136` 
  &idType=`documents`
  &tpl=`ListShop` 
  &tvList=`price,count`     
  &ownerTPL=`@CODE:<table class="table table-hover params"><tr><td>Категория</td><td>Позиция</td><td>Остаток</td><td>Стоимость</td><td>Общая стоимость</td></tr>[+dl.wrap+]</table>`
!]
```

А чанк ListShop содержит такой код:

```
<tr>
  <td>[[DocInfo? &docid=`[+parent+]` &field=`pagetitle`]]</td>
  <td>[+pagetitle+]</td>
  <td>[+tv.count+] шт.</td>
  <td>[+tv.price+] руб.</td>
  <td>[[FullPrice? &price=`[+tv.price+]` &count=`[+tv.count+]`]] руб.</td>
</tr>
```

Если сниппет DocInfo всем знаком, то сниппет FullPrice это ни что иное, как банальное перемножение двух чисел:

```
<?php
$count = isset($count) ? (int)$count : 0;
$price = isset($price) ? (int)$price : 0;
return $count*$price;
?>
```

Чтобы стало понятнее, вот так выглядит дерево ресурсов:

Дерево ресурсов

Добьем последний штрих - посчитаем на какую сумму у нас всего товаров в корзине. Для этого потребуется накидать небольшой сниппет, который пробежится опять по всем документам и посчитает общую сумму FullPrice. Назовем этот сниппет totalFullPrice (где 27 и 26 это ID тв-параметров с ценой и количеством):

```
<?php
//Получаем те же самые данные только для упрощения работы используем json формат. в целом не важно как это происходит, главное получить тут список нужны id документов
$out = $modx->runSnippet("DocLister", array('documents'=>'5133, 5132, 5135, 5131, 5136', 'idType'=>'documents', 'idType'=>'parents', 'depth'=>2, 'api'=>'id', 'JSONformat'=>'id'));
$out = json_decode($out, true);
$id = array();
foreach($out as $item){
  $id[] = $item['id'];
}
 
$q = $modx->db->query("SELECT value,contentid,tmplvarid FROM ".$modx->getFullTableName("site_tmplvar_contentvalues")." WHERE contentid IN (".implode(",", $id).") AND tmplvarid IN (26, 27)");
$q = $modx->db->makeArray($q);
$out = array();
foreach($q as $item){
   $out[$item['contentid']][$item['tmplvarid']] = $item['value'];
}
$price = 0;
foreach($out as $id=>$data){
    $price += $data['27'] * $data['26'];
}
return $price;
?>
```

Т.к. это корзина, то все вызовы сниппетов делаем не кешированными и смотрим на результат (меня интересует общее число запросов): 12 SQL запросов для решения такой плевой задачи.

Пробуем теперь сделать тоже самое при помощи prepare сниппета.

```
[!DocLister? 
&documents=`5133, 5132, 5135, 5131, 5136` 
&idType=`documents`
&prepare=`total` 
&tpl=`@CODE: <tr><td>[+category+]</td><td>[+pagetitle+]</td><td>[+tv.count+] шт.</td><td>[+tv.price+] руб.</td><td>[+fullPrice+] руб.</td></tr>` 
&tvList=`price,count`   
&ownerTPL=`@CODE:<table class="table table-hover params"><tr><td>Категория</td><td>Позиция</td><td>Остаток</td><td>Стоимость</td><td>Общая стоимость</td></tr>[+dl.wrap+]</table>`!]
```

Как видите, в этом случае мы опять отказались от чанка в пользу inline шаблона в котором используются 2 непонятных плейсхолдера - category и fullPrice. Давайте посмотрим на код сниппета prepare, чтобы стало понятнее:

```
<?php
$data['fullPrice'] = $data['tv.count'] * $data['tv.price'];
 
//[[DocInfo? &docid=`[+parent+]` &field=`pagetitle`]]
$data['category'] = $modx->runSnippet('DocInfo',array('docid'=>$data['parent'], 'field'=>'pagetitle'));
  
$key = 'totalFullPrice';
$price = $modx->getPlaceholder($key);
if(empty($price)){
    $price = 0;
}
$price += $data['fullPrice'];
$modx->setPlaceholder($key,$price);
 
return $data;
?>

```
fullPrice это ни что иное, как банальное перемножение 2 числе (цены и количества). Согласитесь, нет необходимости для такой банальной операции создавать/вызывать еще 1 сниппет, когда можно произвести расчет прямо как говорится "не отходя от кассы".

category запускает тот же самый DocInfo при помощи runSnippet (т.е. ничего не поменялось).

А теперь самое главное! Создается глобальный плейсхолдер totalFullPrice, который можно уже использовать вне чанков DocLister'a! Если его нет - то устанавливается значение 0. Если есть, то к нему прибавляется fullPrice. Таким образом, мы избавляемся от необходимости делать повторную выборку тех же самых данных только ради того, чтобы посчитать общую стоимость. Т.е. считаем все и сразу. Соответственно вызов [!totalFullPrice!] на странице заменяется на [+totalFullPrice+] (я еще ни разу не встречал, чтобы подобные данных получали при помощи сниппета вложенного в чанк ListShop. Как правило их получают именно при помощи сниппета похожего на totalFullPrice.)

Проверяем результат - 9 SQL запросов.

Давайте опять подведем итог: Благодаря prepare сниппету получилось избавиться от необходимости повторной обработки тех же самых данных, которые нужны для получения и вывода какой-то другой информации в произвольном месте этой же страницы.

### Пример №3
Этот пример еще сложнее, но одновременно с этим еще более полезней и интересней.

Итак, если посмотреть внимательно на скриншот дерева ресурсов и список ID документов которые мы выводим, то можно заметить, что из разделов телевизоры и магнитофоны выводится по 2 документа. Таким образом, parents у документов 5135, 5131 и 5136, 5132 будут одинаковыми соответственно. Т.е. у первой пары parents будет 5638, а у второй 5639. Что нам это дает? А это дает вот что - мы целых 2 раза вызываем DocInfo просто так. Представьте, вы получили pagetitle документа 5638 и запомнили его. Если он понадобился вам опять - то вы не повторно его запрашиваете, а сразу используете.

Именно для этой цели в DocLister, а если быть точнее в экстендере prepare есть 2 метода: getStore и setStore. Один сохраняет, а второй соответственно извлекает данные из памяти. Как только DocLister завершил свою работу, сохраненные блоки удаляются из памяти (массив автоматически очищается) и все работает дальше без каких-либо глюков, как это могло бы быть, если бы мы сохраняли временные данные в глобальный массив плейсхолдеров. Более того, при таком подходе и больших объемах потребовалось бы очень много памяти...

Ладно, хватит лирики. Давайте посмотрим как можно переписать сниппет prepare с учетом getStore и setStore:

```
if(($data['category']=$_extDocLister->getStore('currentParents'.$data['parent'])) === null){
    //[[DocInfo? &docid=`[+parent+]` &field=`pagetitle`]]
    $data['category'] = $modx->runSnippet('DocInfo',array('docid'=>$data['parent'], 'field'=>'pagetitle'));
    $_extDocLister->setStore('currentParents'.$data['parent'], $data['category']);
}
```

Я не стал копипастить весь исходник, а только процитировал измененную часть. Но думаю тут и так понятно, что мы "обернули" вызов сниппета DocInfo в эти 2 функции. А в качестве уникального ключа указали currentParents[+parent+]. Таким образом, для формирований этой же страницы MODX-у потребовалось всего 7 SQL запросов.

Таким образом: сниппет prepare позволяет не только обрабатывать данные, но и исключить бесполезное повторное выполнение кода.

## Обработка шаблона обертки
После того, как каждый документ обработан, DocLister пытается применить обертку ownerTPL. Порой бывает необходимо эту обертку дополнительно обработать и возможно подменить в зависимости от различных условий (кол-во выводимых документов, даты и т.п.).

### Вывод 3 блоков с равномерным наполнением за 1 вызов 
```
return $modx->runSnippet('DocLister', array(
	'ownerTPL' => '@CODE: <div class="mini-slider clearfix">
		<div id="carousel-left">[+slider.left+]</div>
		<div id="carousel-center">[+slider.center+]</div>
		<div id="carousel-right">[+slider.right+]</div>
		<a id="prev" href="#"></a>
		<a id="next" href="#"></a>
	</div>',
	'tpl' => '@CODE: <div class="sert">
		<img src="[+tv.image+]" alt="[+e.title+]" title="[+e.title+]">
	</div><!-- slide !-->',
	'tvList' => 'image',
	'prepareWrap' => function($data, $modx, $_DL, $_eDL){
		$plh = isset($data['placeholders']) && is_array($data['placeholders']) ? $data['placeholders'] : array();
		$plh['slider.left'] = $plh['slider.center'] = $plh['slider.right'] = '';
		$wrap = explode('<!-- slide !-->',
			(isset($plh['dl.wrap']) && is_scalar($plh['dl.wrap']) ? $plh['dl.wrap'] : '')
		);
		$count = count(
			isset($data['docs']) && is_array($data['docs']) ? $data['docs'] : array()
		);

		for($i = 0; $i <= $count; $i){
			$left = APIHelpers::getkey($wrap, $i++, '');
			$center = APIHelpers::getkey($wrap, $i++, '');
			$right = APIHelpers::getkey($wrap, $i++, '');

			if(empty($left) || empty($center) || empty($right)){
				break;
			}else{
				$plh['slider.left'] .= $left;
				$plh['slider.center'] .= $center;
				$plh['slider.right'] .= $right;
			}
		}
		return $plh;
	}
));
```
### Подстановка данных в шаблон обертку для меню определенного уровня
```
return $modx->runSnippet('DLBuildMenu', array(
    'idType' => 'parents',
    'parents' => 0,
    'debug' => 0,
    'maxDepth' => 2,
    'tvList' => 'dropMenu',
    'TplOneItem' => '@CODE: <li><a href="[+url+]" title="[+e.title+]">[+title+]</a></li>',
    'TplNoChildrenDepth1' => '@CODE: <li><a href="[+url+]" title="[+e.title+]">[+title+]</a></li>',
    'TplDepth1' => '@CODE: <li class="drop"><a href="[+url+]" title="[+e.title+]">&nbsp;[+title+]</a>[+dl.submenu+]</li>',
    'TplMainOwner' => '@CODE: <nav><ul>[+dl.wrap+]</ul></nav>',
    'TplSubOwner' => '@CODE: <div class="drop-block">
        <!--<i class="closed"></i>-->
        <div class="drop-content clearfix" style="[+background+]">
            <div class="cell">
                <ul>
                    [+dl.wrap+]
                </ul>
            </div>
            <div class="left">
                [+addText+]
            </div>
        </div>
    </div>',
    'AfterPrepare' => 'mainMenu::afterPrepare',
    'prepareWrap' => function($data, $modx, $_DL){
        $plh = $data['placeholders'];
        if($_DL->getCfgDef('currentDepth', 1)==2){
            $parent = current($_DL->getOneField('parent', true));
            $plh['addText'] = $modx->runSnippet('DDocInfo', array('id' => $parent, 'field' => 'dropMenuText'));
            $bg = $modx->runSnippet('DDocInfo', array('id' => $parent, 'field' => 'dropMenuImage'));
            if($bg && file_exists(MODX_BASE_PATH . $bg) && is_file(MODX_BASE_PATH . $bg)){
                $plh['background'] = 'background:url('.$bg.') right bottom no-repeat';
            }
        }
        return $plh;
    }
));
```
