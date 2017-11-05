
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ManagerManager: Дополнительно</h2>

<h3 class="sub-header text-bold">Модуль ddMMEditor</h3>
<p>Модуль для удобного редактирования файла конфигурации плагина ManagerManager.</p>
<p><span class="text-bold">Возможности:</span></p>
<ul>
	<li>визуальное создание правил для MM;</li>
	<li>применение правил к необходимым шаблонам и ролям в два клика;</li>
	<li>autocomplete со всеми именами полей и TV;</li>
	<li>объединение правил в группы по смыслу (группы можно называть произвольными именами);</li>
	<li>сворачивание-разворачивание групп для удобного просмотра в общем виде;</li>
	<li>drag'n'drop правил и групп между собой;</li>
	<li>возможность «ручной» вставки произвольного кода в начало и конец конфигурационного файла.</li>
</ul>
<p><span class="text-bold">Установка</span></p>
<p>Содержимое файла module.php должно быть скопировано в поле «Код модуля» в меню создания нового модуля. Остальные файлы должны находиться в assets/modules/ddmmeditor/... (в архиве уже создана нужная структура папок). Модуль изменяет файл assets/plugins/managermanager/mm_rules.inc.php плагина ManagerManager.</p>
<p class="alert alert-warning"><span class="text-bold">Внимание!</span> Чтобы ManagerManager использовал правила, созданные модулем, параметр «Configuration Chunk» в конфигурации плагина (вкладка «Конфигурация») должен быть пустым.</p>
<h3 class="sub-header text-bold"><a id="1007"></a>Сниппет ddGetMultipleField</h3>
<p>Сниппет для вывода данных, разделённых через определённые разделители. Удобно использовать для вывода значений полей документов, сформированных виджетом <a target="_blank" href="managermanager/index.html#322">mm_ddMultipleFields</a>. Возможности:</p>
<ul>
	<li>Получение необходимого поля документа (и TV) по id. Параметры «docField» и «docId».</li>
	<li>Вывод необходимого количества значений по номерам строк и и значениям. Параметры «startRow», «totalRows» и «filter».</li>
	<li>Вывод необходимых значений по номерам колонок. Параметр «columns».</li>
	<li>Сортировка строк по значениям колонок перед выводом ('ASC', 'DESC', 'RAND', 'REVERSE'), в том числе множественная сортировка. Параметры «sortDir» и «sortBy».</li>
	<li>Вывод значений через разделители строк и колонок. Параметры «rowGlue» и «colGlue».</li>
	<li>Удаление пустых значений колонок и строк перед выводом. Параметры «removeEmptyRows» и «removeEmptyCols».</li>
	<li>Типографирование значений перед выводом (используется сниппет <a target="_blank" href="managermanager/index.html#1008">ddTypograph</a>). Параметр «typography».</li>
	<li>URL-кодирование результата перед выводом. Параметр «urlencode».</li>
	<li>Вывод результата в JSON. Параметр «outputFormat».</li>
	<li>Вывод значений по шаблонам (чанкам) строк и колонок (в шаблоне строк также доступен плэйсхолдер [+rowNumber+] с номером строки). Параметры «rowTpl» и «colTpl».</li>
	<li>Вывод результата выполнения в чанк «outerTpl» с передачей дополнительных данных через параметр «placeholders»</li>
</ul>
<p class="alert alert-warning"><span class="text-bold">Внимание!</span> Из пары параметров «string»/«docField» необходимо передавать лишь один.</p>
<div class="flip-scroll">
	<table class="table table-bordered table-vcenter flip-content">
		<thead class="flip-content bordered-palegreen">
			<tr><th>Название</th><th>Описание</th><th>Допустимые значения</th><th>Значение по умолчанию</th></tr>
		</thead>
		<tbody>
			<tr>
				<td class="em">string <span class="help">*<span class="helpPopup"></span></span></td>
				<td>Исходная строка, содержащая значение с разделителями.</td>
				<td>{separated string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>docField</td>
				<td>Имя поля документа / TV, содержащего значение. В этом случае параметр «string» игнорируется, значение получается из поля документа.</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>docId</td>
				<td>ID документа, значение поля которого нужно получить. Если id не задан, берётся id текущего документа.</td>
				<td>{integer}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>rowDelimiter</td>
				<td>Разделитель между строками в исходной строке.</td>
				<td>{string; regexp}</td>
				<td>'||'</td>
			</tr>
			<tr>
				<td>colDelimiter</td>
				<td>Разделитель между колонками в исходной строке.</td>
				<td>{string; regexp}</td>
				<td>'::'</td>
			</tr>
			<tr>
				<td>startRow</td>
				<td>Номер строки, начиная с которой необходимо возвращать (строки нумеруются с 0).</td>
				<td>{integer}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>totalRows</td>
				<td>Количество возвращаемых строк. При значении == 'all' будут возвращены все имеющиеся строки.</td>
				<td>{integer; 'all'}</td>
				<td>'all'</td>
			</tr>
			<tr>
				<td>columns</td>
				<td>Номера колонк через запятую, которые нужно вернуть (колонки нумеруются с 0). При значении == 'all' будут возвращены все колонки.</td>
				<td>{comma separated string; 'all'}</td>
				<td>'all'</td>
			</tr>
			<tr>
				<td>filter</td>
				<td>Фильтр по значениям колонок. Например, при '0::a||0::b||1::1' выведутся только строки, в которых значение колонки 0 равно 'a' или 'b' и значение колонки 1 равно '1'.</td>
				<td>{separated string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>removeEmptyRows</td>
				<td>Удалять пустые строки?</td>
				<td>{0; 1}</td>
				<td>1</td>
			</tr>
			<tr>
				<td>removeEmptyCols</td>
				<td>Удалять пустые колонки?</td>
				<td>{0; 1}</td>
				<td>1</td>
			</tr>
			<tr>
				<td>sortBy</td>
				<td>Номер колонки (нумеруются с ноля), по которой необходимо сортировать. Для множественной сортировки параметры указываются через запятую (например: '0,1').</td>
				<td>{comma separated string}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>sortDir</td>
				<td>Направление сортировки строк. При значении == 'REVERSE' строки будут возвращены в обратном порядке.</td>
				<td>{'ASC'; 'DESC'; 'RAND'; 'REVERSE'; ''}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>typography</td>
				<td>Номера колонок через запятую, значения которых нужно типографировать (колонки нумеруются с 0). Если не задано, ничего не типографируется.</td>
				<td>{comma separated string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>outputFormat</td>
				<td>Формат, в котором возвращать результат.</td>
				<td>{'html'; 'JSON'; 'array'; 'htmlarray'}</td>
				<td>'html'</td>
			</tr>
			<tr>
				<td>rowGlue</td>
				<td>Разделитель (объединитель) между строками при выводе. Может использоваться совместно с шаблоном «rowTpl».</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>colGlue</td>
				<td>Разделитель (объединитель) между колонками при выводе. Может использоваться совместно с шаблоном «colTpl» (но не «rowTpl», по понятным причинам).</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>rowTpl</td>
				<td>Шаблон для вывода строк (параметр «outputFormat» должен быть == 'html'). Доступные плэйсхолдеры: [+rowNumber+] (номер строки, начиная с 1), [+total+] (общее количество строк), [+resultTotal+] (количество возвращаемых строк), [+col0+], [+col1+], … (значения соответствующих колонок).</td>
				<td>{string: chunkName}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>colTpl</td>
				<td>Список шаблонов для вывода колонок, через запятую (параметр «outputFormat» должен быть == 'html'). Если шаблонов меньше, чем колонок, для всех недостающих выставляется последний указанный шаблон. Значение 'null' – без шаблона. Доступный плэйсхолдер: [+val+].</td>
				<td>{comma separated string: chunkName; 'null'}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>outerTpl</td>
				<td>Шаблон внешней обёртки (при «outputFormat» != 'array'). Доступные плэйсхолдеры: [+result+], [+total+] (общее количество строк), [+resultTotal+] (количество возвращаемых строк), [+rowY.colX+] (где «Y» – номер строки, «X» – номер колонки).</td>
				<td>{string: chunkName}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>placeholders</td>
				<td>Дополнительные данные, которые необходимо передать в шаблон «outerTpl». Формат: строка, разделённая '::' между парой ключ-значение и '||' между парами.</td>
				<td>{separated string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>urlencode</td>
				<td>Надо URL-кодировать результирующую строку (при «outputFormat» != 'array')? Строка кодируется согласно RFC 3986.</td>
				<td>{0; 1}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>totalRowsToPlaceholder</td>
				<td>Имя внешнего плэйсхолдера, в который нужно вывести общее количество. Если параметр не задан – не выводится.</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>resultToPlaceholder</td>
				<td>Имя внешнего плэйсхолдера, в который нужно сохранить результат работы сниппета вместо обычного вывода. Если параметр не задан – сниппет просто возвращает реузльтат.</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
		</tbody>
	</table>
</div>

<p><span class="text-bold">Примеры</span></p>
<p><span class="text-bold">Вывод изображений с описаниями</span></p>
<p>Исходная строка (пусть находится в TV документа «images»):</p>
<pre class="brush: html;">/assets/images/some_img1.jpg::Изображение 1||/assets/images/some_img2.jpg::Изображение 2</pre>
<p>Вызов сниппета в шаблоне документа:</p>
<pre class="brush: html;">[[ddGetMultipleField?
&string=`[*images*]`
&rowTpl=`imgRow`
]]</pre>
<p>Код чанка «imgRow»:</p>
<pre class="brush: html;">[+col1+]:
&lt;img src="[+col0+]" alt="[+col1+]" /&gt;</pre>
<p><span class="text-bold">Получение и вывод данных из поля (TV) «prices» документа с id = 25 в виде таблицы, если что-то есть и ничего, если нету</span></p>
<p>Исходное значение поля:</p>
<pre class="brush: html;">Яблоки вкусные::100::кг||Гвозди обыкновенные::5 000::центнер||Коты::865::шт</pre>
<p>Вызов сниппета (где угодно):</p>
<pre class="brush: html;">[[ddGetMultipleField?
&docField=`prices`
&docId=`25`
&rowTpl=`pricesRow`
&outerTpl=`pricesWrap`
]]</pre>
<p>Код чанка «pricesRow»:</p>
<pre class="brush: html;">&lt;tr&gt;
	&lt;td&gt;[+rowNumber+]&lt;/td&gt;
	&lt;td&gt;[+col0+]&lt;/td&gt;
	&lt;td&gt;[+col1+] руб./[+val2+]&lt;/td&gt;
&lt;/tr&gt;</pre>
<p>Код чанка «pricesWrap»:</p>
<pre class="brush: html;">&lt;h1&gt;Табличка цен&lt;/h1&gt;
&lt;table&gt;
	[+result+]
&lt;/table&gt;</pre>
<p><span class="text-bold">Вывод тегов документа через запятую с использованием регулярного выражения в «rowDelimiter»</span></p>
<p>Пусть теги документа у нас хранятся в TV «tags» и к этой TV у нас применён виджет <a target="_blank" href="managermanager/index.html#324">mm_widget_tags</a>. Пользователь заполняет теги через запятую, при этом, может заполняться как с пробелами по краям, так и без них.</p>
<p>Значение TV «tags»:</p>
<pre class="brush: html;">Коты, Кошки,Собаки , Медведи ,Слоны</pre>
<p>Вызов сниппета в шаблоне документа:</p>
<pre class="brush: html;">[[ddGetMultipleField?
&string=`[*tags*]`
&rowDelimiter=`/\s*,\s*/`
&rowGlue=`, `
&rowTpl=`tagsRow`
]]</pre>
<p>Код чанка «tagsRow»:</p>
<pre class="brush: html;">&lt;a href="[~[*parent*]~]?tags=[+col0+]"&gt;[+col0+]&lt;/a&gt;</pre>
<p>Результат:</p>
<pre class="brush: html;">&lt;a href="[~[*parent*]~]?tags=Коты"&gt;Коты&lt;/a&gt;,
&lt;a href="[~[*parent*]~]?tags=Кошки"&gt;Кошки&lt;/a&gt;,
&lt;a href="[~[*parent*]~]?tags=Собаки"&gt;Собаки&lt;/a&gt;,
&lt;a href="[~[*parent*]~]?tags=Медведи"&gt;Медведи&lt;/a&gt;,
&lt;a href="[~[*parent*]~]?tags=Слоны"&gt;Слоны&lt;/a&gt;</pre>

<h3 class="sub-header text-bold"><a id="1008"></a>Сниппет ddTypograph</h3>
<p>Сниппет типографирует текст. Не использует сторонних сервисов, не отправляет никаких запросов, всё делается прямо у вас на сервере.</p>
<div class="flip-scroll">
	<table class="table table-bordered table-vcenter flip-content">
		<thead class="flip-content bordered-palegreen">
			<tr><th>Название</th><th>Описание</th><th>Допустимые значения</th><th>Значение по умолчанию</th></tr>
		</thead>
		<tbody>
			<tr>
				<td class="em">text <span class="help">*<span class="helpPopup"></span></span></td>
				<td>Текст, который нужно типографировать.</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>optAlign</td>
				<td>Оптическое выравнивание (висячая пунктуация).</td>
				<td>{0; 1}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>text_paragraphs</td>
				<td>Простановка параграфов и переносов строк.</td>
				<td>{0; 1}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>text_autoLinks</td>
				<td>Выделение ссылок из текста (в том числе email).</td>
				<td>{0; 1}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>etc_unicodeConvert</td>
				<td>Преобразовывать html-сущности в юникод (– вместо <span>&</span>mdash; и т.д.).</td>
				<td>{0; 1}</td>
				<td>1</td>
			</tr>
			<tr>
				<td>noTags</td>
				<td>Не добавлять теги. Бывают ситуации, когда использование HTML-тегов в тексте недопустимо (например, когда текст выводится в значение атрибута тега), для таких случаев и предназначен этот параметр.</td>
				<td>{0; 1}</td>
				<td>0</td>
			</tr>
		</tbody>
	</table>
</div>

<p><span class="text-bold">Примеры</span></p>
<p>Типографирование аннотации перед выводом</p>
<pre class="brush: html;">[[ddTypograph? &text=`[*introtext*]`]]</pre>
<p>Типографирование аннотации с автоматической расстановкой абзацев, ссылок и адресов email</p>
<pre class="brush: html;">[[ddTypograph? &text=`[*introtext*]` &text_paragraphs=`1` &text_autoLinks=`1`]]</pre>
<p>Типографирование аннотации с автоматическим оптическим выравниванием (висячие кавычки и пр.)</p>
<pre class="brush: html;">[[ddTypograph? &text=`[*introtext*]` &optAlign=`1`]]</pre>

<h3 class="sub-header text-bold"><a id="1009"></a>Сниппет ddYMap</h3>
<p>Сниппет для вывода на страницу Яндекс.Карт в простом виде.</p>
<p>Удобно использовать совместно с виджетом <a target="_blank" href="managermanager/index.html#928">mm_ddYMap</a>.</p>
<p class="alert alert-warning"><span class="text-bold">Внимание!</span> На странице уже должен быть подключен jQuery.</p>
<p class="alert alert-info">Из пары параметров «geoPos» / «docField» необходимо передавать лишь один.</p>
<p class="alert alert-info">Сниппет можно вызывать в любом месте страницы, место его вызова не имеет значения.</p>
<div class="flip-scroll">
	<table class="table table-bordered table-vcenter flip-content">
		<thead class="flip-content bordered-palegreen">
			<tr><th>Название</th><th>Описание</th><th>Допустимые значения</th><th>Значение по умолчанию</th></tr>
		</thead>
		<tbody>
			<tr>
				<td class="em">geoPos <span class="help">*<span class="helpPopup"></span></span></td>
				<td>Координаты на карте (широта и долгота, перечисленные через запятую).</td>
				<td>{comma separated string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>docField</td>
				<td>Имя поля документа, содержащего координаты, значение которого необходимо получить.</td>
				<td>{string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>docId</td>
				<td>ID документа, значение поля которого нужно получить.</td>
				<td>{integer}</td>
				<td>текущий документ</td>
			</tr>
			<tr>
				<td>mapElement</td>
				<td>Селектор контейнера, где будет находиться карта.</td>
				<td>{string}</td>
				<td>'#map'</td>
			</tr>
			<tr>
				<td>defaultType</td>
				<td>Тип карты по умолчанию: 'map' – схема, 'satellite' – спутник, 'hybrid' – гибрид, 'publicMap' – народная карта, 'publicMapHybrid' – народный гибрид.</td>
				<td>{'map'; 'satellite'; 'hybrid'; 'publicMap'; 'publicMapHybrid'}</td>
				<td>'map'</td>
			</tr>
			<tr>
				<td>defaultZoom</td>
				<td>Масштаб карты по умолчанию.</td>
				<td>{integer}</td>
				<td>15</td>
			</tr>
			<tr>
				<td>icon</td>
				<td>Изображение иконки для метки на карте.</td>
				<td>{string}</td>
				<td>без иконки (используется стандартная)</td>
			</tr>
			<tr>
				<td>iconOffset</td>
				<td>Смещение иконки в пикселях относительно базового положения, задается в виде пары чисел, разделенных запятой (x, y). Базовое положение: иконка располагается горизонтально по центру точки (geoPos), вертикально – над точкой.</td>
				<td>{comma separated string}</td>
				<td>–</td>
			</tr>
			<tr>
				<td>scrollZoom</td>
				<td>Разрешёно ли изменение масштаба карты колесом мыши?</td>
				<td>{0; 1}</td>
				<td>0</td>
			</tr>
			<tr>
				<td>mapCenterOffset</td>
				<td>Смещение центра карты относительно центра контейнера в пикселях.</td>
				<td>{comma separated string}</td>
				<td>–</td>
			</tr>
		</tbody>
	</table>
</div>
<p><span class="text-bold">Примеры</span></p>
<pre class="brush: html;">[[ddYMap? &geoPos=`55.177446326764496,61.29041790962219`]]</pre>