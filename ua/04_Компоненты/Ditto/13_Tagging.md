
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Ditto: Параметри tagging </h3> 
Параметри tagging сніпета Ditto.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="527"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse527"><span class="text-bold">&tagDocumentID</span> - ID документа де буде виводитися відфільтрований список документів</a></h4>
</div>
<div id="collapse527" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> <br>
<span class="text-bold">Значення за замовчуванням:</span> <br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagDocumentID=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="528"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse528"><span class="text-bold">&tags</span> - Встановити теги для фільтрації</a></h4>
</div>
<div id="collapse528" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Будь-які допустимі теги, розділені за допомогою tagDelimiter<br>
<span class="text-bold">Значення за замовчуванням:</span> ні<br>
<span class="text-bold">Примітка:</span> Будь-які допустимі теги, розділені за допомогою tagDelimiter<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tags=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="529"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse529"><span class="text-bold">&tagMode</span> - Вибрати або приховати документи з усіма або будь-яким з тегів</a></h4>
</div>
<div id="collapse529" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> onlyAllTags | onlyTags | removeAllTags | removeTags<br>
<span class="text-bold">Значення за замовчуванням:</span> onlyTags<br>
<span class="text-bold">Примітка:</span> <br>onlyAllTags показати документа, що містять всі теги з параметра tags
<br>onlyTags показати документи, які мають будь-який з тегів tags
<br>removeAllTags видалити документи, які містять всі теги tags
<br>removeTags видалити документи, які мають будь-який з тегів tags <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagMode=`onlyAllTags`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="530"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse530"><span class="text-bold">&tagDelimiter</span> - Роздільник між тегами</a></h4>
</div>
<div id="collapse530" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> рядок<br>
<span class="text-bold">Значення за замовчуванням:</span> пробіл<br>
<span class="text-bold">Примітка:</span> Будь-який символ, що не міститься в тегах<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagDelimiter=`, `</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="531"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse531"><span class="text-bold">&caseSensitive</span> - Вмикає/вимикає дублювання тегів, чутливий до регістру</a></h4>
</div>
<div id="collapse531" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 0<br>
<span class="text-bold">Примітка:</span> 1 - вкл., 0 - викл.<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&caseSensitive=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="532"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse532"><span class="text-bold">&tagDisplayDelimiter</span> - Роздільник між тегами при їх виведенні</a></h4>
</div>
<div id="collapse532" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> рядок<br>
<span class="text-bold">Значення за замовчуванням:</span> значення параметра tagDelimiter<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagDisplayDelimiter=`, `</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="533"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse533"><span class="text-bold">&tagSort</span> - Сортувати теги за алфавітом</a></h4>
</div>
<div id="collapse533" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagSort=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="582"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse582"><span class="text-bold">&tagData</span> - Поле, що містить інформацію</a></h4>
</div>
<div id="collapse582" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Поле документа або змінна шаблону<br>
<span class="text-bold">Значення за замовчуванням:</span> ні<br>
<span class="text-bold">Примітка:</span> автоматично додає в позначки Extender<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagData=`tags`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="534"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse534"><span class="text-bold">&tagDisplayMode</span> - Формат відображення тегів в плейсхолдере tagLinks</a></h4>
</div>
<div id="collapse534" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 1 | 2<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br>1 - рядок з посиланнями і роздільником tagDisplayDelimiter)
<br>2 - UL/LI перелік<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagDisplayMode=`2`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="535"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse535"><span class="text-bold">&tplTagLinks</span> - Шаблон для виведення плейсхолдера tagLinks</a></h4>
</div>
<div id="collapse535" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ім'я чанка | @FILE | @CODE<br>
<span class="text-bold">Значення за замовчуванням:</span> ні<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tplTagLinks=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="536"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse536"><span class="text-bold">&tagCallback</span> - Ім'я функції для обробки тегів</a></h4>
</div>
<div id="collapse536" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> будь-яке припустиме ім'я функції<br>
<span class="text-bold">Значення за замовчуванням:</span> ні<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&tagCallback=``</pre>
</div>
</div>
</div>
</div>
