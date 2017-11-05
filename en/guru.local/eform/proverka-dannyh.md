
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>eForm: Проверка данных</h2>

<p>Эта версия поддерживает расширенную проверку на стороне сервера и фильтрацию, использующую очень гибкие правила проверки, которые включаются в параметр eform. Вы можете определить 2 дополнительных параметра проверки, сообщение об ошибке и проверке или правило фильтра.</p>
<p>Например:</p>
<pre class="brush: html;">eform="Year of Birth:integer:1:Must be between 1950 and 2002:#RANGE 1950-2002"</pre>

<h3 class="sub-header text-bold">Правила проверки</h3>
<p><span class="text-bold">#LIST</span> - перечисленные через запятую возможные значения.</p>
<p>Например:</p>
<pre class="brush: html;">#LIST красный,зеленый,оранжевый,синий</pre>
<p><span class="text-bold">#RANGE</span> - разделенные запятой возможный числовые значения или числовые диапазоны. При установке диапазона порядок не имеет значения. 1~10 и 10~1 будут одинаково определять числа между 1 и 10 (включительно). Можно использовать как положительные так и отрицательные числа.</p>
<p>Например:</p>
<pre class="brush: html;">#RANGE 1,3,-5~-15,60~82</pre>
<p><span class="text-bold">#SELECT</span> - определяет правильность значений, которые будут возвращены из базы при запросе. Запрос должен возвращать значения только одной колонки (функция проверяет только первую колонку). Вы можете использовать {\DBASE} {\PREFIX} тэги. Они будут автоматически заменены на название базы MODX и используемый префикс таблицы.</p>
<p>Например:</p>
<pre class="brush: html;">#SELECT keyword FROM {\PREFIX}site_keywords</pre>
<p><span class="text-bold">#EVAL</span> - строка кода PHP. Может возвращать true или false. Внимание! Хотя #EVAL все еще используется в eForm 1.4, но в будущих версиях они скорее всего больше не будут поддерживаться. Взамен используйте #FUNCTION.</p>
<p><span class="text-bold">#FUNCTION</span> - название функции. Функция должна использовать только одно значение (значение поля) и возвращать TRUE или FALSE. Смотрите примеры, чтобы разобраться как это действует.</p>
<p>Например:</p>
<pre class="brush: html;">#FUNCTION myValidationFunction</pre>
<p><span class="text-bold">#REGEX</span> - регулярное выражение. Синтаксис preg_match() в PHP.</p>
<p>Пример:</p>
<pre class="brush: html;">#REGEX /^[\a-z]+ [\a-z0-9_]+/i</pre>
<p><span class="text-bold">#FILTER</span> - фильтры не проверяют введенных значений, но заменяют слова и значения, которые соответствуют критериям. Вы можете использовать следующие фильтры:</p>
<ul>
	<li>#FILTER #LIST<br> Используйте две вертикальные черты для разделения заменяемых и заменяющих слов.<br> Например:
		<pre class="brush: html;">#FILTER #LIST badword,verybadword||goodword,verygoodword</pre>
	</li>
	<li>#FILTER #EVAL<br> Например:
		<pre class="brush: html;">#FILTER #EVAL return myFilterFunction($value);</pre>
		<p>(естественно вы должны быть уверены в существовании указанной функции)<br><br>Примеры применения фильтра:</p>
		<pre class="brush: php;">function myFilterFunction($value){
	$badWords = array('scribble','coding');
	$goodWords = array('design','sleep');
	return str_replace($badWords,$goodWords,$value);
}</pre>
	</li>
	<li>#FILTER #REGEX<br> Регулярное выражение замены. Синтаксис preg_replace() в PHP. Поиск и выражение замены разделяется двумя вертикальными чертами (||)</li>
</ul>

<h3 class="sub-header text-bold">Поля select, radio и checkbox</h3>
<p>Эти поля имеют автоматическу проверку. Все полученные значения проверяются на соответствие установленными вами в шаблоне формы. Это позволяет избежать добавления посторонних значений в эти поля.</p>

<h3 class="sub-header text-bold">Скрытые поля</h3>
<p>По умолчанию скрытые поля присутствуют как защита от подделки формы при сравнении используемых значений (как в полях select, radio и checkbox). Но в некоторых местах это может быть ненужно. Например если вы используете обработку javascript, которая хранит свои значения в скрытых полях. В это случае вы можете изменить это поведение используя параметр eform (включая или выключая проверку).</p>
<p>Скрытое поле пример 1:</p>
<p>Встроенное поведение удобно, если вы храните в скрытом поле идентификатор документа и не хотите чтобы он был изменен кем-либо. Поле должно выглядеть примерно так:</p>
<pre class="brush: html;">&lt;input type="hidden" name="docId" value="31" /&gt;</pre>
<p>Скрытое поле пример 2:</p>
<p>Если вы используете javascript, который хранит значения в скрытых полях, то вам необходимо убрать проверку поля так:</p>
<pre class="brush: html;">&lt;input type="hidden" name="calculatedField" value="" eform="::0::" /&gt;</pre>
<p>Скрытое поле пример 3:</p>
<p>Пример похожий на 2, но вы хотите убедиться, что возвращенные значения лежат в допустимом диапазоне чисел. Установим для параметра eform заголовок, числовой тип данных, обязательность заполнения, сообщение об ошибке и проверку на диапазон. Это будет выглядеть так:</p>
<pre class="brush: html;">&lt;input type="hidden" name="calculatedField" value="" eform="Calculated Value:integer:1:Calculation out of range:#RANGE 1-10" /&gt;</pre>

<h3 class="sub-header text-bold">Пример полей с проверкой</h3>
<p>Выпадающий список - обязательное поле (не требуется проверка)</p>
<pre class="brush: html;">
&lt;select name="mySelect" eform_options="Select Country::1" /&gt; (тип данных не определен)
	&lt;option value="en-au"&gt;Australia&lt;/option&gt;
	&lt;option value="en-us"&gt;USA&lt;/option&gt;
&lt;/select&gt;
</pre>
<p>Текстовое поле - обязательное поле и формат данных для дат.</p>
<pre class="brush: html;">&lt;input type="text" name="dobDate" eform_options="Date of Birth:date:1:@EVAL return (strtotime($value)!==-1)?true:false;" /&gt;</pre>
<p>Много чекбоксов - обязательное поле, можно выбрать несколько значений.</p>
<pre class="brush: html;">
&lt;input type="checkbox" name="myColors[]" value="Red" eform_options="Colors::1" /&gt; (тип данных не определен)
&lt;input type="checkbox" name="myColors[]" value="Green" /&gt; (тип данных не определен)
</pre>