
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>AjaxSearch: Ajax параметри </h3> 
Ajax параметри сніпета AjaxSearch.	
<br>
<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="105"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse105"><span class="text-bold">&liveSearch</span> - (Ajax параметр) - увімкнення автоматичного пошуку</a></h4>
</div>
<div id="collapse105" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 0<br>
<span class="text-bold">Примітка:</span> <br>Є два режима роботи форми ajaxSearch:<br>
0 - форма і кнопка відображаються та пошук не починається до натискання кнопки користувачем.<br>
1 - пошук  запускається автоматично, як тільки користувач вводить пошуковий запит<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&liveSearch=`1`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="106"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse106"><span class="text-bold">&ajaxMax</span> - (Ajax параметр) - кількість відображених результатів без перезавантаження сторінки для пошуку з Ajax (&ajaxSearch=`1`).</a></h4>
</div>
<div id="collapse106" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значення за замовчуванням:</span> 6<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&ajaxMax=`10`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="107"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse107"><span class="text-bold">&showMoreResults</span> - (Ajax параметр) - показати посилання на всі результати через Ajax</a></h4>
</div>
<div id="collapse107" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 0<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&showMoreResults=`1`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="108"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse108"><span class="text-bold">&moreResultsPage</span> - (Ajax параметр) - ID сторінки на якій буде вивід всіх результатів пошуку у режимі з Ajax </a></h4>
</div>
<div id="collapse108" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ID документа<br>
<span class="text-bold">Значення за замовчуванням:</span> 0<br>
<span class="text-bold">Примітка:</span> Дана сторінка повинна містити інший виклик сніпета для того , щоб показати результати<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&moreResultsPage=`12`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="109"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse109"><span class="text-bold">&opacity</span> - (Ajax параметр) - прозорість виведеного результата</a></h4>
</div>
<div id="collapse109" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 < число < 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&opacity=`0.9`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="110"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse110"><span class="text-bold">&jscript</span> - (Ajax параметр) - вибір між Mootools або jQuery.</a></h4>
</div>
<div id="collapse110" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> jquery | mootools2 | mootools<br>
<span class="text-bold">Значення за замовчуванням:</span> mootools<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&jscript=`mootools2`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="111"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse111"><span class="text-bold">&addJscript</span> - (Ajax параметр) - добавити mootools бібліотеку до заголовку веб-сторінки автоматично</a></h4>
</div>
<div id="collapse111" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значення за замовчуванням:</span> 1<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&addJscript=`0`</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="112"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse112"><span class="text-bold">&jsMooTools</span> - (Ajax параметр) - розташування MooTools JavaScript бібліотеки</a></h4>
</div>
<div id="collapse112" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Шлях до бібліотеки MooTools<br>
<span class="text-bold">Значення за замовчуванням:</span> manager/media/script/mootools/mootools.js<br>
<span class="text-bold">Примітка:</span> <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&jsMooTools=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="113"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse113"><span class="text-bold">&jsMooTools2</span> - (Ajax параметр) -розташування MooTools2 JavaScript бібліотеки</a></h4>
</div>
<div id="collapse113" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Шлях до бібліотеки MooTools2<br>
<span class="text-bold">Значення за замовчуванням:</span> js/mootools2/mootools1.2.js<br>
<span class="text-bold">Примітка:</span> mootools2 - альтернатива mootools бібліотеці.
Mootools1.2.4 вже встановлена <br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&jsMooTools2=``</pre>
</div>
</div>
</div>
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="114"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion2" href="#collapse114"><span class="text-bold">&jsJquery</span> - (Ajax параметр) - розташування Jquery JavaScript бібліотеки</a></h4>
</div>
<div id="collapse114" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span>Шлях до бібліотеки Jquery<br>
<span class="text-bold">Значення за замовчуванням:</span> js/jQuery/jquery.js<br>
<span class="text-bold">Примітка:</span> суміснусть з Jquery 1.4.2 бібліотекою<br>
<p><span class="text-bold">Приклад:</span></p>
<pre class="brush: html;">&jsJquery=``</pre>
</div>
</div>
</div>
</div>
