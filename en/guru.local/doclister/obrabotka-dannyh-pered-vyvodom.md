
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: Обработка данных перед выводом</h2>

<p>Чаще всего полученные данные выводятся не в чистом виде. Например, требуется выполнение при выводе каких-либо условий или обработок (вывод превью для картинки, пересчет цены, форматирование значений).</p>
<p>Традиционным способом в MODX является вызов сниппетов в шаблонах вывода или использование модификаторов (phx). Такой подход часто используется новичками в силу простоты, но при этом увеличивается нагрузка на парсер и базу данных.</p>
<p>В DocLister предусмотрена возможность предварительной обработки данных средствами PHP с помощью параметра prepare.</p>
<p>Значением параметра prepare может быть:</p>
<ul>
<li>имя сниппета;</li>
<li>вызов метода заранее загруженного класса;</li>
<li>анонимная функция.</li>
</ul>
<p>Можно задавать несколько значений для последовательных обработок.</p>
<h2 class="page-header">Использование сниппетов</h2>
<p>Сниппет обрабатывает значения массива $data после обработки возвращает массив $data или false. В последнем случае данные выводиться не будут, т.е. можно использовать prepare таким образом для фильтрации данных.</p>
<p>Также в сниппете можно использовать объекты $_DocLister и $_extDocLister.</p>
<p>Объект $_DocLister дает возможность обращаться к методам и свойствам контроллера. Например, можно подменить текущий шаблон вывода:</p>
<pre class="brush: php;">
$_DocLister-&gt;renderTPL = "@CODE:[+pagetitle+]";
</pre>
<p>В объекте <code>$_extDocLister</code> доступны методы <code>getStore</code> и <code>setStore</code>. setStore сохраняет, а getStore, соответственно, извлекает данные из памяти. Как только DocLister завершил свою работу, сохраненные блоки удаляются из памяти.</p>
<h2 class="page-header">Использование методов класса</h2>
<pre class="brush: php;">
class DLprepare {
	public static function prepare(array $data = array(), DocumentParser $modx, $_DL, prepare_DL_Extender $_extDocLister) {
		return $data
	}
}
</pre>
<p>Значение параметра в этом случае: DLprepare::prepare</p>
<p>Аналогичным образом можно использовать анонимные функции.</p>
<h2 class="page-header">Примеры из блога Agel Nash</h2>
<h3 class="sub-header text-bold">Пример 1</h3>
<p>Итак, представим, что у нас есть некий вызов DocLister'a:</p>
<pre class="brush: html;">
[[DocLister? &amp;tpl=`tplChunk` &amp;parents=`1`]]
</pre>
<p>Где tplChunk это ни что иное, как:</p>
<pre class="brush: html;">
&lt;a href="[+url+]"&gt;[[if? &amp;is=`[+longtitle+]:notempty` &amp;then=`[+longtitle+]` &amp;else=`[[snippet? &amp;text=`[+pagetitle+]`]]`]]&lt;/a&gt;
</pre>
<p>Внутри чанка tplChunk имеется вложенный вызов if (допустим тот, что был указан в начале топика). Что мы делаем?</p>
<p>Добавляем к вызову DocLister параметр <code>&amp;prepare=test</code> (можно и не тест, а любое другое значение).</p>
<p>Создаем сниппет с именем test (ну или с тем именем, которое было указано в параметре prepare)</p>
<p>В сниппете пишем такой код:</p>
<pre class="brush: php;">
&lt;?php
if(!empty($data['longtitle'])){
	$data['longtitle'] = $modx-&gt;runSnippet("snippet", array('text'=&gt;$data['pagetitle']));
}
return $data;
</pre>
<p>Вы конечно можете вместо runSnippet написать и:</p>
<pre class="brush: php;">
$data['longtitle'] = "[[snippet? &amp;text=`".$data['pagetitle']."`]]";
</pre>
<p>Но еще раз вспомним почему это плохо: pagetitle может содержать символы об которые запнется парсер modx. Так можно написать только в том случае, если pagetitle может содержать вызов сниппета (но это оооочень редкий случай + есть другие способы для обработки вложенных modx тегов)! Но вернемся к нашим баранам.</p>
<p>Избавившись от вложенного сниппета теперь можно спокойно избавиться от чанка tplChunk и вынести шаблон прямо в вызов DocLister'a:</p>
<pre class="brush: html;">
[[DocLister? &amp;tpl=`@CODE:&lt;a href="[+url+]"&gt;[+longtitle+]&lt;/a&gt;` &amp;parents=`1`]]
</pre>
<p>Теперь можно подвести итог: Проверка условий средствами php (при помощи сниппета prepare) позволяет избежать ненужных вызовов вложенных сниппетов (вложенных вызов происходит только тогда, когда условие true). А еще, на мой скромный взгляд, inline шаблоны это очень удобно, т.к. наглядно виден и сам вызов и шаблон - все в 1 месте.</p>

<h3 class="sub-header text-bold">Пример №2</h3>
<p>Этот пример будет сложнее для понимания. Но он еще более наглядно демонстрирует преимущество параметра prepare.</p>
<p>На сайте имеются несколько групп товаров (телефоны, телевизоры, магнитофоны). В каждой группе соответственно свои позиции, которые пользователь добавляет в корзину. На странице оформления заказа все выбранные позиции должны еще иметь подпись (к какой группе товаров они принадлежат). Помимо каждый товар в корзине имеет такие характеристики, как кол-во заказываемого товара, стоимость товара и общая стоимость с учетом количества. Так же нужно посчитать общее ИТОГО в виде полной суммы заказа.</p>
<p>Упростим немного эту задачку переместив в TV-параметр count заказываемое количество позиций. А саму корзину выведем точным перечислением ID документов. Таким образом вызов принимает следующий вид:</p>
<pre class="brush: html;">
[!DocLister? 
&amp;documents=`5133, 5132, 5135, 5131, 5136` 
&amp;idType=`documents`
&amp;tpl=`ListShop` 
&amp;tvList=`price,count` 
&amp;ownerTPL=`@CODE:&lt;table class="table table-hover params"&gt;&lt;tr&gt;&lt;td&gt;Категория&lt;/td&gt;&lt;td&gt;Позиция&lt;/td&gt;&lt;td&gt;Остаток&lt;/td&gt;&lt;td&gt;Стоимость&lt;/td&gt;&lt;td&gt;Общая стоимость&lt;/td&gt;&lt;/tr&gt;[+dl.wrap+]&lt;/table&gt;`
!]
</pre>
<p>А чанк ListShop содержит такой код:</p>
<pre class="brush: html;">
&lt;tr&gt;
	&lt;td&gt;[[DocInfo? &amp;docid=`[+parent+]` &amp;field=`pagetitle`]]&lt;/td&gt;
	&lt;td&gt;[+pagetitle+]&lt;/td&gt;
	&lt;td&gt;[+tv.count+] шт.&lt;/td&gt;
	&lt;td&gt;[+tv.price+] руб.&lt;/td&gt;
	&lt;td&gt;[[FullPrice? &amp;price=`[+tv.price+]` &amp;count=`[+tv.count+]`]] руб.&lt;/td&gt;
&lt;/tr&gt;
</pre>
<p>Если сниппет DocInfo всем знаком, то сниппет FullPrice это ни что иное, как банальное перемножение двух чисел:</p>
<pre class="brush: html;">
&lt;?php
$count = isset($count) ? (int)$count : 0;
$price = isset($price) ? (int)$price : 0;
return $count*$price;
?&gt;
</pre>
<p>Чтобы стало понятнее, вот так выглядит дерево ресурсов:</p>
<p>Дерево ресурсов</p>
<p>Добьем последний штрих - посчитаем на какую сумму у нас всего товаров в корзине. Для этого потребуется накидать небольшой сниппет, который пробежится опять по всем документам и посчитает общую сумму FullPrice. Назовем этот сниппет totalFullPrice (где 27 и 26 это ID тв-параметров с ценой и количеством):</p>
<pre class="brush: php;">
&lt;?php
//Получаем те же самые данные только для упрощения работы используем json формат. в целом не важно как это происходит, главное получить тут список нужны id документов
$out = $modx-&gt;runSnippet(
	'DocLister',
	array(
		'documents'=&gt;'5133, 5132, 5135, 5131, 5136',
		'idType'=&gt;'documents',
		'idType'=&gt;'parents',
		'depth'=&gt;2,
		'api'=&gt;'id',
		'JSONformat'=&gt;'id'
	)
);
$out = json_decode($out, true);
$id = array();
foreach($out as $item){
	$id[] = $item['id'];
}

$q = $modx-&gt;db-&gt;query("SELECT value,contentid,tmplvarid FROM ".$modx-&gt;getFullTableName("site_tmplvar_contentvalues")." WHERE contentid IN (".implode(",", $id).") AND tmplvarid IN (26, 27)");
$q = $modx-&gt;db-&gt;makeArray($q);
$out = array();
foreach($q as $item){
	$out[$item['contentid']][$item['tmplvarid']] = $item['value'];
}
$price = 0;
foreach($out as $id=&gt;$data){
	$price += $data['27'] * $data['26'];
}
return $price;
?&gt;
</pre>
<p>Т.к. это корзина, то все вызовы сниппетов делаем не кешированными и смотрим на результат (меня интересует общее число запросов): 12 SQL запросов для решения такой плевой задачи.</p>
<p>Пробуем теперь сделать тоже самое при помощи prepare сниппета.</p>
<pre class="brush: html;">
[!DocLister? 
&amp;documents=`5133, 5132, 5135, 5131, 5136` 
&amp;idType=`documents`
&amp;prepare=`total` 
&amp;tpl=`@CODE: &lt;tr&gt;&lt;td&gt;[+category+]&lt;/td&gt;&lt;td&gt;[+pagetitle+]&lt;/td&gt;&lt;td&gt;[+tv.count+] шт.&lt;/td&gt;&lt;td&gt;[+tv.price+] руб.&lt;/td&gt;&lt;td&gt;[+fullPrice+] руб.&lt;/td&gt;&lt;/tr&gt;` 
&amp;tvList=`price,count` 
&amp;ownerTPL=`@CODE:&lt;table class="table table-hover params"&gt;&lt;tr&gt;&lt;td&gt;Категория&lt;/td&gt;&lt;td&gt;Позиция&lt;/td&gt;&lt;td&gt;Остаток&lt;/td&gt;&lt;td&gt;Стоимость&lt;/td&gt;&lt;td&gt;Общая стоимость&lt;/td&gt;&lt;/tr&gt;[+dl.wrap+]&lt;/table&gt;`!]
</pre>
<p>Как видите, в этом случае мы опять отказались от чанка в пользу inline шаблона в котором используются 2 непонятных плейсхолдера - category и fullPrice. Давайте посмотрим на код сниппета prepare, чтобы стало понятнее:</p>
<pre class="brush: php;">
&lt;?php
$data['fullPrice'] = $data['tv.count'] * $data['tv.price'];

//[[DocInfo? &amp;docid=`[+parent+]` &amp;field=`pagetitle`]]
$data['category'] = $modx-&gt;runSnippet('DocInfo',array('docid'=&gt;$data['parent'], 'field'=&gt;'pagetitle'));

$key = 'totalFullPrice';
$price = $modx-&gt;getPlaceholder($key);
if(empty($price)){
 $price = 0;
}
$price += $data['fullPrice'];
$modx-&gt;setPlaceholder($key,$price);

return $data;
?&gt;
</pre>
<p>fullPrice это ни что иное, как банальное перемножение 2 числе (цены и количества). Согласитесь, нет необходимости для такой банальной операции создавать/вызывать еще 1 сниппет, когда можно произвести расчет прямо как говорится "не отходя от кассы".</p>
<p>category запускает тот же самый DocInfo при помощи runSnippet (т.е. ничего не поменялось).</p>
<p>А теперь самое главное! Создается глобальный плейсхолдер totalFullPrice, который можно уже использовать вне чанков DocLister'a! Если его нет - то устанавливается значение 0. Если есть, то к нему прибавляется fullPrice. Таким образом, мы избавляемся от необходимости делать повторную выборку тех же самых данных только ради того, чтобы посчитать общую стоимость. Т.е. считаем все и сразу. Соответственно вызов [!totalFullPrice!] на странице заменяется на</p>
<p>Проверяем результат - 9 SQL запросов.</p>
<p>Давайте опять подведем итог: Благодаря prepare сниппету получилось избавиться от необходимости повторной обработки тех же самых данных, которые нужны для получения и вывода какой-то другой информации в произвольном месте этой же страницы.</p>
<h3 class="sub-header text-bold">Пример №3</h3>
<p>Этот пример еще сложнее, но одновременно с этим еще более полезней и интересней.</p>
<p>Итак, если посмотреть внимательно на скриншот дерева ресурсов и список ID документов которые мы выводим, то можно заметить, что из разделов телевизоры и магнитофоны выводится по 2 документа. Таким образом, parents у документов 5135, 5131 и 5136, 5132 будут одинаковыми соответственно. Т.е. у первой пары parents будет 5638, а у второй 5639. Что нам это дает? А это дает вот что - мы целых 2 раза вызываем DocInfo просто так. Представьте, вы получили pagetitle документа 5638 и запомнили его. Если он понадобился вам опять - то вы не повторно его запрашиваете, а сразу используете.</p>
<p>Именно для этой цели в DocLister, а если быть точнее в экстендере prepare есть 2 метода: getStore и setStore. Один сохраняет, а второй соответственно извлекает данные из памяти. Как только DocLister завершил свою работу, сохраненные блоки удаляются из памяти (массив автоматически очищается) и все работает дальше без каких-либо глюков, как это могло бы быть, если бы мы сохраняли временные данные в глобальный массив плейсхолдеров. Более того, при таком подходе и больших объемах потребовалось бы очень много памяти...</p>
<p>Ладно, хватит лирики. Давайте посмотрим как можно переписать сниппет prepare с учетом getStore и setStore:</p>
<pre class="brush: php;">
if(($data['category']=$_extDocLister-&gt;getStore('currentParents'.$data['parent'])) === null){
	//[[DocInfo? &amp;docid=`[+parent+]` &amp;field=`pagetitle`]]
	$data['category'] = $modx-&gt;runSnippet('DocInfo',array('docid'=&gt;$data['parent'], 'field'=&gt;'pagetitle'));
	$_extDocLister-&gt;setStore('currentParents'.$data['parent'], $data['category']);
}
</pre>
<p>Я не стал копипастить весь исходник, а только процитировал измененную часть. Но думаю тут и так понятно, что мы "обернули" вызов сниппета DocInfo в эти 2 функции. А в качестве уникального ключа указали currentParents[+parent+]. Таким образом, для формирований этой же страницы MODX-у потребовалось всего 7 SQL запросов.</p>
<p>Таким образом: сниппет prepare позволяет не только обрабатывать данные, но и исключить бесполезное повторное выполнение кода.</p>
<h2 class="page-header">Обработка шаблона обертки</h2>
<p>После того, как каждый документ обработан, DocLister пытается применить обертку ownerTPL. Порой бывает необходимо эту обертку дополнительно обработать и возможно подменить в зависимости от различных условий (кол-во выводимых документов, даты и т.п.).</p>
<h3 class="sub-header text-bold">Вывод 3 блоков с равномерным наполнением за 1 вызов</h3>
<pre class="brush: php;">
return $modx-&gt;runSnippet(
	'DocLister',
	array(
		'ownerTPL' =&gt; '@CODE: &lt;div class="mini-slider clearfix"&gt;
		&lt;div id="carousel-left"&gt;[+slider.left+]&lt;/div&gt;
		&lt;div id="carousel-center"&gt;[+slider.center+]&lt;/div&gt;
		&lt;div id="carousel-right"&gt;[+slider.right+]&lt;/div&gt;
		&lt;a id="prev" href="#"&gt;&lt;/a&gt;
		&lt;a id="next" href="#"&gt;&lt;/a&gt;
		&lt;/div&gt;',
		'tpl' =&gt; '@CODE: &lt;div class="sert"&gt;
		&lt;img src="[+tv.image+]" alt="[+e.title+]" title="[+e.title+]"&gt;
		&lt;/div&gt;&lt;!-- slide !--&gt;',
		'tvList' =&gt; 'image',
		'prepareWrap' =&gt; function($data, $modx, $_DL, $_eDL){
			$plh = isset($data['placeholders']) &amp;&amp; is_array($data['placeholders']) ? $data['placeholders'] : array();
			$plh['slider.left'] = $plh['slider.center'] = $plh['slider.right'] = '';
			$wrap = explode('&lt;!-- slide !--&gt;', (isset($plh['dl.wrap']) &amp;&amp; is_scalar($plh['dl.wrap']) ? $plh['dl.wrap'] : ''));
			$count = count(isset($data['docs']) &amp;&amp; is_array($data['docs']) ? $data['docs'] : array());

			for($i = 0; $i &lt;= $count; $i){
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
	)
);
</pre>

<h3 class="sub-header text-bold">Подстановка данных в шаблон обертку для меню определенного уровня</h3>
<pre class="brush: php;">
return $modx-&gt;runSnippet(
	'DLBuildMenu',
	array(
		'idType' =&gt; 'parents',
		'parents' =&gt; 0,
		'debug' =&gt; 0,
		'maxDepth' =&gt; 2,
		'tvList' =&gt; 'dropMenu',
		'TplOneItem' =&gt; '@CODE: &lt;li&gt;&lt;a href="[+url+]" title="[+e.title+]"&gt;[+title+]&lt;/a&gt;&lt;/li&gt;',
		'TplNoChildrenDepth1' =&gt; '@CODE: &lt;li&gt;&lt;a href="[+url+]" title="[+e.title+]"&gt;[+title+]&lt;/a&gt;&lt;/li&gt;',
		'TplDepth1' =&gt; '@CODE: &lt;li class="drop"&gt;&lt;a href="[+url+]" title="[+e.title+]"&gt;&amp;nbsp;[+title+]&lt;/a&gt;[+dl.submenu+]&lt;/li&gt;',
		'TplMainOwner' =&gt; '@CODE: &lt;nav&gt;&lt;ul&gt;[+dl.wrap+]&lt;/ul&gt;&lt;/nav&gt;',
		'TplSubOwner' =&gt; '@CODE: &lt;div class="drop-block"&gt;
		&lt;!--&lt;i class="closed"&gt;&lt;/i&gt;--&gt;
		&lt;div class="drop-content clearfix" style="[+background+]"&gt;
		&lt;div class="cell"&gt;
		&lt;ul&gt;
		[+dl.wrap+]
		&lt;/ul&gt;
		&lt;/div&gt;
		&lt;div class="left"&gt;
		[+addText+]
		&lt;/div&gt;
		&lt;/div&gt;
		&lt;/div&gt;',
		'AfterPrepare' =&gt; 'mainMenu::afterPrepare',
		'prepareWrap' =&gt; function($data, $modx, $_DL){
			$plh = $data['placeholders'];
			if($_DL-&gt;getCfgDef('currentDepth', 1)==2){
				$parent = current($_DL-&gt;getOneField('parent', true));
				$plh['addText'] = $modx-&gt;runSnippet('DDocInfo', array('id' =&gt; $parent, 'field' =&gt; 'dropMenuText'));
				$bg = $modx-&gt;runSnippet('DDocInfo', array('id' =&gt; $parent, 'field' =&gt; 'dropMenuImage'));
				if($bg &amp;&amp; file_exists(MODX_BASE_PATH . $bg) &amp;&amp; is_file(MODX_BASE_PATH . $bg)){
					$plh['background'] = 'background:url('.$bg.') right bottom no-repeat';
				}
			}
			return $plh;
		}
	)
);
</pre>