
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>AjaxSearch: Шаблоны</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="118"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse118"><span class="text-bold">&tplInput</span> - шаблон формы поиска</a></h4>
</div>
<div id="collapse118" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ input.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>Примеры шаблонов находятся в папке: templates/inputTemplates/<br>
Input 1: простой поиск с простым вводом<br>
Input 2: расширенный поиск. Переключатели для выбора варианта поиска<br>
Input 3: поиск по параметрам из выпадающего списка (multi-select)<br>
Параметр расширенного поиска может быть смешан с шаблонами (2 & 3).<br>
При liveSearch кнопка поиска не отображается.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplInput=`@FILE:assets/snippets/ajaxSearch/templates/inputTemplates/input2.tpl.html`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="119"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse119"><span class="text-bold">&tplGrpResult</span> - шаблон результатов поиска для груп, без Ajax</a></h4>
</div>
<div id="collapse119" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ grpResult.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplGrpResult=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="120"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse120"><span class="text-bold">&tplResults</span> - шаблон результатов поиска, без Ajax</a></h4>
</div>
<div id="collapse120" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ results.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplResults=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="121"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse121"><span class="text-bold">&tplResult</span> - шаблон для каждого результата поиска, без Ajax</a></h4>
</div>
<div id="collapse121" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ result.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplResult=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="122"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse122"><span class="text-bold">&tplComment</span> - шаблон формы комментариев</a></h4>
</div>
<div id="collapse122" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ comment.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplComment=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="123"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse123"><span class="text-bold">&tplPaging0</span> - шаблон для pagingType=`0`</a></h4>
</div>
<div id="collapse123" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ Paging0.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaging0=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="124"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse124"><span class="text-bold">&tplPaging1</span> - шаблон для pagingType=`1`</a></h4>
</div>
<div id="collapse124" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ Paging1.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaging1=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="125"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse125"><span class="text-bold">&tplAjaxGrpResult</span> - шаблон результатов поиска для груп, с Ajax</a></h4>
</div>
<div id="collapse125" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> templates/ ajaxGrpResult.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplAjaxGrpResult=`assets/snippets/ajaxSearch/templates /myAjaxGrpResult.tpl.html`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="126"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse126"><span class="text-bold">&tplAjaxResults</span> - шаблон результатов поиска, с Ajax</a></h4>
</div>
<div id="collapse126" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> templates/ ajaxResults.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplAjaxResults=`@FILE:assets/snippets/ajaxSearch/templates /myAjaxResults.tpl.html`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="127"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse127"><span class="text-bold">&tplAjaxResult</span> - шаблон для каждого результата поиска, с Ajax</a></h4>
</div>
<div id="collapse127" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> templates/ ajaxResult.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplAjaxResult=`@FILE:assets/snippets/ajaxSearch/templates /myAjaxResult.tpl.html`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="129"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion4" href="#collapse129"><span class="text-bold">&tplPaging2</span> - шаблон для pagingType=`2`</a></h4>
</div>
<div id="collapse129" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка | @FILE<br>
<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/ajaxSearch/templates/ Paging2.tpl.html<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tplPaging2=``</pre>
</div>
</div>
</div>
</div>