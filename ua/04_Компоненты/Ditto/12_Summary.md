<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Ditto: Параметри summary </h3> 
Параметри summary сніпета Ditto.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="523"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse523"><span class="text-bold">&truncSplit</span> - Документ повинен бути отриманий в результаті з роздільником?</a></h4>
</div>
<div id="collapse523" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&truncSplit=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="597"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse597"><span class="text-bold">&trunc</span> - Включити/відключити обрізання для [+summary+]</a></h4>
</div>
<div id="collapse597" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br> 
<span class="text-bold">0</span> - викл<br>
<span class="text-bold">1</span> - вкл<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&trunc=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="598"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse598"><span class="text-bold">&truncAt</span> - Текст, службовець роздільником для [+summary+]</a></h4>
</div>
<div id="collapse598" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> рядок<br>
<span class="text-bold">Значення за замовчуванням:</span> &lt;!-- splitter --&gt;<br>
<span class="text-bold">Примітка:</span> Будь унікальний текст або код, який міститься в змісті кожного документа<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&truncAt=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="599"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse599"><span class="text-bold">&truncLen</span> - Обмеження довжини в [+summary+]</a></h4>
</div>
<div id="collapse599" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значення за замовчуванням:</span> 300<br>
<span class="text-bold">Примітка:</span> Будь-яке число більше ніж &truncOffset<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&truncLen=`800`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="600"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse600"><span class="text-bold">&truncOffset</span> - Кількість "блукаючих" символів від truncLen</a></h4>
</div>
<div id="collapse600" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значення за замовчуванням:</span> 30<br>
<span class="text-bold">Примітка:</span> Будь-яке число не перевищує &truncLen<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&truncOffset=`50`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="601"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse601"><span class="text-bold">&truncText</span> - Текст посилання в [+link+]</a></h4>
</div>
<div id="collapse601" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> рядок<br>
<span class="text-bold">Значення за замовчуванням:</span> Read more...<br>
<span class="text-bold">Примітка:</span> Будь-який текст або уривок html-коду<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&truncText=`Читати далі...`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="602"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse602"><span class="text-bold">&tplTrunc</span> - Шаблон для [+link+]</a></h4>
</div>
<div id="collapse602" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ім'я чанка | @FILE | @CODE<br>
<span class="text-bold">Значення за замовчуванням:</span> &truncText<br>
<span class="text-bold">Примітка:</span> <br> 
Будь-яке валідності назву чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tplTrunc=``</pre>
</div>
</div>
</div>
</div>
