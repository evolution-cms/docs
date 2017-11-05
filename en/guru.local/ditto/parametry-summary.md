
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Параметры summary</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="523"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse523"><span class="text-bold">&truncSplit</span> - Документ должен быть получен в итоге с разделителем?</a></h4>
</div>
<div id="collapse523" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&truncSplit=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="597"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse597"><span class="text-bold">&trunc</span> - Включить/отключить обрезание для [+summary+]</a></h4>
</div>
<div id="collapse597" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br> 
<span class="text-bold">0</span> - выкл<br>
<span class="text-bold">1</span> - вкл<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&trunc=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="598"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse598"><span class="text-bold">&truncAt</span> - Текст, служащий разделителем для [+summary+]</a></h4>
</div>
<div id="collapse598" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка<br>
<span class="text-bold">Значение по умолчанию:</span> &lt;!-- splitter --&gt;<br>
<span class="text-bold">Примечание:</span> Любой уникальный текст или код, который содержится в содержании каждого документа<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&truncAt=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="599"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse599"><span class="text-bold">&truncLen</span> - Ограничение длины в [+summary+]</a></h4>
</div>
<div id="collapse599" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 300<br>
<span class="text-bold">Примечание:</span> Любое число больше чем &truncOffset<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&truncLen=`800`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="600"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse600"><span class="text-bold">&truncOffset</span> - Количество "блуждающих" символов от truncLen</a></h4>
</div>
<div id="collapse600" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 30<br>
<span class="text-bold">Примечание:</span> Любое число не превышающее &truncLen<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&truncOffset=`50`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="601"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse601"><span class="text-bold">&truncText</span> - Текст ссылки в [+link+]</a></h4>
</div>
<div id="collapse601" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка<br>
<span class="text-bold">Значение по умолчанию:</span> Read more...<br>
<span class="text-bold">Примечание:</span> Любой текст или отрывок html-кода<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&truncText=`Читать далее...`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="602"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse602"><span class="text-bold">&tplTrunc</span> - Шаблон для [+link+]</a></h4>
</div>
<div id="collapse602" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> &truncText<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplTrunc=``</pre>
</div>
</div>
</div>
</div>