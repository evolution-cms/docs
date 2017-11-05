
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ListIndexer: Пагинация</h2>

<div class="panel-group accordion">
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="702"></a><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse702"><span class="text-bold">&LIn_fQty</span> - Количество ссылок на страницу при включенной пагинации</a></h4>
		</div>
		<div id="collapse702" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 10<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&LIn_fQty=`20`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="703"></a><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse703"><span class="text-bold">&LIn_pageSeparator</span> - Разделитель номеров страниц</a></h4>
		</div>
		<div id="collapse703" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> строка<br>
				<span class="text-bold">Значение по умолчанию:</span> |<br>
				<span class="text-bold">Примечание:</span> Данный параметр настраивается только в коде сниппета в переменной $pageSeparator.
				<br>Чтобы появилась возможность задавать разделитель номеров страниц при вызове сниппета, необходимо в код сниппета в блоке с конфигурацией добавить следующую строку: <br>$pageSeparator = (isset($LIn_pageSeparator))? $LIn_pageSeparator : $pageSeparator ;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&LIn_pageSeparator=`||`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="704"></a><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse704"><span class="text-bold">&LIn_pgPosition</span> - Положение списка пагинации</a></h4>
		</div>
		<div id="collapse704" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | bottom | both<br>
				<span class="text-bold">Значение по умолчанию:</span> both<br>
				<span class="text-bold">Примечание:</span> <br>top - сверху
				<br>bottom - снизу
				<br>both - и сверху и снизу
				<br>Данный параметр настраивается только в коде сниппета в переменной $pgPosition.
				<br>Чтобы появилась возможность задавать положение пагинации при вызове сниппета, необходимо в код сниппета в блоке с конфигурацией добавить следующую строку: <br>$pgPosition = (isset($LIn_pgPosition))? $LIn_pgPosition : $pgPosition ;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&LIn_pgPosition=`bottom`</pre>
			</div>
		</div>
	</div>
</div>