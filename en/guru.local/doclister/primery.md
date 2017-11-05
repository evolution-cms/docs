
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: Примеры</h2>

<h2 class="page-header">Простой пример без пагинации</h2>
<pre class="brush: html;">
[!DocLister? &amp;display=`20` &amp;summary=`notags,len` &amp;dateSource=`pub_date` &amp;parents=`5` &amp;tvList=`img,tag` &amp;id=`lastnews` &amp;tpl=`ListSummaryPost`!]
</pre>
<p>Выборка последних 20 документов из родителем которых является документ с ID=5. </p>
<p>Текст каждого документа будет подвержен дополнительной обработке классом summary с предварительным удалением html тегов и усечением длины текста до 200 +/- 50 символов. При этом в чанке будут доступны плейсхолдеры tv.img и tv.tag со значением TV параметров img и tag.</p>
<p>Для наглядности чанк ListSummaryPost</p>
<pre class="brush: html;">
&lt;div class="post"&gt;
&lt;div class="date"&gt;[+createdon+]&lt;/div&gt;
&lt;h3&gt;&lt;a href="/[~[+id+]~]"&gt;[+pagetitle+]&lt;/a&gt; &lt;/h3&gt;
&lt;div class="tag"&gt;&lt;span&gt;Теги: &lt;/span&gt; [+tv.tag+] &lt;/div&gt;
&lt;div class="content"&gt;
	&lt;a href="/[~[+id+]~]" title="[+pagetitle+]"&gt;&lt;img src="[+tv.img+]" /&gt;&lt;/a&gt;
	&lt;p&gt;[+summary+]...&lt;/p&gt;
	&lt;a href="/[~[+id+]~]" title="Подробнее"&gt;Подробнее&lt;/a&gt; 
&lt;/div&gt;
&lt;/div&gt;
</pre>
<h2 class="page-header">Использование конфигов</h2>
<pre class="brush: html;">
[!DocLister? &amp;config=`test`!]
</pre>
<p>После чего создаем JSON файл test.json в подпапке сниппета /config/custom/ с таким содержимым:</p>
<pre class="brush: php;">
{
	"display" : "20",
	"summary" : "notags,len", 
	"dateSource" : "pub_date",
	"parents" : "5",
	"tvList" : "img,tag",
	"id" : "lastnews",
	"tpl" : "ListSummaryPost"
}
</pre>
<p>Результат работы этого вызова будет идентичен предыдущему примеру.</p>
<h2 class="page-header">Использование лексиконов</h2>
<pre class="brush: html;">
[!DocLister? &amp;tpl=`example` &amp;customLang=`news`!]
</pre>
<p>После чего создаем php файл news.php с $_lang массивом в подпапке сниппета /lang/</p>
<pre class="brush: php;">
&lt;?php
if (!defined('MODX_BASE_PATH')){die('What are you doing? Get out of here!');}
$_lang = array();
$_lang['newsTitle'] = 'Последние новости';
return $_lang;
</pre>
<p>Теперь в чанке example можно использовать тег [%newsTitle%] и он автоматически будет заменен на сообщение "Последние новости".</p>
<h2 class="page-header">Сложный пример с пагинацией</h2>
<pre class="brush: html;">
[!DocLister?
&amp;display=`4`
&amp;depth=`2`
&amp;tpl=`ListSummaryPost`
&amp;summary=`notags,len:500`
&amp;dateFormat=`%d.%m.%Y в %H:%M`
&amp;dateSource=`pub_date`
&amp;parents=`2`
&amp;tvList=`img,tag`
&amp;renderTV=`img`
&amp;id=`list`
&amp;showParent=`0`
&amp;addWhereList=`c.template IN (6,7)`
&amp;sortBy=`menuindex`
&amp;paginate=`pages`
&amp;TplNextP=``
&amp;TplPrevP=``
&amp;TplPage=`@CODE: &lt;li&gt;&lt;a href="[+link+]"&gt;[+num+]&lt;/a&gt;&lt;/li&gt;`
&amp;TplCurrentPage=`@CODE: &lt;li class="active"&gt;&lt;a href="[+link+]"&gt;[+num+]&lt;/a&gt;&lt;/li&gt;`
&amp;TplWrapPaginate=`@CODE: &lt;div class="pagination"&gt;&lt;ul&gt;[+wrap+]&lt;/ul&gt;&lt;/div&gt;`!]
[+list.pages+]
</pre>
<p>В данном случае происходит выборка всех документов из контейнера с ID=2 с глубиной 2 и шаблонами 6 или 7. После чего будут отфильтрованы документы контейнеры (те документы внутри которых производился поиск. А именно - документ с ID=2 и все его дочерние элементы которые являются контейнерами). При выводе будет подготовлена пагинация типа page и переопределяется шаблоны для элементов пагинации на те, что указаны в параметрах TplWrapPaginate, TplCurrentPage и TplPage. Шаблоны для ссылок следующая и предыдущая будут пустыми (соответственно текст в этих элементах не будут выводиться). Ко всем плейсхолдерам сниппета DocLister добавится префикс list, а к каждому документ участвующему в выдаче прибавятся значения TV параметров img и tag в плейсхолдеры tv.img и tv.tag соответственно. TV параметр img будет отрендерен в соответствии с виджетом указанным при создании этого TV параметра. Всего на странице будет отображено по 4 документа. При этом сортировка будет произведена не по дате создания, а по menuindex (позиции в меню). В качестве источника даты будет браться дата публикации документа.</p>
<p>Для наглядности чанк ListSummaryPost</p>
<pre class="brush: html;">
&lt;div class="post"&gt;
&lt;div class="date"&gt;[+createdon+]&lt;/div&gt;
&lt;h3&gt;&lt;a href="/[~[+id+]~]"&gt;[+pagetitle+]&lt;/a&gt; &lt;/h3&gt;
&lt;div class="tag"&gt;&lt;span&gt;Теги: &lt;/span&gt; [+tv.tag+] &lt;/div&gt;
&lt;div class="content"&gt;
	&lt;a href="/[~[+id+]~]" title="[+pagetitle+]"&gt;[+tv.img+]&lt;/a&gt;
	&lt;p&gt;[+summary+]...&lt;/p&gt;
	&lt;a href="/[~[+id+]~]" title="Подробнее"&gt;Подробнее&lt;/a&gt; 
&lt;/div&gt;
&lt;/div&gt;
</pre>
<h2 class="page-header">Пример вывода информации из таблицы отличной от site_content</h2>
<pre class="brush: html;">
[!DocLister?
&amp;contentField=`snippet`
&amp;sortBy=`name`
&amp;sortDir=`ASC`
&amp;display=`10`
&amp;idField=`id`
&amp;table=`site_snippets`
&amp;tpl=`snippet`
&amp;controller=`onetable`
&amp;id=`snip`
&amp;showParent=`0`
&amp;paginate=`pages`!]
</pre>
<p>Чанк snippet</p>
<pre class="brush: html;">
&lt;div class="row"&gt;
	&lt;div class="span12"&gt;
		&lt;h3 class="pagination-centered"&gt;[+name+]&lt;/h3&gt;
		&lt;code&gt;[+snippet+]&lt;/code&gt;&lt;br /&gt;
		&lt;table class="table table-striped table-bordered"&gt;
			&lt;thead&gt;
				&lt;tr&gt;&lt;td&gt;&lt;strong&gt;field&lt;/strong&gt;&lt;/td&gt;&lt;td&gt;&lt;strong&gt;value&lt;/strong&gt;&lt;/td&gt;&lt;/tr&gt;
			&lt;/thead&gt;
			&lt;tbody&gt;
				&lt;tr&gt;&lt;td&gt;id&lt;/td&gt;&lt;td&gt;[+id+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;name&lt;/td&gt;&lt;td&gt;[+name+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;description&lt;/td&gt;&lt;td&gt;[+description+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;editor_type&lt;/td&gt;&lt;td&gt;[+editor_type+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;category&lt;/td&gt;&lt;td&gt;[+category+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;cache_type&lt;/td&gt;&lt;td&gt;[+cache_type+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;locked&lt;/td&gt;&lt;td&gt;[+locked+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;properties&lt;/td&gt;&lt;td&gt;[+properties+]&lt;/td&gt;&lt;/tr&gt;
				&lt;tr&gt;&lt;td&gt;moduleguid&lt;/td&gt;&lt;td&gt;[+moduleguid+]&lt;/td&gt;&lt;/tr&gt;
			&lt;/tbody&gt;
		&lt;/table&gt;
	&lt;/div&gt;
&lt;/div&gt;
&lt;hr /&gt;
</pre>
<p>В данном примере информация будет выводиться из таблицы site_snippets. В качестве колонки PrimaryKey выступает поле id. Сортировка происходит по возрастанию значений в колонке name.</p>