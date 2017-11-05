
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Параметры пагинации</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="569"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse569"><span class="text-bold">&paginate</span> - Включает / выключает разбиение по страницам</a></h4>
</div>
<div id="collapse569" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> На каждой странице выведется &show документов. Для вывода пэйджера используются глобальные плэйсхолдеры:<br>
[+next+] – Кнопка «Следующее»<br>
[+previous+] – Кнопка «Предыдущее»<br>
[+pages+] – Список страниц<br>
[+totalPages+] – Общее количество страниц<br>
[+start+] – Номер первой показываемой страницы<br>
[+stop+] – Номер последней показываемой страницы<br>
[+currentPage+] – Номер показываемой текущей страницы<br>
[+total+] – Общее количество страниц<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&paginate=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="570"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse570"><span class="text-bold">&paginateAlwaysShowLinks</span> - Показывать ли [+next+] и [+previous+] всегда</a></h4>
</div>
<div id="collapse570" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> В случае если страницы для перехода нет (крайние страницы), то ссылка Previous или Next будет показана в виде текста без ссылки и будет заключена в тэг &lt;spanclass="ditto_off"&gt;Privious&lt;/span&gt;<br>
0 - показывать ссылки Next и Previous только, если существуют страницы для перехода<br>
1 - всегда показывать ссылки Next и Privious<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&paginateAlwaysShowLinks=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="571"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse571"><span class="text-bold">&paginateSplitterCharacter</span> - Символ для разделения Previous и Next</a></h4>
</div>
<div id="collapse571" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> символ (или строка)<br>
<span class="text-bold">Значение по умолчанию:</span> |<br>
<span class="text-bold">Примечание:</span> Символ для разделения Previous и Next, когда paginateAlwaysShowLinks выключен и обе ссылки есть. Предотвращает показ ссылок в виде &lt;Previous Next&gt;, когда [+pages+] не используется<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&paginateSplitterCharacter=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="591"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse591"><span class="text-bold">&tplPaginateCurrentPage</span> - Шаблон для ссылки текущей страницы</a></h4>
</div>
<div id="collapse591" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaginateCurrentPage=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="592"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse592"><span class="text-bold">&tplPaginateNext</span> - Шаблон оформления ссылки Next</a></h4>
</div>
<div id="collapse592" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaginateNext=`newsPaginateNext`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="593"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse593"><span class="text-bold">&tplPaginatePrevious</span> - Шаблон оформления ссылки Previous</a></h4>
</div>
<div id="collapse593" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaginatePrevious=`newsPaginatePrevious`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="594"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse594"><span class="text-bold">&tplPaginateNextOff</span> - Шаблон для внутренней части следующей ссылки</a></h4>
</div>
<div id="collapse594" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FIL<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaginateNextOff=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="595"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse595"><span class="text-bold">&tplPaginatePage</span> - Шаблон для ссылок на страницы</a></h4>
</div>
<div id="collapse595" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaginatePage=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="596"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse596"><span class="text-bold">&tplPaginatePreviousOff</span> - Шаблон для предыдущей ссылки, когда он выключен</a></h4>
</div>
<div id="collapse596" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br> 
Любое валидное название чанка<br>
Код через @CODE<br>
Файл через @FILE<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaginatePreviousOff=``</pre>
</div>
</div>
</div>
</div>