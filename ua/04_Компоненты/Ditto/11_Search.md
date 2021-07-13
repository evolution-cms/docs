
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Ditto: Параметри search </h3> 
Параметри search сніпета Ditto.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1155"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1155"><span class="text-bold">&searchFields</span> - поля і змінні шаблону, за якими відбувається пошук</a></h4>
</div>
<div id="collapse1155" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> список полів через кому<br>
<span class="text-bold">Значення за замовчуванням:</span> content<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&searchFields=`content,tv1,tv2`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1156"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1156"><span class="text-bold">&searchOptions</span> - параметри пошуку</a></h4>
</div>
<div id="collapse1156" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> caseSensitive | regex | snippet<br>
<span class="text-bold">Значення за замовчуванням:</span> ні<br>
<span class="text-bold">Примітка:</span> caseSensitive - проводити пошук з урахуванням регістру<br>
regex - пошук з регулярними виразами<br>
snippet - використання фрагментів для отримання результатів<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&searchOptions=`caseSensitive`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1157"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1157"><span class="text-bold">&searchString</span> - пошуковий запит</a></h4>
</div>
<div id="collapse1157" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> рядок | @FILE | @CHUNK<br>
<span class="text-bold">Значення за замовчуванням:</span> порожньо<br>
<span class="text-bold">Примітка:</span> JSON рядок з роздільниками для списку опцій. <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&searchString=`@CHUNK regexSearchChunk`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="1158"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse1158"><span class="text-bold">&searchOptionsSeparators</span> - роздільник параметрів пошуку</a></h4>
</div>
<div id="collapse1158" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> рядок | @FILE | @CHUNK<br>
<span class="text-bold">Значення за замовчуванням:</span> '{"outer":",","inner":"="}'<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&searchOptionsSeparators=``</pre>
</div>
</div>
</div>
</div>
