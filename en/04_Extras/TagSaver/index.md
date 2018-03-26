
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>TagSaver: Плагин для работы с тегами </h3>
Плагин TagSaver для работы с тегами.
<p>Вообще, фильтрация по тегам в MDOX реализуется довольно кисло. Представьте, у вас есть какой-то TV параметр, в котором у вас к каждой статье прописано по 10 тегов.</p>
<p>А в базе все эти теги для документа хранятся в одной строке. Т.е. Выглядит это примерно так</p>
<pre class="brush: php;">modx, теги, работа с тегами, фильтрация по тегам</code></pre>
<p>Как обычно происходит фильтрация? Создается SQL запрос в таблицу site_tmplvar_contentvalues с применением WHERE value LIKE %тег%</p>
<p>Таким образом, мы можем искать не только по тем тегам, которые задумывались автором сайта, но и по тегам</p>
<ul>
	<li>и, р</li>
	<li>ми, фи</li>
	<li>льтра</li>
	<li>бот</li>
	<li>фил</li>
	<li>mod</li>
</ul>
<p>Более того, если документов очень много, то поиск происходит нереально долго. Как вообще идеально должна выглядеть работа с тегами?</p>
<p><span class="text-bold">Таблица с документами вида</span>: id, content, pagetitle</p>
<p><span class="text-bold">Таблица с тегами</span>: id, tag</p>
<p><span class="text-bold">Таблица связей с тегами</span>: doc_id, tag_id </p>
<p>Можно конечно долго спорить о необходимости таблицы связи, т.к. придется делать лишний JOIN. Но за счет правильно расставленых индексов этот джоин вообще незаметен. Более того, немного доработав таблицу мы можем забивать теги в нескольких TV-шках, а хранить в одной таблице по вышеописаному стандарту.</p>
<p>На основании всего вышесказанного у нас получаются вот такие 2 таблицы</p>
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
<p>Как можно заметить, формат у таблиц MyISAM. Но у такого выбора есть своя причина. Одна из них это auto_increment. А вторая – уникальный ключ по нескольким полям. Не буду долго задерживаться на этом пункте. Скажу одно – если у вас MODX установлен с префиксом таблиц отличным от modx, то измените его на свой;-)</p>

<h3 class="sub-header">Создали таблицы? И что? Как теперь инфу то в них добавлять?</h3>
<p>Все очень просто. Создаете как обычно TV параметр. Можете даже добавить виджет mm_widget_tags от ManagerManager. После этого создаете плагин <a href="https://gist.github.com/4690798" rel="nofollow" target="_blank">TagSaver</a> с параметрами</p>
<pre class="brush: html;">&amp;tv=ID TV-параметра;input; &amp;sep=Разделитель тегов;input;</pre>
<p>Если разделителя нет, то можно оставить пустым.</p>

<h3 class="sub-header">Что делать если мне нужно 2 поля с тегами?</h3>
<p>Создавайте копию плагина под другим именем с аналогичными параметрами. Только не забудьте у новой версии плагина указать разделитель и ID другого TV параметра.</p>

<h3 class="sub-header">Почему плагин делает SELECT за значениями TV, а не принимает $_POST['tv'.$tv]?</h3>
<ol>
	<li>Мы работаем в админке и ± 1 SQL запрос особого вреда не принесет</li>
	<li>Могут стоять другие плагины которые вызываются раньше и изменят значение сохраняемого TV параметра</li>
	<li>Значение TV параметра из $_POST может отличаться от сохраненного в базу</li>
</ol>

<h3 class="sub-header">Как вывести на странице теги привязаные к текущей стрнице?</h3>
<p>Выводить их можете как и раньше – через сниппеты DocInfo, просто подставляя tv параметр на странице .</p>

<h3 class="sub-header">Как теперь отфильтровать данные по нужному тегу?</h3>
<p>Очень просто. Создаете сниппет примерно такого содержания</p>
<pre class="brush: php;">
$tag = ((isset($tag) &amp;&amp; is_scalar($tag))? $tag : (isset($_GET['tag']) &amp;&amp; !is_array($_GET['tag']) ? $_GET['tag'] : ''));
$id = isset($id) ? (int)$id : 0;
$out = array();
if($id&gt;0 &amp;&amp; $tag!=''){
	$sql=$modx-&gt;db-&gt;query("SELECT doc_id FROM ".$modx-&gt;getFullTableName("tags")." as t
	LEFT JOIN ".$modx-&gt;getFullTableName("site_content_tags")." s ct ON ct.tag_id = id
	WHERE t.`name`='".$modx-&gt;db-&gt;escape($tag)."' AND ct.tv_id={$id}");
	$sql=$modx-&gt;db-&gt;makeArray($sql);
	foreach($sql as $item){
		$out[]=$item['doc_id'];
	}
}
return implode(",",$out);
</pre>

<p>И результат работы этого сниппета передаете в параметр documents от Ditto. У сниппета указаного выше есть 2 параметра:</p>
<ul>
	<li><span class="text-bold">tag</span> – если этот параметр передан, то сниппет использует его значение. В противном случа пытается взять значение $_GET переменной tag</li>
	<li><span class="text-bold">id</span> – Идентификатор TV переменной в которой хранятся теги</li>
</ul>
<p>Получается примерно так</p>
<pre class="brush: html;">[[Ditto? &amp;documents=`[!GetTag? &amp;id=`2`!]`]]</pre>
<h3 class="sub-header">Как теперь вывести популярные теги?</h3>
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

<p>У сниппета 3 параметра </p>
<ul>
	<li><span class="text-bold">count</span> – сколько тегов выводить (по умолчанию 10)</li>
	<li><span class="text-bold">tv</span> – Идентификатор TV переменной в которой хранятся теги</li>
	<li><span class="text-bold">tpl</span> – чанк в который будут подставляться теги. У меня он выглядит так
		<pre class="brush: php;">&lt;a href="/[~11~]?tag=[[urlencode? &amp;input=`[+name+]`]]" title="Статьи с тегом [+name+]" class="label"&gt;[+name+] ([+count+])&lt;/a&gt;
	</pre>
	</li>
</ul>
<p>Как видно, этот сниппет не только теги подставляет, но еще и считает сколько раз они используются. Таким образом вызов сниппета для облака тегов выглядит так:</p>
<pre class="brush: html;">[[TagCloud? &amp;tpl=`TagCloudItem` &amp;tv=`7` &amp;count=`20`]]</pre>

<h3 class="sub-header">А что за сниппет urlencode?</h3>
<pre class="brush: php;">
return isset($input) ? urlencode($input) : '';
</pre>
<p>Для чего он нужен найдете в гугле</p>
<p>В силу того, что мне довольно часто приходится работать с сайтами сделаными другими программистами, то могу сказать вам одно – таких решений еще нигде небыло. Все фильтруют по старинке средствамми Ditto и изобретают свои велосипеды в виде экстендеров для него. Мое решение повзоляет вам работать с видимой частью так же, как и раньше. Зато существенно снимает нагрузку на сервер при фильтрациях. И облегчает выборку даже если вы используете знаменитый сниппет DropDownDocs для привязки статей к нескольким разделам (ведь по сути это тоже теги, только вид с боку). Соответственно, если вам нужны теги и фильтрации по TV параметрам в значении которых может быть несколько данных – используйте <a href="https://gist.github.com/4690798" rel="nofollow" target="_blank">TagSaver</a>.</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/AgelxNash" rel="nofollow" target="_blank">Agel_Nash</a></p>