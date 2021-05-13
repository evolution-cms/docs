
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>TagSaver: Плагін для роботи з тегами </h3>
Плагін TagSaver для роботи з тегами.
<p>Взагалі, фільтрація по тегам в MDOX реалізується доволі кисло. Представте, у вас є якись TV параметр, в якому у вас до кожної статті прописано по 10 тегів.</p>
<p>А в базі всі ці теги для документа зберігаються в одній стрічці. Тобто виглядає це приблизно так</p>
<pre class="brush: php;">modx, теги, робота з тегами, сортування за тегами</code></pre>
<p>Як зазвичай відбувається сортування? Створюється SQL запит в таблицю site_tmplvar_contentvalues з використанням WHERE value LIKE %тег%</p>
<p>Таким чином, ми можемо шукати не тільки по тим тегам, які задумувались автором сайта, а й по тегам</p>
<ul>
	<li>і, р</li>
	<li>ми, фи</li>
	<li>льтра</li>
	<li>бот</li>
	<li>філ</li>
	<li>mod</li>
</ul>
<p>Більш того, якщо документів дуже багато, то пошук відбувається неймовірно довго. Як взагалі ідеально повинна виглядати робота з тегами?</p>
<p><span class="text-bold">Таблиця з документами вигляду</span>: id, content, pagetitle</p>
<p><span class="text-bold">Таблица з тегами</span>: id, tag</p>
<p><span class="text-bold">Таблица зв'язків з тегами</span>: doc_id, tag_id </p>
<p>Можна звісно довго спорити про необхідності таблиці звязку, Оскільки придеться робити лишній JOIN. Але щодо правильно разставлених індексів цей джоін взагалі непомітний. Більш того, трохи доробивши таблицю ми можемо вбивати теги в декількох TV-шках, а зберігати в одній таблиці по вищеописаному стандарту.</p>
<p>На основі всього вищесказаного у нас получаються вот такі 2 таблиці</p>
<pre class="brush: sql;">
DROP TABLE IF EXISTS `modx_site_content_tags`;
CREATE TABLE `modx_site_content_tags` (
  `doc_id` int(11) NOT NULL,
  `tag_id` int(11) NOT NULL,
  `tv_id` int(11) NOT NULL DEFAULT '0',
  PRIMARY KEY (`tag_id`,`doc_id`,`tv_id`),
  UNIQUE KEY `dtt` (`doc_id`,`tag_id`,`tv_id`) USING BTREE,
  KEY `doc_id` (`doc_id`),
  KEY `tag_id` (`tag_id`),
  KEY `tv_id` (`tv_id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

DROP TABLE IF EXISTS `modx_tags`;
CREATE TABLE `modx_tags` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(50) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `name` (`name`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
</pre>
<p>Як видно, формат у таблиць MyISAM. Але у такого вибору є своя причина. Одна з них це auto_increment. А друга – унікальний ключ по декільком полям. Не буду довго затримуватись на цьому пункті. Скажу одне – якщо у вас MODX встановлений з префіксом таблиць відмінним від modx, то поміняйте його на свій;-)</p>

<h3 class="sub-header">Створили таблиці? І що? Як тепер інфу в них добавляти?</h3>
<p>Все дуже просто. Створіть як зазвичай TV параметр. Можете навіть добавити віджет mm_widget_tags від ManagerManager. Після цього створіть плагін <a href="https://gist.github.com/4690798" rel="nofollow" target="_blank">TagSaver</a> з параметрами</p>
<pre class="brush: html;">&amp;tv=ID TV-параметра;input; &amp;sep=Роздільник тегів;input;</pre>
<p>Якщо роздільника немає, то можна залишити порожнім.</p>

<h3 class="sub-header">Що рбити якщо мені потрібно 2 поля з тегами?</h3>
<p>Створіть копію плагіна з іншим іменем з аналогічними параметрами. Тільки не забудьте в новій версії плагіна вказати роздільник і ID другого TV параметра.</p>

<h3 class="sub-header">Чому плагін робить SELECT за значенями TV, а не принймає $_POST['tv'.$tv]?</h3>
<ol>
	<li>Ми працюємо в адмінці і ± 1 SQL запит особливогї шкоди не зробить</li>
	<li>Можуть стояти інші плагіни котрі викликаються раніше і змінюють значення TV параметра що зберігається</li>
	<li>Значення TV параметра з $_POST може відрізнятися від збереженого в базу</li>
</ol>

<h3 class="sub-header">Як вивести на сторінці теги привязані до поточної сторінки?</h3>
<p>Виводити їх можна як і раніше – через сніппети DocInfo, просто демонструючи TV параметр на сторінці .</p>

<h3 class="sub-header">Як тепер відсортувати данні за потрібним тегом?</h3>
<p>Очень просто. Створіть сніппет приблизно з таким вмістом</p>
<pre class="brush: php;">
$tag = ((isset($tag) &amp;&amp; is_scalar($tag))? $tag : (isset($_GET['tag']) &amp;&amp; !is_array($_GET['tag']) ? $_GET['tag'] : ''));
$id = isset($id) ? (int)$id : 0;
$out = array();
if($id&gt;0 &amp;&amp; $tag!=''){
	$sql=$modx-&gt;db-&gt;query("SELECT doc_id FROM ".$modx-&gt;getFullTableName("tags")." as t
	LEFT JOIN ".$modx-&gt;getFullTableName("site_content_tags")." as ct ON ct.tag_id = id
	WHERE t.`name`='".$modx-&gt;db-&gt;escape($tag)."' AND ct.tv_id={$id}");
	$sql=$modx-&gt;db-&gt;makeArray($sql);
	foreach($sql as $item){
		$out[]=$item['doc_id'];
	}
}
return implode(",",$out);
</pre>

<p>І результат роботи цього сніппета передаєте в параметр documents від Ditto. У сніппета вказаного вище є 2 параметра:</p>
<ul>
	<li><span class="text-bold">tag</span> – якщо цей параметр переданий, то сніппет використовує його значення. В іншому випадку намагаєтся взяти значення $_GET змінної tag</li>
	<li><span class="text-bold">id</span> – Індетифікатор TV змінної в котрій зберігаються теги</li>
</ul>
<p>Виходить приблизно так</p>
<pre class="brush: html;">[[Ditto? &amp;documents=`[!GetTag? &amp;id=`2`!]`]]</pre>
<h3 class="sub-header">Як тепер вивести популярні теги?</h3>
<pre class="brush: php;">
$count = isset($count) ? (int)$count : 10;
$tv = isset($tv) ? (int)$tv : '';
$out = array();
$sql = $modx-&gt;db-&gt;query(
	"SELECT ct.tv_id,t.name,count(ct.tag_id) as count
	FROM ".$modx-&gt;getFullTableName("tags")." as t
	LEFT JOIN ".$modx-&gt;getFullTableName("site_content_tags")." as ct ON ct.tag_id=t.id
	LEFT JOIN ".$modx-&gt;getFullTableName("site_content")." as c on c.id=ct.doc_id
	WHERE deleted=0 AND published=1 ".(($tv!='') ? ("AND ct.tv_id=".$tv) : "")."
	GROUP BY tag_id ORDER BY count(ct.tag_id) DESC LIMIT 0,".$count
);
$sql = $modx-&gt;db-&gt;makeArray($sql);
foreach($sql as $item){
	$out[]=$modx-&gt;parseChunk($tpl,$item,"[+","+]");
}
return implode((isset($outSep) ? $outSep : ""),$out);
</pre>

<p>У сніппета є 3 параметра </p>
<ul>
	<li><span class="text-bold">count</span> – скількі тегів виводити (за замовчуванням 10)</li>
	<li><span class="text-bold">tv</span> – Ідентификатор TV змінної в якій зберігаються теги</li>
	<li><span class="text-bold">tpl</span> – чанк в котрий будуть підставляться теги. У мене він виглядає так
		<pre class="brush: php;">&lt;a href="/[~11~]?tag=[[urlencode? &amp;input=`[+name+]`]]" title="Статті з тегом [+name+]" class="label"&gt;[+name+] ([+count+])&lt;/a&gt;
	</pre>
	</li>
</ul>
<p>Як бачимо, цей сніппет не тільки теги підставляє, але ще й считує скільки разів вони використовуються. Таким чином виклик сніппета для хмари тегів виглядає так:</p>
<pre class="brush: html;">[[TagCloud? &amp;tpl=`TagCloudItem` &amp;tv=`7` &amp;count=`20`]]</pre>

<h3 class="sub-header">А що за сніппет urlencode?</h3>
<pre class="brush: php;">
return isset($input) ? urlencode($input) : '';
</pre>
<p>Для чого він потрібний найдете в гуглі</p>
<p>В силу того, що мені доволі часто приходиться працювати з сайтами зробленими іншими программістами, то можу сказати вам одне – таких рішень ще ніде небуло. Всі сортуют за страрими стандартами Ditto і винаходять свої велосипеди у вигляді екстендерів для нього. Моє рішення дозволяє вам працювати з видимою частиною також, як і раніше. Проте суттєво знімає навантаження на сервер при сортуваннях. І полегшує вибірку навіть якщо ви використовуєте знаменитий сніппет DropDownDocs для прив'язки статей до декількох розділів (адже по суті це також теги, тільки вигляд з боку). Відповідно, якщо вам потрібні теги й сортування за параметрам TV в значенні котрих може бути декілька даних – використовуйте <a href="https://gist.github.com/4690798" rel="nofollow" target="_blank">TagSaver</a>.</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/AgelxNash" rel="nofollow" target="_blank">Agel_Nash</a></p>
