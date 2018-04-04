
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Ditto: Параметры tagging </h3> 
Параметры tagging сниппета Ditto.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="527"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse527"><span class="text-bold">&tagDocumentID</span> - ID документа где будет выводиться отфильтрованный список документов</a></h4>
</div>
<div id="collapse527" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> <br>
<span class="text-bold">Значение по умолчанию:</span> <br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagDocumentID=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="528"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse528"><span class="text-bold">&tags</span> - Установить теги для фильтрации</a></h4>
</div>
<div id="collapse528" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любые допустимые теги, разделенные с помощью tagDelimiter<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Любые допустимые теги, разделенные с помощью tagDelimiter<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tags=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="529"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse529"><span class="text-bold">&tagMode</span> - Выбрать или скрыть документы со всеми или любым из тегов</a></h4>
</div>
<div id="collapse529" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> onlyAllTags | onlyTags | removeAllTags | removeTags<br>
<span class="text-bold">Значение по умолчанию:</span> onlyTags<br>
<span class="text-bold">Примечание:</span> <br>onlyAllTags показать документа, содержащие все теги из параметра tags
<br>onlyTags показать документы, которые имеют любой из тегов tags
<br>removeAllTags удалить документы, которые содержат все теги tags
<br>removeTags удалить документы, которые имеют любой из тегов tags <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagMode=`onlyAllTags`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="530"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse530"><span class="text-bold">&tagDelimiter</span> - Разделитель между тегами</a></h4>
</div>
<div id="collapse530" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка<br>
<span class="text-bold">Значение по умолчанию:</span> пробел<br>
<span class="text-bold">Примечание:</span> Любой символ, не содержащийся в тегах<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagDelimiter=`, `</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="531"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse531"><span class="text-bold">&caseSensitive</span> - Включает/выключает дублирование тегов, чувствителен к регистру</a></h4>
</div>
<div id="collapse531" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> 1 - вкл., 0 - выкл.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&caseSensitive=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="532"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse532"><span class="text-bold">&tagDisplayDelimiter</span> - Разделитель между тегами при их выводе</a></h4>
</div>
<div id="collapse532" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка<br>
<span class="text-bold">Значение по умолчанию:</span> значение параметра tagDelimiter<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagDisplayDelimiter=`, `</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="533"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse533"><span class="text-bold">&tagSort</span> - Сортировать теги по алфавиту</a></h4>
</div>
<div id="collapse533" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagSort=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="582"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse582"><span class="text-bold">&tagData</span> - Поле, содержащее информацию</a></h4>
</div>
<div id="collapse582" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Поле документа или переменная шаблона<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> автоматически добавляет в пометки Extender<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagData=`tags`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="534"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse534"><span class="text-bold">&tagDisplayMode</span> - Формат отображения тегов в плэйсхолдере tagLinks</a></h4>
</div>
<div id="collapse534" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 1 | 2<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>1 - строка с ссылками и разделителем tagDisplayDelimiter)
<br>2 - UL/LI список<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagDisplayMode=`2`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="535"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse535"><span class="text-bold">&tplTagLinks</span> - Шаблон для вывода плэйсхолдера tagLinks</a></h4>
</div>
<div id="collapse535" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplTagLinks=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="536"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse536"><span class="text-bold">&tagCallback</span> - Имя функции для обработки тегов</a></h4>
</div>
<div id="collapse536" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> любое допустимое имя функции<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tagCallback=``</pre>
</div>
</div>
</div>
</div>