
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Параметры glossaryFilter</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1146"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1146"><span class="text-bold">&filterVar</span> - поле документа или переменная шаблона, используемая для сопоставления</a></h4>
</div>
<div id="collapse1146" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле документа | TV-параметр<br>
<span class="text-bold">Значение по умолчанию:</span> pagetitle<br>
<span class="text-bold">Примечание:</span> ВАЖНО! Вам лучше избегать использования поля content, либо делать это осмотрительно<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&filterVar=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1147"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1147"><span class="text-bold">&filterMode</span> - тип сопоставления</a></h4>
</div>
<div id="collapse1147" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> class | custom | chunk<br>
<span class="text-bold">Значение по умолчанию:</span> class<br>
<span class="text-bold">Примечание:</span> class (default) - match with RegExp /^[...]/i where ... is substituted with the value of filterBy parameter
<br>custom - match with full-fledged RegExp provided with filterBy parameter
<br>chunk - match with full-fledged RegExp privided with a chunk whose name is kept within filterBy parameter<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&filterMode=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1148"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1148"><span class="text-bold">&filterBy</span> - условие для сопоставления</a></h4>
</div>
<div id="collapse1148" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> <br>
<span class="text-bold">Значение по умолчанию:</span> <br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&filterBy=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1149"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1149"><span class="text-bold">&forceUTF8</span> - рассматривать ли значение filterBy как UTF-8 строку</a></h4>
</div>
<div id="collapse1149" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&forceUTF8=`1`</pre>
</div>
</div>
</div>
</div>