
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Ditto: Параметри request </h3> 
Завдяки екстендеру request, сніпет Ditto обробляє значення і виводить результат відповідно до переданих параметрів.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="524"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse524"><span class="text-bold">&stripTags</span> - Видалення HTML-тегів з наданих параметрів</a></h4>
</div>
<div id="collapse524" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&stripTags=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="525"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse525"><span class="text-bold">&bad</span> - Параметри, які не можуть бути встановлені через екстендер</a></h4>
</div>
<div id="collapse525" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Параметри Ditto через кому<br>
<span class="text-bold">Значення за замовчуванням:</span> seeThroughtUnpub, showInMenuOnly, showPublishedOnly, debug, start, config, extenders, dittoID<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&bad=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="526"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse526"><span class="text-bold">&good</span> - Параметри, які можуть бути встановлені за допомогою екстендера</a></h4>
</div>
<div id="collapse526" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Параметри Ditto через кому<br>
<span class="text-bold">Значення за замовчуванням:</span> Всі параметри, які не ввійшли в список bad<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&good=``</pre>
</div>
</div>
</div>
</div>
