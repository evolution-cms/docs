
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Параметры</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="547"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse547"><span class="text-bold">&config</span> - Загрузка выборочной конфигурации</a></h4>
</div>
<div id="collapse547" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Имя конфигурационного файла<br>
<span class="text-bold">Значение по умолчанию:</span> default<br>
<span class="text-bold">Примечание:</span> Файл конфигурации может включать значения различных параметров Ditto, избавляя от неудобств, связанных с ограничениями, накладываемыми MODX на значения параметров сниппетов (нельзя использовать &, `, <em>&lt;enter&gt;</em> т.п.). Файлы конфигурации сохраняются в папке <em><span class="text-bold">&ditto_base</span></em>/configs/. Их имена имею формат <em><span class="text-bold">&config</span></em>.config.php<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&config=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="548"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse548"><span class="text-bold">&dateFormat</span> - Формат времени для PHP</a></h4>
</div>
<div id="collapse548" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любой валидный формат времени, который соответствует правилам функции PHP - strftime<br>
<span class="text-bold">Значение по умолчанию:</span> [LANG]<br>
<span class="text-bold">Примечание:</span> Определяет формат времени, которое выводится с помощью плейсхолдера<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&dateFormat=`%d.%m.%Y`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="549"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse549"><span class="text-bold">&dateSource</span> - Источник определяющий значение [+date+]</a></h4>
</div>
<div id="collapse549" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Время в формате UNIX timestamp из поля MODX или TV-параметра<br>
<span class="text-bold">Значение по умолчанию:</span> createdon<br>
<span class="text-bold">Примечание:</span> Любое значение времени в формате UNIX timestamp из поля MODX или TV-параметра, как например createdon, pub_date, or editedon.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&dateSource=`pub_date`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="550"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse550"><span class="text-bold">&debug</span> - Включить / выключить режим отладки</a></h4>
</div>
<div id="collapse550" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> Режим отладки позволяет разобраться в сложных и непонятных ситуациях. Особенно актуальная возможндость для крупных сайтов, где множество вызовов Ditto могут конфликтовать между собой. При включенном режиме отладки помимо результатов работы выводится множество полезной для разработчика информации (все параметры, список документов результата, их ID и т.п.).<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&debug=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="551"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse551"><span class="text-bold">&depth</span> - Глубина поиска документов</a></h4>
</div>
<div id="collapse551" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> Число уровней в глубину для поиска документов. Документы будут найдены внутри документов-контейнеров, указанных в &startID и &parents и вложенных документов-контейнеров до уровня указанного в &depth. Т.е. если этот параметр равен 1, то будут брать только непосредственно дочерние документы, указанных в &startID и &parents. Если &depth = 2, в поиск пройдет еще и в дочерних.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&depth=`5`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="552"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse552"><span class="text-bold">&display</span> - Число отображаемых документов</a></h4>
</div>
<div id="collapse552" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число | all<br>
<span class="text-bold">Значение по умолчанию:</span> 3<br>
<span class="text-bold">Примечание:</span> all - все документы<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&display=`10`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="553"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse553"><span class="text-bold">&ditto_base</span> - Расположение фалов Ditto</a></h4>
</div>
<div id="collapse553" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> путь<br>
<span class="text-bold">Значение по умолчанию:</span> [(base_path)]assets/snippets/ditto/<br>
<span class="text-bold">Примечание:</span> Папка со слэшем на конце, указывающая размещение фалов Ditto на сервере. Как правило этот параметр изменять не приходится.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&ditto_base=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="554"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse554"><span class="text-bold">&documents</span> - Список ID документов для результата</a></h4>
</div>
<div id="collapse554" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ID документов, через запятую<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Этот параметр должен сожержать список ID'ов тех документов, которые будут отображены в результатах. Т. е. можно жестко задать список документов, которые будут отображаться.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&documents=`1, 35, 122`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="555"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse555"><span class="text-bold">&extenders</span> - Имена расширений</a></h4>
</div>
<div id="collapse555" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Расширения через запятую<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Указывает Ditto, какие расширения следует загрузить. Пример расширения с комментариями (на английском) можно найти по пути: &ditto_base/extenders/example.extender.inc.php. Все расширения находятся в папке &ditto_base/extenders/ и имена файлов имеют формат: name.extender.inc.php.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&extenders=`summary`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="556"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse556"><span class="text-bold">&filter</span> - Фильтр для отсеивания документов</a></h4>
</div>
<div id="collapse556" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле,критерий,тип сравнения<br>
<span class="text-bold">Значение по умолчанию:</span> NULL<br>
<span class="text-bold">Примечание:</span> Используется формат <span class="text-bold">`поле,критерий,тип сравнения`</span> с запятой между значениями.<br>
<span class="text-bold">Список фильтров:</span><br>
<span class="text-bold">По умолчанию:</span> NULL<br>
<span class="text-bold">Типы сравнения:</span><br>
<span class="text-bold">1</span> - != (не соответствует критерию)<br>
<span class="text-bold">2</span> - == (соответствует критерию)<br>
<span class="text-bold">3</span> - &lt; (меньше критерия)<br>
<span class="text-bold">4</span> - &gt; (больше критерия)<br>
<span class="text-bold">5</span> - &lt;= (меньше или равен критерию)<br>
<span class="text-bold">6</span> - &gt;= (больше или равен критерию)<br>
<span class="text-bold">7</span> - (не содержит текст критерия)<br>
<span class="text-bold">8</span> - (содержит текст критерия)<br>
<span class="text-bold"> 9</span> - case insenstive version of #7<br>
<span class="text-bold">10</span> - case insenstive version of #8<br>
<span class="text-bold">11</span> - checks leading character of the field<br>
Может содержать несколько запросов, разделенных глобальным разделителем |.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&filter=`id,10,2|id,20,2`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="557"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse557"><span class="text-bold">&format</span> - Используемый формат для вывода</a></h4>
</div>
<div id="collapse557" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> html | json | xml | atom | rss<br>
<span class="text-bold">Значение по умолчанию:</span> html<br>
<span class="text-bold">Примечание:</span> Ditto умеет работать с различными форматами данных. Например, он может выводить RSS ленту новостей или данные в XML формате.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&format=`rss`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="558"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse558"><span class="text-bold">&globalFilterDelimiter</span> - Разделитель правил фильтра</a></h4>
</div>
<div id="collapse558" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любой сивол, который не будет использоваться в правиле фильтра<br>
<span class="text-bold">Значение по умолчанию:</span> |<br>
<span class="text-bold">Примечание:</span> Задает значение разделителя для параметра &filter.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&globalFilterDelimiter=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="559"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse559"><span class="text-bold">&hiddenFields</span> - Возвращать необработанные поля</a></h4>
</div>
<div id="collapse559" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любое название параметра MODX или TV-параметра, перечисленные через запятую.<br>
<span class="text-bold">Значение по умолчанию:</span> NULL<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&hiddenFields=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="560"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse560"><span class="text-bold">&hideFolders</span> - Скрывать документы-контейнеры</a></h4>
</div>
<div id="collapse560" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&hideFolders=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="561"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse561"><span class="text-bold">&hidePrivate</span> - Запрещает показ документов если пользователь не имеет разрешения на просмотр</a></h4>
</div>
<div id="collapse561" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&hidePrivate=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="562"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse562"><span class="text-bold">&id</span> - Унакальный ID сессии Ditto</a></h4>
</div>
<div id="collapse562" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Числа или буквы английского алфавита. Строка чувствительна к регистру.<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Уникальный идентификатор нужен главным образом тогда, когда необходимо использовать более одного вызова Ditto на странице, причем актуален этот параметр тогда, когда для более чем одного вызова Ditto используются глобальные плэйсхолдеры.<br>
К примеру, Вы выводите на одной странице спосок новостей и список последних публикаций, причем оба списка имеют пэйджер. Если Вы вставите дважды [+pages+], то оба пэйджера будут управлять двумя списками сразу. Это во-первых. А во-вторых оба пэйджера буду отражать страницы первого списка. Т.е. когда MODX обработает первый вызов, он заменит оба плэйсхолдера [+pages+] на это значение. А список страниц второго списка ни куда не попадет.<br>
Так вот в таком случае, следует использовать для каждого вызова Ditto свой id. А глобальные плэйсхолдеры примут вид [+id_placeholder+]. Символ подчеркивания между идентификатором и названием плэйсхолдера добавится автоматически.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&id=`nav`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="563"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse563"><span class="text-bold">&keywords</span> - Использование выборки ключевых слов</a></h4>
</div>
<div id="collapse563" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> Используется как [+keywords+] или источник tagData.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&keywords=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="564"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse564"><span class="text-bold">&language</span> - язык Ditto</a></h4>
</div>
<div id="collapse564" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Название языкового файла<br>
<span class="text-bold">Значение по умолчанию:</span> english<br>
<span class="text-bold">Примечание:</span> В языковых файлах Ditto хранятся шаблоны, используемые по-умолчанию, описания ошибок и уведомления.<br>
Ditto сначала загружает свой стандартный языковой файл, а уже после этого тот файл, что указан в данном параметре. Таким образом, если в файле указанном пользователем нет какой-либо строки, она будет использована из стандартного файла.
Примечание. Языковые файлы находятся в папке &ditto_base/lang/. Имена имею формат: &language.inc.php<br><br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&language=`russian-UTF8`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="565"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse565"><span class="text-bold">&localFilterDelimiter</span> - Разделитель, используемый для разделения отдельных параметров в каждой строке фильтра</a></h4>
</div>
<div id="collapse565" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любой сивбол, который не будет использоваться в параметре фильтра<br>
<span class="text-bold">Значение по умолчанию:</span> ,<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&localFilterDelimiter=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="566"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse566"><span class="text-bold">&noResults</span> - Текст выводимый если нет результата</a></h4>
</div>
<div id="collapse566" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любой текст или название чанка<br>
<span class="text-bold">Значение по умолчанию:</span> LANG<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&noResults=`Документы не найдены`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="567"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse567"><span class="text-bold">&orderBy</span> - Порядок и направление, используемые для сортировки результатов</a></h4>
</div>
<div id="collapse567" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Разделенный запятыми список<br>
<span class="text-bold">Значение по умолчанию:</span> createdon DESC<br>
<span class="text-bold">Примечание:</span> Взамен &sortBy и &sortDir.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&orderBy=`pagetitle ASC`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="572"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse572"><span class="text-bold">&parents</span> - Идентификаторы контейнеров</a></h4>
</div>
<div id="collapse572" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Список ID через запятую<br>
<span class="text-bold">Значение по умолчанию:</span> Текущий документ<br>
<span class="text-bold">Примечание:</span> Указывает Ditto список идентификаторов (id) документов-контейнеров, откуда будут браться документы для вывода Ditto. Документы беруться до глубины &depth.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&parents=`1, 5, 8`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="573"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse573"><span class="text-bold">&phx</span> - Использование PHx форматирования</a></h4>
</div>
<div id="collapse573" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> В Ditto имеетвы встроенный парсер PHx. Эта опция включает / выключает его.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&phx=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="574"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse574"><span class="text-bold">&queryLimit</span> - Лимит на запрос в базе</a></h4>
</div>
<div id="collapse574" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> 0 - нет ограничения<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&queryLimit=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="575"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse575"><span class="text-bold">&randomize</span> - Вывод документов в случайном порядке</a></h4>
</div>
<div id="collapse575" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> Остерегайтесь кэшированных вызовов!<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&randomize=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="576"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse576"><span class="text-bold">&removeChunk</span> - Названия вырезаемых чанков</a></h4>
</div>
<div id="collapse576" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любое название чанка, которое используется при выводе<br>
<span class="text-bold">Значение по умолчанию:</span> NULL<br>
<span class="text-bold">Примечание:</span> Обычно используется для удаления комментариев<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&removeChunk=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="577"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse577"><span class="text-bold">&save</span> - Сохранить результат в плэйсхолдер</a></h4>
</div>
<div id="collapse577" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1 | 2 | 3<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание: 0</span> - off; returns output<br>
<span class="text-bold">1</span> - remaining; returns output<br>
<span class="text-bold">2</span> - all;<br>
<span class="text-bold">3</span> - all; returns ph only<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&save=`3`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="578"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse578"><span class="text-bold">&seeThruUnpub</span> - Смотреть сквозь неопубликованные документы</a></h4>
</div>
<div id="collapse578" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> Используется если глубина (&depth) больше 1<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&seeThruUnpub=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="579"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse579"><span class="text-bold">&showInMenuOnly</span> - Показывать только документы видимые в меню</a></h4>
</div>
<div id="collapse579" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>
<span class="text-bold">0</span> - показывать все документы<br>
<span class="text-bold">1</span> - показывать только документы у которых поставлен флаг «Показывать в меню»<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&showInMenuOnly=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="580"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse580"><span class="text-bold">&showPublishedOnly</span> - Показывать только опубликованные документы</a></h4>
</div>
<div id="collapse580" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<span class="text-bold">0</span> - показывать только неопубликованные документы<br>
<span class="text-bold">1</span> - показывать только опубликованные документы<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&showPublishedOnly=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="581"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse581"><span class="text-bold">&start</span> - Пропуск начальных документов</a></h4>
</div>
<div id="collapse581" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&start=`5`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="583"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse583"><span class="text-bold">&total</span> - Число возвращаемых документов</a></h4>
</div>
<div id="collapse583" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число | all<br>
<span class="text-bold">Значение по умолчанию:</span> all<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&total=`10`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="584"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse584"><span class="text-bold">&where</span> - Специальное условие для запроса</a></h4>
</div>
<div id="collapse584" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> Любое валидное выражение MySQL WHERE<br>
<span class="text-bold">Значение по умолчанию:</span> NULL<br>
<span class="text-bold">Примечание:</span> Используется только для параметров документов. Не поддерживает TV-параметры.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&where=``</pre>
</div>
</div>
</div>
</div>