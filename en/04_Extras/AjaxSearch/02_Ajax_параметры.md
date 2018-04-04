
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>AjaxSearch: Ajax параметры </h3> 
Ajax параметры сниппета AjaxSearch.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="105"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse105"><span class="text-bold">&liveSearch</span> - (Ajax параметр) - включение автоматического поиска</a></h4>
</div>
<div id="collapse105" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>Есть два режима работы формы ajaxSearch:<br>
0 - форма и кнопка отображаются и поиск не начинается до нажатия кнопки пользователем.<br>
1 - поиск запускается автоматически, как только пользователь вводит поисковый запрос<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&liveSearch=`1`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="106"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse106"><span class="text-bold">&ajaxMax</span> - (Ajax параметр) - количество отображаемых результатов без перезагрузки страницы для поиска с Ajax (&ajaxSearch=`1`).</a></h4>
</div>
<div id="collapse106" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 6<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&ajaxMax=`10`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="107"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse107"><span class="text-bold">&showMoreResults</span> - (Ajax параметр) - показать ссылку на все результаты через Ajax</a></h4>
</div>
<div id="collapse107" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&showMoreResults=`1`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="108"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse108"><span class="text-bold">&moreResultsPage</span> - (Ajax параметр) - ID страницы на которой будет вывод всех результатов поиска в режиме с Ajax </a></h4>
</div>
<div id="collapse108" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ID документа<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> эта страница должна содержать другой вызов сниппета для того, чтобы показать результаты<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&moreResultsPage=`12`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="109"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse109"><span class="text-bold">&opacity</span> - (Ajax параметр) - прозрачность выводимого результата</a></h4>
</div>
<div id="collapse109" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 < число < 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&opacity=`0.9`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="110"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse110"><span class="text-bold">&jscript</span> - (Ajax параметр) - выбор между Mootools или jQuery.</a></h4>
</div>
<div id="collapse110" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> jquery | mootools2 | mootools<br>
<span class="text-bold">Значение по умолчанию:</span> mootools<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&jscript=`mootools2`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="111"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse111"><span class="text-bold">&addJscript</span> - (Ajax параметр) - добавить mootools библиотеку к заголовку веб-страницы автоматически</a></h4>
</div>
<div id="collapse111" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&addJscript=`0`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="112"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse112"><span class="text-bold">&jsMooTools</span> - (Ajax параметр) - расположение MooTools JavaScript библиотеки</a></h4>
</div>
<div id="collapse112" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Путь к библиотеке MooTools<br>
<span class="text-bold">Значение по умолчанию:</span> manager/media/script/mootools/mootools.js<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&jsMooTools=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="113"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse113"><span class="text-bold">&jsMooTools2</span> - (Ajax параметр) - расположение MooTools2 JavaScript библиотеки</a></h4>
</div>
<div id="collapse113" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Путь к библиотеке MooTools2<br>
<span class="text-bold">Значение по умолчанию:</span> js/mootools2/mootools1.2.js<br>
<span class="text-bold">Примечание:</span> mootools2 - альтернатива mootools библиотеке.
Mootools1.2.4 уже установлена<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&jsMooTools2=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="114"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse114"><span class="text-bold">&jsJquery</span> - (Ajax параметр) - расположение Jquery JavaScript библиотеки</a></h4>
</div>
<div id="collapse114" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Путь к библиотеке Jquery<br>
<span class="text-bold">Значение по умолчанию:</span> js/jQuery/jquery.js<br>
<span class="text-bold">Примечание:</span> совместимость с Jquery 1.4.2 библиотекой<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&jsJquery=``</pre>
</div>
</div>
</div>
</div>