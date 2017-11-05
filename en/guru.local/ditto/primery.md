
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Примеры</h2>

<h3 class="sub-header text-bold">Простой вызов</h3>
<pre class="brush: html;">[!Ditto? &tpl=`news_tpl` &parents=`2`!] // некэшируемый вызов
[[Ditto? &tpl=`news_tpl` &parents=`2`]] // кэшируемый вызов</pre>
<p>где:</p>
<p><code>&tpl=`news_tpl`</code> - шаблон вывода документов</p>
<p><code>&parents=`2`</code> - ID папки в которой находятся обрабатываемые документы</p>

<h3 class="sub-header text-bold">Сортировка документов</h3>
<pre class="brush: html;">[!Ditto? &tpl=`news_tpl` &parents=`2` &orderBy=`pagetitle ASC`!]</pre>
<p>где:</p>
<p><code>&orderBy=`ASC pagetitle`</code> - сортировать по возрастанию по полю заголовка документов</p>

<h3 class="sub-header text-bold">Пагинация</h3>
<pre class="brush: html;">[!Ditto? &tpl=`news_tpl` &parents=`2` &id=`news` &paginate=`1` &display=`10`!]
&lt;div class="pagination"&gt;
Страница [+news_currentPage+] из [+news_totalPages+] [+news_previous+][+news_pages+][+news_next+]
&lt;/div&gt; </pre>
<p>где:</p>
<p><code>&id=`news`</code> - идентификатор Ditto. Должен быть уникальным для каждого из вызовов Ditto с постраничным разбиением. Необходим для корректной работы постраничных плэйсхолдеров, если на странице используются и другие вызовы сниппета Ditto</p>
<p><code>&paginate=`1`</code> - включаем постраничное разбиение</p>
<p><code>&display=`10`</code> - количество отображаемых документов на каждой странице</p>
<p>При использовании идентификатора при постраничном разбиении, идентификатор должен быть добавлен в качестве суффикса к плэйсхолдерам пагинации, т.е. в данном случае плэйсхолдер <code>[+pages+]</code> должен превратиться в <code>[+news_pages+]</code>.</p>

<h3 class="sub-header text-bold">Вывод даты</h3>
<pre class="brush: html;">[!Ditto? &tpl=`news_tpl` &parents=`2` &dateSource=`pub_date` &dateFormat=`%d.%m.%Y`!]</pre>
<p>где:</p>
<p><code>&dateSource=`pub_date`</code> - источник, определяющий значение плейсхолдера <code>[+date+]</code>, использующегося в шаблоне news_tpl</p>
<p><code>&dateFormat=`%d.%m.%Y`</code> - определяет формат времени, которое выводится с помощью плейсхолдера <code>[+date+]</code> согласно правилам функции PHP - strftime.</p>

<h3 class="sub-header text-bold">Фильтрация документов</h3>
<pre class="brush: html;">[!Ditto? &tpl=`news_tpl` &parents=`2` &filter=`id,10,2|id,20,2`!]</pre>
<p>где:</p>
<p><code>&filter=`id,10,2|id,20,2`</code> - исключает документы с id 10 и 20</p>

<h3 class="sub-head">Вызов в сниппете</h3>
<pre class="brush: php;">
$modx->runSnippet(
	'Ditto', 
	array(
		'startID' => 34,33,37,35,36,
		'summarize' => 9,
		'tpl' => 'portfolioTpl',
		'dateFormat' => '%d.%m.%Y',
		'dateSource' => 'pub_date',
		'display' => 9,
		'paginate' => 1,
		'paginateAlwaysShowLinks' => 1,
		'filter' => 'year,'.$_GET['year'].',1'
	)
);
</pre>