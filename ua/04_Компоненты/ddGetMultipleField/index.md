
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>ddGetMultipleField Сніпет для виведення даних </h3> 
Сніпет для виведення даних, розділених через певні роздільники. Зручно використовувати для виведення значень полів документів.	
<br>
<p>Сніпет для виведення даних, розділених через певні роздільники. Зручно використовувати для виведення значень полів документів, сформованих віджетом <a href="128.html">mm_ddMultipleFields</a>.</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/DivanDesign/MODXEvo.snippet.ddGetMultipleField" rel="nofollow" target="_blank">DivanDesign</a></p>

<h3 class="sub-header">Можливості:</h3>
<ul>
	<li>Отримання необхідного поля документа (і TV) по id. Параметри «inputString_docField» і «inputString_docId».</li>
	<li>Виведення необхідної кількості значень за номерами рядків і і значенням. Параметри «startRow», «totalRows» і «filter».</li>
	<li>Виведення необхідних значень за номерами колонок. Параметр «columns».</li>
	<li>Сортування рядків за значеннями колонок перед виведенням ('ASC', 'DESC', 'RAND', 'REVERSE'), в тому числі множинне сортування. Параметри «sortDir» і «sortBy».</li>
	<li>Виведення значень через роздільники рядків і колонок. Параметри «rowGlue» і «colGlue».</li>
	<li>Видалення порожніх значень колонок і рядків перед виведенням. Параметри «removeEmptyRows» і «removeEmptyCols».</li>
	<li>Типографіровання значень перед виведенням (використовується сніппет <a href="ddtypograph/index.html">ddTypograph</a>). Параметр «typography».</li>
	<li><span style="word-spacing:nowrap;">URL-кодування</span> результату перед виведенням. Параметр «urlencode».</li>
	<li>Виведення результату в JSON. Параметр «outputFormat».</li>
	<li>Виведення значень за шаблонами (чанками) рядків і колонок (в шаблоні рядків також доступний плейсхолдер <span>[</span>+rowNumber+] з номером рядка). Параметри «rowTpl» і «colTpl».</li>
	<li>Виведення результату виконання в чанк «outerTpl» з передачею додаткових даних через параметр «placeholders».</li>
</ul>

<h2 class="page-header">Документація</h2>
<p>З пари параметрів «inputString» / «inputString_docField» необхідно передавати лише один.</p>
<h3 class="sub-header">Опис параметрів</h3>
<table class="table table-bordered table-vcenter flip-content">
	<thead class="flip-content bordered-palegreen">
		<tr>
			<th>Назва</th>
			<th>Опис</th>
			<th>Допустимі значення</th>
			<th>Значення за замовчуванням</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td class="em">inputString<span class="help" title="Обов'язковий параметр">*</span></td>
			<td colspan="1">Вихідний рядок, що містить значення з роздільниками.</td>
			<td>{separated string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>inputString_docField</td>
			<td colspan="1">Ім'я поля документа / TV, що містить значення. У цьому випадку параметр «inputString» ігнорується, значення виходить з поля документа..</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>inputString_docId</td>
			<td colspan="1">ID документа, значення поля яке потрібно отримати. Якщо id не заданий, береться id поточного документа.</td>
			<td>{integer}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>rowDelimiter</td>
			<td colspan="1">Роздільник між рядками в вихідній стрічці.</td>
			<td>{string; regexp}</td>
			<td>'||'</td>
		</tr>
		<tr>
			<td>colDelimiter</td>
			<td colspan="1">Роздільник між колонками в вихідній стрічці.</td>
			<td>{string; regexp}</td>
			<td>'::'</td>
		</tr>
		<tr>
			<td>startRow</td>
			<td colspan="1">Номер рядка, починаючи з якого необхідно повертати (рядки нумеруються з 0).</td>
			<td>{integer}</td>
			<td>0</td>
		</tr>
		<tr>
			<td>totalRows</td>
			<td colspan="1">Кількість повертаючих рядків. При значенні == 'all' будуть повернуті всі наявні рядки.</td>
			<td>{integer; 'all'}</td>
			<td>'all'</td>
		</tr>
		<tr>
			<td>columns</td>
			<td colspan="1">Номера колонок через кому, які потрібно повернути (колонки нумеруються з 0). При значенні == 'all' будуть повернуті всі колонки.</td>
			<td>{comma separated string; 'all'}</td>
			<td>'all'</td>
		</tr>
		<tr>
			<td>filter</td>
			<td colspan="1">Фільтр за значеннями колонок. Наприклад, при '0 :: a || 0 :: b || 1 :: 1' виведуться тільки рядки, в яких значення колонки 0 дорівнює 'a' або 'b' і значення колонки 1 дорівнює '1'.</td>
			<td>{separated string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>removeEmptyRows</td>
			<td colspan="1">Видаляти порожні рядки</td>
			<td>{0; 1}</td>
			<td>1</td>
		</tr>
		<tr>
			<td>removeEmptyCols</td>
			<td colspan="1">Видаляти порожні колонки</td>
			<td>{0; 1}</td>
			<td>1</td>
		</tr>
		<tr>
			<td>sortBy</td>
			<td colspan="1">Номер колонки (нумерується з нуля), по якій необхідно сортувати. Для множинного сортування параметри вказуються через кому (наприклад: '0,1')..</td>
			<td>{comma separated string}</td>
			<td>0</td>
		</tr>
		<tr>
			<td>sortDir</td>
			<td colspan="1">Напрямок сортування рядків. При значенні == 'REVERSE' рядки будуть повернуті в зворотньому порядку.</td>
			<td>{'ASC'; 'DESC'; 'RAND'; 'REVERSE'; ''}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>typography</td>
			<td colspan="1">Номери колонок через кому, значення яких потрібно типографірувати (колонки нумеруються з 0). Якщо не задано, нічого не типографується.</td>
			<td>{comma separated string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>outputFormat</td>
			<td colspan="1">Формат, в якому повертається результат.</td>
			<td>{'html'; 'JSON'; 'array'; 'htmlarray'}</td>
			<td>'html'</td>
		</tr>
		<tr>
			<td>rowGlue</td>
			<td colspan="1">Роздільник (об'єднувач) між рядками при виведенні. Може використовуватися спільно з шаблоном «rowTpl».</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>colGlue</td>
			<td colspan="1">Роздільник (об'єднувач) між колонками при виведенні. Може використовуватися спільно з шаблоном «colTpl» (але не «rowTpl», зі зрозумілих причин).</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>rowTpl</td>
			<td colspan="1">Шаблон для виведення рядків (параметр «outputFormat» повинен бути == 'html').
				<p>Доступні плейсхолдери:</p>
				<ul>
					<li>[+rowNumber+] – номер рядка, що починається з 1;</li>
					<li>[+rowNumber.zeroBased+] – номер рядка, що починається з 0;</li>
					<li>[+total+] – загальна кількість рядків;</li>
					<li>[+resultTotal+] – кількість повертаючих рядків;</li>
					<li>[+col0+], [+col1+], … – значення відповідних колонок.</li>
				</ul>
				<p>Передавати код безпосередньо без чанка можна починаючи значення з «@CODE:».</p></td>
			<td>{string: chunkName|string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>colTpl</td>
			<td colspan="1">Список шаблонів для виведення колонок, через кому (параметр «outputFormat» повинен бути == 'html'). Якщо шаблонів менше, ніж колонок, для всіх відсутніх виставляється останній вказаний шаблон. Значення 'null' - без шаблону.
				<p>Доступні плейсхолдери:</p>
				<ul>
					<li>[+val+] – значення;</li>
					<li>[+rowNumber+] – номер рядка, що починається з 1;</li>
					<li>[+rowNumber.zeroBased+] – номер рядка, що починається з 0.</li>
				</ul>
				<p>Передавати код безпосередньо без чанка можна починаючи значення з «@CODE:».</p></td>
			<td>{comma separated string: chunkName|string; 'null'}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>outerTpl</td>
			<td colspan="1">Шаблон зовнішньої обгортки (при «outputFormat» != 'array').
				<p>Доступні плейсхолдери:</p>
				<ul>
					<li>[+result+] – результат сніппета;</li>
					<li>[+total+] – загальна кількість рядків;</li>
					<li>[+resultTotal+] – кількість повертаючих рядків;</li>
					<li>[+rowY.colX+] – значення (де «Y» - номер рядка, «X» - номер колонки).</li>
				</ul>
				<p>Передавати код безпосередньо без чанка можна починаючи значення з «@CODE:».</p></td>
			<td>{string: chunkName|string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>placeholders</td>
			<td colspan="1">Додаткові дані у вигляді <a href="https://en.wikipedia.org/wiki/Query_string" target="_blank">query string</a> які будуть передані в шаблони «outerTpl», «rowTpl» і «colTpl». Наприклад, «pladeholder1=value1&pagetitle=My awesome pagetitle!».</td>
			<td>{query string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>urlencode</td>
			<td colspan="1">Треба URL-кодувати результуючий рядок (при «outputFormat»! = 'Array')? Рядок кодується згідно RFC 3986.</td>
			<td>{0; 1}</td>
			<td>0</td>
		</tr>
		<tr>
			<td>totalRowsToPlaceholder</td>
			<td colspan="1">Ім'я зовнішнього плейсхолдера, в який потрібно вивести загальну кількість рядків. Якщо параметр не заданий - не виводиться.</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
		<tr>
			<td>resultToPlaceholder</td>
			<td colspan="1">Ім'я зовнішнього плейсхолдера, в який потрібно зберегти результат роботи сніпета замість звичайного виведення. Якщо параметр не заданий - сніпет просто повертає реузльтат.</td>
			<td>{string}</td>
			<td>–</td>
		</tr>
	</tbody>
</table>

<h3 class="sub-header">Приклади</h3>
<h4>Виведення зображень з описами</h4>
<p>Вихідний рядок (нехай перебуває в TV документа «images»):</p>
<pre class="brush: html;">
assets/images/some_img1.jpg::Изображение 1||assets/images/some_img2.jpg::Зображення 2</pre>
<p>Виклик сніпета в шаблоні документа:</p>
<pre class="brush: html;">
[[ddGetMultipleField?
&inputString=``
&rowTpl=`images_item`
]]
</pre>
<p>Код чанка «images_item»:</p>
<pre class="brush: html;">
[+col1+]:
&lt;img src="[+col0+]" alt="[+col1+]" /&gt;
</pre>

<h4>Отримання і виведення даних з поля (TV) «prices» документа з id = 25 в вигляді таблиці, якщо щось є і нічого, якщо немає</h4>
<p>Вихідне значення поля:</p>
<pre class="brush: html;">Яблука смачні::100::кг||Цвяхи звичайні::5 000::центнер||Коти::865::шт</pre>

<p>Виклик сніпета (де завгодно):</p>
<pre class="brush: html;">
[[ddGetMultipleField?
&amp;inputString_docField=`prices`
&amp;inputString_docId=`25`
&amp;outerTpl=`prices`
&amp;rowTpl=`prices_item`
]]</pre>

<p>Код чанка «prices_item»:</p>
<pre class="brush: html;">
&lt;tr&gt;
	&lt;td&gt;[+rowNumber+]&lt;/td&gt;
	&lt;td&gt;[+col0+]&lt;/td&gt;
	&lt;td&gt;[+col1+] руб./[+col2+]&lt;/td&gt;
&lt;/tr&gt;</pre>

<p>Код чанка «prices»:</p>
<pre class="brush: html;">
&lt;h1&gt;Табличка цін&lt;/h1&gt;
&lt;table&gt;
	[+result+]
&lt;/table&gt;
</pre>

<h4>Виведення тегів документа через кому з використанням регулярного виразу в «rowDelimiter»</h4>
<p>Нехай теги документа у нас зберігаються в TV «tags» і до цієї TV у нас застосований віджет <a href="130.html">mm_widget_tags</a>. Користувач заповнює теги через кому, при цьому, може заповнюватися як з пробілами по краях, так і без них.</p>
<p>Значення TV «tags»:</p>
<pre class="brush: html;">
Коти, Кішки, Собаки, Ведмеді, Слони</pre>
<p>Виклик сніпета в шаблоні документа:</p>
<pre class="brush: html;">
[[ddGetMultipleField?
&inputString=`Manager, General`
&rowDelimiter=`/\s*,\s*/`
&rowGlue=`, `
&rowTpl=`tags_row`
]]
</pre>
<p>Код чанка «tags_row»:</p>
<pre class="brush: html;">
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=[+col0+]"&gt;[+col0+]&lt;/a&gt;</pre>

<p>Результат:</p>
<pre class="brush: html;">
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Коти"&gt;Коти&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Кішки"&gt;Кішки&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Собаки"&gt;Собаки&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Ведмеді"&gt;Ведмеді&lt;/a&gt;,
&lt;a href="dlbuildmenu/kratkoe-opisanie?tags=Слони"&gt;Слони&lt;/a&gt;
</pre>

<h4>Передача додаткових даних через параметр «placeholders»</h4>
<pre class="brush: html;">
[[ddGetMultipleField?
&inputString=`Сірий::8 кг::любить м'ясо || Рудий :: 6 кг :: вегетаріанець`
&outerTpl=`cats`
&rowTpl=`cats_item`
&colTpl=`cats_item_color,null,null`
&placeholders=`kind=коти`
&price=`не продається.`
&colorTitle=`Шерсть густа, хороша`
]]
</pre>
<p>Код чанка «cats» (замість «[+ kind]» підставляється «коти»):</p>
<pre class="brush: html;">&lt;h1&gt;Наші улюблені [+kind+], [+resultTotal+] штук.&lt;/h1&gt;[+result+]</pre>
<p>Код чанка «cats_item» (замість «[+price+]» підставиться «не продається.»):</p>
<pre class="brush: html;">[+rowNumber+]. [+col0+], важить [+col1+], [+col2+] – &lt;i&gt;[+price+]&lt;/i&gt;&lt;br /&gt;</pre>
<p>Код чанка «cats_item_color» (замість «[+colorTitle+]» підставиться «Шерсть густа, хороша»):</p>
<pre class="brush: html;">&lt;span title="[+colorTitle+]"&gt;[+val+]&lt;/span&gt;</pre>
<p><i>Прикладів тут можна напридумувати безліч.</i></p>
