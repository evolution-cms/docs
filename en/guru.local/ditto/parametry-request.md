
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Параметры request</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="524"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse524"><span class="text-bold">&stripTags</span> - Удаление HTML-тегов из предоставленных параметров</a></h4>
</div>
<div id="collapse524" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&stripTags=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="525"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse525"><span class="text-bold">&bad</span> - Параметры, которые не могут быть установлены через экстендер</a></h4>
</div>
<div id="collapse525" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Параметры Ditto через запятую<br>
<span class="text-bold">Значение по умолчанию:</span> seeThroughtUnpub, showInMenuOnly, showPublishedOnly, debug, start, config, extenders, dittoID<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&bad=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="526"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse526"><span class="text-bold">&good</span> - Параметры, которые могут быть установлены с помощью экстендера</a></h4>
</div>
<div id="collapse526" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Параметры Ditto через запятую<br>
<span class="text-bold">Значение по умолчанию:</span> Все параметры, которые не вошли в список bad<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&good=``</pre>
</div>
</div>
</div>
</div>