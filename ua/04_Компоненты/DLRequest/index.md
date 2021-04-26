
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>DLRequest - запуск сніпетів з параметрами з get/post </h3>
DLRequest - запуск сніпетів з параметрами з get/post
<p>Сніппет розроблений для заміни Ditto з екстендером request на прохання <a href="http://modx.im/profile/Extremum/" rel="nofollow" target="_blank">Extremum</a> і на його ж кошти, за що велике спасибі.</p>
<p>Сніппет приймає значення з post або get-масиву і використовує їх в якості параметрів для запуску іншого сниппета. Спочатку планувалася робота тільки з DocLister (звідси і назва), але в підсумку можна викликати будь-сниппет. Проте, наявність встановленого DocLister'а обов'язково.</p>
<p>DLRequest вміє не тільки передавати параметри, але і будувати форму для управління цими самими параметрами, без милиць типу:</p>
<pre class="brush: php;">
&lt;?php
//[!selected? &field=`ditto_id1_sortDir` &value=`DESC`!]
if ($_REQUEST[$field] == $value) {
	echo "selected"; 
}
</pre>
<p>Важливий момент - можливі значення параметрів задаються розробником, тобто якщо в формі для вибору кількості документів на сторінці зазначено «10, 20, 50, 100», то підставити руками url?display=100500 не вийде - такий параметр буде просто проігноровано.</p>
<p>Передбачена також можливість зберігати значення параметрів, які передаються з браузера для інших фрагментів, наприклад, для DocLister це буде параметр page. Тобто якщо в списку документів ви перебуваєте на сторінці 5, то після зміни, наприклад, напряму сортування, все одно залишитеся на сторінці 5.</p>
<p>Тепер приведу приклад виклику, з якого зрозуміло, як це все працює:</p>
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
<p class="text-warning"><em>Після &amp; прогалини стоять, бо інакше редактор підміняє символи.</em></p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/DLRequest" rel="nofollow" target="_blank">Pathologic</a></p>
