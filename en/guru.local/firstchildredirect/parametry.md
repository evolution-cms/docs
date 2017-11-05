
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>FirstChildRedirect: Параметры</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1686"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1686"><span class="text-bold">&docid</span> - id папки, в первый дочерний документ которой необходим редирект</a></h4>
</div>
<div id="collapse1686" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> id документа<br>
<span class="text-bold">Значение по умолчанию:</span> ID текущей страницы<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&docid=`12`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1687"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1687"><span class="text-bold">&default</span> - перадресация на документ в случае отсутствия дочерних документов</a></h4>
</div>
<div id="collapse1687" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> id доумента | site_start | site_unavailable_page | error_page | unauthorized_page<br>
<span class="text-bold">Значение по умолчанию:</span> site_start<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&default=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1688"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1688"><span class="text-bold">&sortBy</span> - получение первого документа в зависимости от сортировки</a></h4>
</div>
<div id="collapse1688" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле документа<br>
<span class="text-bold">Значение по умолчанию:</span> menuindex<br>
<span class="text-bold">Примечание:</span> любое допустимое поле документа<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&sortBy=`pagetitle`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1689"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1689"><span class="text-bold">&sortDir</span> - направление сортировки</a></h4>
</div>
<div id="collapse1689" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ASC | DESC<br>
<span class="text-bold">Значение по умолчанию:</span> ASC<br>
<span class="text-bold">Примечание:</span> <br>ASC - по возрастанию
<br>DESC - по убыванию<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&sortDir=`DESC`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1690"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1690"><span class="text-bold">&responseCode</span> - код перенаправления</a></h4>
</div>
<div id="collapse1690" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 301 | 302 | HTTP/1.1 302 Moved Temporarily<br>
<span class="text-bold">Значение по умолчанию:</span> 301<br>
<span class="text-bold">Примечание:</span> <br>
<br><br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&responseCode=`302`</pre>
</div>
</div>
</div>

</div>