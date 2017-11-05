
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Шаблоны</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="586"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse586"><span class="text-bold">&tpl</span> - шаблон для записи</a></h4>
</div>
<div id="collapse586" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tpl=`news`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="587"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse587"><span class="text-bold">&tplAlt</span> - Шаблон для четных документов</a></h4>
</div>
<div id="collapse587" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> &tpl<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplAlt=`news_alt`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="588"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse588"><span class="text-bold">&tplCurrentDocument</span> - Шаблон текущего документа</a></h4>
</div>
<div id="collapse588" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> &tpl<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplCurrentDocument=`news_current`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="589"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse589"><span class="text-bold">&tplFirst</span> - Шаблон для первого документа</a></h4>
</div>
<div id="collapse589" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> &tpl<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplFirst=`news_first`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="590"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse590"><span class="text-bold">&tplLast</span> - Шаблон для последнего документа</a></h4>
</div>
<div id="collapse590" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> &tpl<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplLast=`news_last`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="853"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse853"><span class="text-bold">&outerTpl</span> - Шаблон контейнера Ditto (v 2.1.1)</a></h4>
</div>
<div id="collapse853" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Доступные плейсхолдеры:<br>
<code>[+ditto+]</code> 
или идентичный ему
<code>[+wrapper+]</code><br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&outerTpl=`&lt;ul&gt;[+ditto+]&lt;/ul&gt;`</pre>
</div>
</div>
</div>
</div>