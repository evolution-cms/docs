
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>DLCrumbs - breadcrumbs с помощью DocLister </h3>
Сниппет для создания навигации breadcrumbs с помощью DocLister. Вы можете использовать любой из параметров DocLister в вызове DLCrumbs.
<p>Сниппет для создания навигации breadcrumbs с помощью DocLister. Вы можете использовать любой из параметров DocLister в вызове DLCrumbs.</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/AgelxNash" rel="nofollow" target="_blank">Agel_Nash</a></p>
<h2 class="page-header">Параметры</h2>
<h3 class="sub-header text-bold">id</h3>
<p>ID текущей страницы.</p>
<p>Значение по умолчанию:</p>
<pre class="brush: php;">
$modx-&gt;documentIdentifier
</pre>
<h3 class="sub-header text-bold">hideMain</h3>
<p>Установите значение 1, если необходимо спрятать ссылку на домашнию страницу.</p>
<p>Значение по умолчанию: 0.</p>
<h3 class="sub-header text-bold">showCurrent</h3>
<p>Установите значение 1, чтобы включить текущую страницу.</p>
<p>Значение по умолчанию: 0.</p>
<h3 class="sub-header text-bold">minDocs</h3>
<p>Этот параметр определяет минимальное количество отображаемых элементов.</p>
<p>Значение по умолчанию: 0.</p>

<h2 class="page-header">Шаблоны</h2>
<h3 class="sub-header text-bold">tpl</h3>
<p>Шаблон вывода крошки.</p>
<p>Значение по умолчанию: </p>
<pre class="brush: html;">
@CODE:&lt;li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;&lt;meta itemprop="position" content="[+iteration+]" /&gt;
	&lt;a href="[+url+]" title="[+e.title+]" itemprop="item"&gt;
		&lt;span itemprop="name"&gt;[+title+]&lt;/span&gt;
	&lt;/a&gt;
&lt;/li&gt;
</pre>
<h3 class="sub-header text-bold">tplFirst</h3>
<p>Шаблон вывода первого пункта.</p>
<p>Значение по умолчанию: нету</p>
<p>Пример шаблона для домашней страницы</p>
<pre class="brush: html;">
@CODE:&lt;li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem" class="home-link"&gt;
	&lt;meta itemprop="position" content="[+iteration+]" /&gt;
	&lt;a href="[+url+]" title="[+longtitle+]" itemprop="item" class="icon icon-home"&gt;&lt;i class="fa fa-home"&gt;&lt;/i&gt;&lt;/a&gt;
&lt;/li&gt;
</pre>
<h3 class="sub-header text-bold">tplCurrent</h3>
<p>Шаблон вывода текущей страницы.</p>
<p>Значение по умолчанию:</p>
<pre class="brush: html;">
@CODE:&lt;li class="active" itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;
	&lt;meta itemprop="position" content="[+iteration+]" /&gt;
	&lt;span itemprop="item"&gt;[+title+]&lt;/span&gt;
&lt;/li&gt;
</pre>
<h3 class="sub-header text-bold">ownerTPL</h3>
<p>Шаблон обертки.</p>
<p>Значение по умолчанию:</p>
<pre class="brush: html;">
@CODE:&lt;nav class="breadcrumbs"&gt;
	&lt;ul class="breadcrumb" itemscope itemtype="http://schema.org/BreadcrumbList"&gt;
		[+crumbs.wrap+]
	&lt;/ul&gt;
&lt;/nav&gt;
</pre>
