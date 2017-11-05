
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Yams: Wayfinder и YAMS</h2>

<p>Вызов Wayfinder– a:</p>
<pre class="brush: html;">[[Wayfinder? &startId=`0`  &useWeblinkUrl=`true` &rowTpl=`menu_tpl`]]</pre>
<p>YAMS-у требуется, чтобы параметр &useWeblinkUrl был включён.</p>
<p>Чтобы Wayfinder правильно генерировал ссылки, всё в шаблоне работает через сниппет YAMS.</p>
<p>Шаблон одной кнопки – menu_tpl:</p>
<pre class="brush: html;">
&lt;li [+wf.id+][+wf.classes+]>
	<a href="(yams_doc-%5B+wf.docid+%5D).html" [+wf.attributes+]>[[YAMS? &get=`content` &docid=`[+wf.docid+]` &from=`pagetitle`]]</a>
	[+wf.wrapper+]
&lt;/li>
</pre>