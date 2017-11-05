
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: Разработчикам</h2>

<h3 class="sub-header text-bold">Контроллеры</h3>
<p>Имя класса расположенного в файле php файле должно заканчиваться на DocLister, а сам класс должен быть унаследован от абстрактного класса DocLister.</p>
<p>В параметре dir можно указать пусть от корня сайта к папке с контроллером.</p>
<h3 class="sub-header text-bold">Экстендеры</h3>
<p>Экстендеры могут загружаться из контроллера или с помощью параметра extenders, в котором перечислены имена файлов *.extender.inc из папки /core/extender/</p>
<p>Загружаемый экстендер должен быть классом имя которого должно начинаться с имени экстендера и заканчиваться на _DL_Extender. Помимо этого, загружаемый экстендер должен быть унаследован от абстрактного класса extDocLister.</p>
<h3 class="sub-header text-bold">Фильтры</h3>
<p>Правила фильтрации можно найти в файле *.filter.php по имени фильтра из папки /core/filter/. Класс в файле должен быть унаследован от абстрактного гласса filterDocLister, а само имя должно заканчиваться на _DL_filter.</p>
<h3 class="sub-header text-bold">Приведение типов TV-параметров</h3>
<p>Пример в контроллере site_content:</p>
<pre class="brush: php;">
public function changeSortType($field, $type){
	$type = trim($type);
	switch (strtoupper($type)) {
		case 'TVDATETIME':
			$field = "STR_TO_DATE(" . $field . ",'%d-%m-%Y %H:%i:%s')";
		break;
		
		default:
			$field = parent::changeSortType($field, $type);
		break;
	}
	return $field;
}
</pre>
<h3 class="sub-header text-bold">Сохранение объекта DocLister</h3>
<p>Это может быть удобно, когда один и тот же список необходимо шаблонизировать 2 раза.</p>
<pre class="brush: php;">
$out1 = $modx-&gt;runSnippet(
	'DocLister',
	array(
		'idType' =&gt; 'parents',
		'parents' =&gt; 0,
		'tpl' =&gt; '@CODE: [+pagetitle+]&lt;br /&gt;',
		'saveDLObject' =&gt; '_DL'
	)
);
$_DL = $modx-&gt;getPlaceholder('_DL');
$out2 = $_DL-&gt;docsCollection()-&gt;reduce(function($out, $data) use ($_DL, $modx){
	$data['title'] = empty($data['menutitle']) ? $data['pagetitle'] : $data['menutitle'];
	$data['url'] = $modx-&gt;makeUrl($data['id']);
	return $out.$_DL-&gt;parseChunk('@CODE: [+title+]&lt;br /&gt;', $data);
});

/** Либо через подмену конфига, чтобы задействовать экстендеры и штатную подготовку плейсхолдеров */
$_DL-&gt;setConfig(array(
   'tpl' =&gt; '@CODE: [+title+]&lt;br /&gt;'
));
$out2 = $_DL-&gt;render();
return implode("&lt;hr /&gt;", array($out1, $out2));
</pre>
<p>Или, например, нужно получить массив ID документов, которые задействованы в выводе</p>
<pre class="brush: php;">
$out = $modx-&gt;runSnippet(
	'DocLister',
	array(
		'saveDLObject' =&gt; '_DL'
	)
);
$_DL = $modx-&gt;getPlaceholder('_DL');
$ids = $_DL-&gt;getOneField('id');

/** или через коллекцию */
$ids = $_DL-&gt;docsCollection()-&gt;map(function($val){
	return $val['id'];
})-&gt;toArray();
</pre>
<h3 class="sub-header text-bold">Использование шаблонизатора DocLister в своих сниппетах</h3>
<p>Подключив класс DLTemplate вы уже можете пользоваться шаблонизатором, который:</p>
<ul>
<li>Понимает inline шаблоны</li>
<li>Умеет создавать плейсхолдеры из многомерных массивов</li>
<li>Автоматически активирует phx при необходимости</li>
<li>Позволяет отрендерить документ применив любой шаблон (как с применением событий, так и без них)</li>
</ul>
<p>Наиболее удачная практика - создание шаблонизатора в переменной tpl у объекта $modx. Чтобы не делать это постоянно, лучше всего воспользоваться небольшим плагином на событиях OnWebPageInit и OnPageNotFound</p>
<pre class="brush: php;">
require_once(MODX_BASE_PATH.'assets/snippets/DocLister/lib/DLTemplate.class.php');
$modx-&gt;tpl = DLTemplate::getInstance($modx);
</pre>
<h3 class="sub-header text-bold">Обычная шаблонизация</h3>
<pre class="brush: php;">
$data = array(
	array(
		'id' =&gt; 1,
		'text' =&gt; 'hello', 
		'info' =&gt; array(
			'phone' =&gt; '01',
			'site' =&gt; 'http://example.org'
		)
	),
	array(
		'id' =&gt; 2,
		'text' =&gt; 'world', 
		'info' =&gt; array(
			'phone' =&gt; '02',
			'site' =&gt; 'http://example.com'
		)
	)
);
$out = '';
foreach($data as $item){
	$out .= $modx-&gt;tpl-&gt;parseChunk('@CODE: &lt;strong&gt;[+id+]&lt;/strong&gt;. [+text+] ([+info.phone+], [+info.site+])', $item);
}
return $out;
</pre>
<h3 class="sub-header text-bold">Подмена шаблона у документа</h3>
<p>Наиболее удачный пример - версия для печати. Порой бывает проще сделать минимальный шаблон каждого типа и настроить вывод так, как нужно, нежели играться с CSS.</p>
<p>Для упрощения восприятия, весь процесс настройки ТВ параметров будет упущен. Поэтому представим, что у нас имеется:</p>
<ul>
<li>Плагин cfgTV с префиксом для настроек cfg_.</li>
<li>ТВ параметр со списком ID возможных шаблонов для печати (для каждого документа можно выбрать свой шаблон)</li>
<li>Ссылки на версию для печати выводятся в виде <code>[~[<em>id</em>]~]?save=print</code></li>
</ul>
<p>Создаем плагин для событий <code>OnLoadWebDocument</code> и <code>OnLoadWebPageCache</code></p>
<pre class="brush: php;">
if(isset($modx-&gt;print)) return;
$defaultTPL = $modx-&gt;getConfig('cfg_printTPL');
$modx-&gt;print = true;
if(isset($_GET['save']) &amp;&amp; $_GET['save']=='print' &amp;&amp; !empty($modx-&gt;documentObject)){
	$tpl = !empty($modx-&gt;documentObject['printTPL'][1]) ? $modx-&gt;documentObject['printTPL'][1] : $defaultTPL;
	if(!empty($tpl)){
			$modx-&gt;print = $modx-&gt;tpl-&gt;renderDoc($modx-&gt;documentObject['id'], true, (int)$tpl);
	}else{
			$modx-&gt;print = false;
	}
}
if($modx-&gt;print){
	if($modx-&gt;print !== true){
		echo $modx-&gt;print;
		die();
	}
}else{
	$modx-&gt;sendErrorPage();
}
</pre>
<p>Использовать подмену шаблонов может быть удобно, если вы редактируете сайт на горячую (без разворачивания девелоперских версий).</p>