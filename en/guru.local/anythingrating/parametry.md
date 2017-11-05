
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>AnythingRating: Параметры</h2>

<div class="panel-group accordion">
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="708"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse708"><span class="text-bold">&define</span> - Определить рейтинг группы</a></h4>
		</div>
		<div id="collapse708" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&define=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="709"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse709"><span class="text-bold">&getTopRated</span> - Вывести результаты голосования</a></h4>
		</div>
		<div id="collapse709" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&getTopRated=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="710"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse710"><span class="text-bold">&language</span> - Устанавливает язык AnythingRating</a></h4>
		</div>
		<div id="collapse710" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Имя языкового файла<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> Языковые пакеты реализованы не полностью, вы можете добавить собственный языковой файл.<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&language=`russian-utf8`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="711"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse711"><span class="text-bold">&nbStars</span> - Количество звезд</a></h4>
		</div>
		<div id="collapse711" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 5<br>
				<span class="text-bold">Примечание:</span> AnythingRating.css должен соответствовать этому количеству<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&nbStars=`3`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="712"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse712"><span class="text-bold">&nbIP</span> - Количество хранящихся IP-адресов</a></h4>
		</div>
		<div id="collapse712" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> all<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&nbIP=`50`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="713"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse713"><span class="text-bold">&endDate</span> - Дата окончания голосования</a></h4>
		</div>
		<div id="collapse713" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> YYYY-MM-DD | неограничено<br>
				<span class="text-bold">Значение по умолчанию:</span> неограничено<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&endDate=`2012-12-12`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="714"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse714"><span class="text-bold">&canVote</span> - Список веб-групп пользователей с правами голоса, разделенный запятыми</a></h4>
		</div>
		<div id="collapse714" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> список веб-групп пользователей через запятую<br>
				<span class="text-bold">Значение по умолчанию:</span> голосование доступно для всех<br>
				<span class="text-bold">Примечание:</span> Для голосования веб-пользователю необходимо авторизоваться<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&canVote=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="715"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse715"><span class="text-bold">&multiVote</span> - Разрешить пользователям голосовать несколько раз</a></h4>
		</div>
		<div id="collapse715" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> 0 - допускается только один голос<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&multiVote=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="716"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse716"><span class="text-bold">&atrCss</span> - Путь к файлу CSS</a></h4>
		</div>
		<div id="collapse716" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets/anythingRating/css/anythingRating.css <br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&atrCss=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="717"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse717"><span class="text-bold">&atrTpl</span> - Имя файла с шаблоном для формы голосования</a></h4>
		</div>
		<div id="collapse717" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> <br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/anythingRating/templates/anythingRating.tpl.html<br>
				<span class="text-bold">Примечание:</span> @FILE:путь к файлу<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&atrTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="718"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse718"><span class="text-bold">&atrId</span> - Уникальный идентификатор</a></h4>
		</div>
		<div id="collapse718" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Любая комбинация символов AZ, подчеркивания и цифр 0-9<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&atrId=`ar1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="719"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse719"><span class="text-bold">&noVotes</span> - Запретить/ разрешить голосование</a></h4>
		</div>
		<div id="collapse719" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&noVotes=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="720"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse720"><span class="text-bold">&init</span> - Initialize the vote with a rating value or from content of a template Variable.</a></h4>
		</div>
		<div id="collapse720" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> A numeric value &gt;=1 and &lt;= &nbStars | A data formatted as follow TVname[:DocId] <br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> The content of the TV should contain a rating_value or "rating_value:nb_votes" <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&init=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="721"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse721"><span class="text-bold">&topNb</span> - Количество отображаемых пунктов в результатах голосования</a></h4>
		</div>
		<div id="collapse721" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 5<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topNb=`10`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="722"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse722"><span class="text-bold">&topDir</span> - Показать лучшие или худшие результаты</a></h4>
		</div>
		<div id="collapse722" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> best | worst<br>
				<span class="text-bold">Значение по умолчанию:</span> best<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topDir=`worst`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="723"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse723"><span class="text-bold">&topTpl</span> - Имя файла с шаблоном результатов голосования</a></h4>
		</div>
		<div id="collapse723" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets/anythingRating/templates/topRated.tpl.html <br>
				<span class="text-bold">Примечание:</span> @FILE:путь<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="724"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse724"><span class="text-bold">&topLabel</span> - Название блока с результатами рейтинга</a></h4>
		</div>
		<div id="collapse724" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> <br>
				<span class="text-bold">Значение по умолчанию:</span> <br>
				<span class="text-bold">Примечание:</span> Используются поля $_lang['atr_bestlabel'] или $_lang['atr_worstlabel'] из языкового файла<br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topLabel=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="725"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse725"><span class="text-bold">&topTable</span> - Имя таблицы в которой следует искать данные предметов рейтинга [ОБЯЗАТЕЛЬНО]</a></h4>
		</div>
		<div id="collapse725" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Любое существующее имя таблицы без префикса MODX<br>
				<span class="text-bold">Значение по умолчанию:</span> <br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topTable=`site_content`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="726"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse726"><span class="text-bold">&topIdField</span> - Имя поля для идентификатора в таблице результатов голосования [ОБЯЗАТЕЛЬНО]</a></h4>
		</div>
		<div id="collapse726" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> <br>
				<span class="text-bold">Значение по умолчанию:</span> id<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topIdField=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="727"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse727"><span class="text-bold">&topTitleField</span> - Имя поля для названия в таблице результатов голосования [ОБЯЗАТЕЛЬНО]</a></h4>
		</div>
		<div id="collapse727" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> <br>
				<span class="text-bold">Значение по умолчанию:</span> title<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topTitleField=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="728"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse728"><span class="text-bold">&topDescrField</span> - Поле для описания в таблице результатов голосования [ОБЯЗАТЕЛЬНО]</a></h4>
		</div>
		<div id="collapse728" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> имя поля<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topDescrField=`description`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="729"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse729"><span class="text-bold">&topImageField</span> - Имя поля изображения в таблице результатов голосования</a></h4>
		</div>
		<div id="collapse729" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> имя поля<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topImageField=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="730"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse730"><span class="text-bold">&topLinkField</span> - Имя поля для ссылки в результатах рейтинга</a></h4>
		</div>
		<div id="collapse730" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> имя поля<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<p><span class="text-bold">Пример:</span></p>
				<pre class="brush: html;">&topLinkField=`alias`</pre>
			</div>
		</div>
	</div>
</div>