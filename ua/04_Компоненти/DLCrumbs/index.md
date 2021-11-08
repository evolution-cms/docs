
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>DLCrumbs - breadcrumbs за допомогою DocLister </h3>
<p>Сніпет для створення навігації breadcrumbs за допомогою DocLister. Ви можете використовувати будь-який з параметрів DocLister у виклику DLCrumbs.</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/AgelxNash" rel="nofollow" target="_blank">Agel_Nash</a></p>
<h2 class="page-header">Параметри</h2>
<h3 class="sub-header text-bold">id</h3>
<p>ID поточної сторінки.</p>
<p>Значення за замовчуванням:</p>
<pre class="brush: php;">
$modx-&gt;documentIdentifier
</pre>
<h3 class="sub-header text-bold">hideMain</h3>
<p>Встановіть значення 1, якщо необхідно заховати посилання на домашню сторінку..</p>
<p>Значення за замовчуванням: 0.</p>
<h3 class="sub-header text-bold">showCurrent</h3>
<p>Встановіть значення 1, щоб включити поточну сторінку.</p>
<p>Значення за замовчуванням: 0..</p>
<h3 class="sub-header text-bold">minDocs</h3>
<p>Цей параметр визначає мінімальну кількість відображуваних елементів.</p>
<p>Значення за замовчуванням: 0..</p>

<h2 class="page-header">Шаблони</h2>
<h3 class="sub-header text-bold">tpl</h3>
<p>Шаблон виведення крихти.</p>
<p>Значення за замовчуванням: </p>
<pre class="brush: html;">
@CODE:&lt;li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;&lt;meta itemprop="position" content="[+iteration+]" /&gt;
	&lt;a href="[+url+]" title="[+e.title+]" itemprop="item"&gt;
		&lt;span itemprop="name"&gt;[+title+]&lt;/span&gt;
	&lt;/a&gt;
&lt;/li&gt;
</pre>
<h3 class="sub-header text-bold">tplFirst</h3>
<p>Шаблон виведення першого пункту.</p>
<p>Значення за замовчуванням: немає</p>
<p>Приклад шаблону для домашньої сторінки</p>
<pre class="brush: html;">
@CODE:&lt;li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem" class="home-link"&gt;
	&lt;meta itemprop="position" content="[+iteration+]" /&gt;
	&lt;a href="[+url+]" title="[+longtitle+]" itemprop="item" class="icon icon-home"&gt;&lt;i class="fa fa-home"&gt;&lt;/i&gt;&lt;/a&gt;
&lt;/li&gt;
</pre>
<h3 class="sub-header text-bold">tplCurrent</h3>
<p>Шаблон виведення поточної сторінки.</p>
<p>Значення за замовчуванням:</p>
<pre class="brush: html;">
@CODE:&lt;li class="active" itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"&gt;
	&lt;meta itemprop="position" content="[+iteration+]" /&gt;
	&lt;span itemprop="item"&gt;[+title+]&lt;/span&gt;
&lt;/li&gt;
</pre>
<h3 class="sub-header text-bold">ownerTPL</h3>
<p>Шаблон обгортки.</p>
<p>Значення за замовчуванням:</p>
<pre class="brush: html;">
@CODE:&lt;nav class="breadcrumbs"&gt;
	&lt;ul class="breadcrumb" itemscope itemtype="http://schema.org/BreadcrumbList"&gt;
		[+crumbs.wrap+]
	&lt;/ul&gt;
&lt;/nav&gt;
</pre>
