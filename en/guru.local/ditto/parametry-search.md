
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Параметры search</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1155"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1155"><span class="text-bold">&searchFields</span> - поля и переменные шаблона, по которым происходит поиск</a></h4>
</div>
<div id="collapse1155" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> список полей через запятую<br>
<span class="text-bold">Значение по умолчанию:</span> content<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&searchFields=`content,tv1,tv2`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1156"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1156"><span class="text-bold">&searchOptions</span> - параметры поиска</a></h4>
</div>
<div id="collapse1156" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> caseSensitive | regex | snippet<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> caseSensitive - производить поиск с учетом регистра<br>
regex - поиск с регулярными выражениями<br>
snippet - использование сниппетов для получения результатов<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&searchOptions=`caseSensitive`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1157"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1157"><span class="text-bold">&searchString</span> - поисковый запрос</a></h4>
</div>
<div id="collapse1157" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка | @FILE | @CHUNK<br>
<span class="text-bold">Значение по умолчанию:</span> пусто<br>
<span class="text-bold">Примечание:</span> JSON строка с разделителями для списка опций. <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&searchString=`@CHUNK regexSearchChunk`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1158"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1158"><span class="text-bold">&searchOptionsSeparators</span> - разделитель параметров поиска</a></h4>
</div>
<div id="collapse1158" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка | @FILE | @CHUNK<br>
<span class="text-bold">Значение по умолчанию:</span> '{"outer":",","inner":"="}'<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&searchOptionsSeparators=``</pre>
</div>
</div>
</div>
</div>