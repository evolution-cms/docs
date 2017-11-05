
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLRequest</h2>

<p>Сниппет разработан для замены Ditto с экстендером request по просьбе <a href="http://modx.im/profile/Extremum/" rel="nofollow" target="_blank">Extremum</a> и на его же средства, за что большое спасибо.</p>
<p>Сниппет принимает значения из post или get-массива и использует их в качестве параметров для запуска другого сниппета. Изначально планировалась работа только с DocLister (отсюда и название), но в итоге можно вызывать любой сниппет. Тем не менее, наличие установленного DocLister'а обязательно.</p>
<p>DLRequest умеет не только передавать параметры, но и строить форму для управления этими самыми параметрами, без костылей типа:</p>
<pre class="brush: php;">
&lt;?php
//[!selected? &field=`ditto_id1_sortDir` &value=`DESC`!]
if ($_REQUEST[$field] == $value) {
	echo "selected"; 
}
</pre>
<p>Важный момент – возможные значения параметров задаются разработчиком, то есть если в форме для выбора количества документов на странице указано «10, 20, 50, 100», то подставить руками url?display=100500 не получится – такой параметр будет просто проигнорирован.</p>
<p>Предусмотрена также возможность сохранять значения параметров, которые передаются из браузера для других сниппетов, например, для DocLister это будет параметр page. То есть если в списке документов вы находитесь на странице 5, то после смены, например, направления сортировки, все равно останетесь на странице 5.</p>
<p>Теперь приведу пример вызова, из которого понятно, как это все работает:</p>
<pre class="brush: html;">
[+paramsForm+]
&lt;div&gt;
	[!DLRequest? 
	&runSnippet=`DocLister` 
	&parents=`2` 
	&tpl=`@CODE:<p>[+id+]. [+pagetitle+]</p>` 
	&paginate=`pages` 
	&display=`0` 
	&rqParams=`{
		"sortBy":{
			"id":"По id",
			"pagetitle":"По pagetitle"
		},
		"sortDir":{
			"asc":"По возрастанию",
			"desc":"По убыванию"
		},
		"display":{
			"1":"1 документ",
			"3":"3 документа",
			"5":"5 документов"
		}
	}`
	&rqParamsNames=`{
		"sortBy":"Сортировать по",
		"sortDir":"Порядок",
		"display":"Результатов на странице"
	}`
	&selectedClassName=`selected`
	& paramsForm=`paramsForm`
	&keepParams=`page`
	& paramsOwnerTPL=`@CODE:
		<form method="get" action="%5B~%5B*id*%5D~%5D.html">
			[+keepParams+]
			[+params+]
			<button type="submit">Отправить</button>
		</form>
	`
	& param.ownerTPL=`@CODE:
		<label>[+description+]</label>
		<select name="[+paramName+]">
			[+values+]
		</select>
	`
	& param.tpl=`@CODE:
		<option value="[+value+]" [+selectedClass+]>
			[+description+]
		</option>
	`
	&sortBy.tpl=`@CODE:
		<option value="[+value+]" [+selectedClass+]>
			[+description+] dfdfdfh
		</option>
	`
	&display.ownerTPL=`@CODE:
		<label style="color:red;">[+description+]</label>
		<select name="[+paramName+]">
			[+values+]
		</select>
	`
	&keepTpl=`@CODE:
		<input name="[+paramName+]" value="[+value+]" type="hidden">
	`
	!]
&lt;/div&gt;
[+pages+]
</pre>
<p class="text-warning"><em>После &amp; пробелы стоят, потому что иначе редактор подменяет символы.</em></p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/DLRequest" rel="nofollow" target="_blank">Pathologic</a></p>