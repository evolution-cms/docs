
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: Параметры выборки</h2>

<h3 class="sub-header text-bold">&amp;controller</h3>
<p>Задает класс для выборки данных. Базовые классы (расположены в папке DocLister/core/controller/):</p>
<ul>
<li>site_content - для работы с документами MODX;</li>
<li>shopkeeper - для работы с каталогом Shopkeeper;</li>
<li>onetable - для работы с произвольными таблицами;</li>
<li>site_content_tags - вывод документов MODX с фильтрацией по тэгам в связке с плагином TagSaver.</li>
</ul>
<p><span class="text-bold">Значение по умолчанию</span> - site_content</p>
<h3 class="sub-header text-bold">&amp;idType</h3>
<p>Тип выборки документов.</p>
<p>Список документов подставляемых в запрос будет выбран из параметра, имя которого совпадает со значением данного параметра. </p>
<p>Во избежание недоразумений рекомендуется всегда явно определять этот параметр. Особенно актуально, когда одновременно используются параметры parents и documents.</p>
<p><span class="text-bold">Возможные значения</span> - parents, documents.</p>
<p><span class="text-bold">Значение по умолчанию</span> - parents</p>
<h3 class="sub-header text-bold">&amp;parents</h3>
<p>Выборка документов на основании списка родительских документов. </p>
<p><span class="text-bold">Возможные значения</span> - значения id родительских документов, разделенные запятой.</p>
<p><span class="text-bold">Значение по умолчанию</span> - id страницы, на которой вызывается сниппет.</p>
<h3 class="sub-header text-bold">&amp;documents</h3>
<p>Выборка произвольных документов. </p>
<p>Если используется параметр parents__, то документы перечисленные в этом параметре будут просто подмешаны в результат и подвержены последующим правилам выборки (фильтрация, сортировка).</p>
<p><span class="text-bold">Возможные значения</span> - значения id документов, разделенные запятой.</p>
<h3 class="sub-header text-bold">&amp;ignoreEmpty</h3>
<p>Позволяет сделать выборку всех записей из таблицы, если параметр documents не задан. Параметр idType в этом случае должен быть documents.</p>
<p><span class="text-bold">Возможные значения</span> - 1 или 0.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;display</h3>
<p>Максимальное число документов при выборке.</p>
<p><span class="text-bold">Возможные значения</span> - целое число, которое больше или равно нулю.</p>
<p>Может быть переопределено значением параметра queryLimit.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;queryLimit</h3>
<p>Максимальное число документов при выборке.</p>
<p><span class="text-bold">Возможные значения</span> - целое число, которое больше или равно нулю.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;depth</h3>
<p>Глубина выборки с использованием параметра parents. </p>
<p><span class="text-bold">Возможные значения</span> - целое число, которое больше или равно нулю.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;offset</h3>
<p>Число пропускаемых документов с начала списка. Переопределяется при использовании пагинации. Если же требуется всегда пропускать N документов, то необходимо использовать параметр start.</p>
<p><span class="text-bold">Возможные значения</span> - целое число, которое больше или равно нулю.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;start</h3>
<p>Число документов пропускаемых с начала выборки. Складывается со значением offset автоматически устанавливаемым при пагинации.</p>
<p><span class="text-bold">Возможные значения</span> - целое число, которое больше или равно нулю.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;total</h3>
<p>Максимальное число документов отображаемое на 1 странице в выборке. </p>
<p><span class="text-bold">Возможные значения</span> - целое число, которое больше или равно нулю.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;addWhereList</h3>
<p>Дополнительные условия выборки документов. Любая строка удовлетворяющая требованиями строки для подстановки в WHERE блок SQL запроса. </p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h3 class="sub-header text-bold">&amp;showParent</h3>
<p>Исключение документов из которых делалась выборка с использованием параметра parents.</p>
<p><span class="text-bold">Возможные значения</span>:</p>
<ul>
<li>0 - принудительное игнорирование родителей в выборке;</li>
<li>1 - принудительное добавление родителя в выборку;</li>
<li>-1 - игнорируются только родители, указанные в параметре parents.</li>
</ul>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>
<h3 class="sub-header text-bold">&amp;selectFields</h3>
<p>Имена полей, включаемых в выборку.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h3 class="sub-header text-bold">&amp;groupBy</h3>
<p>Группировка результатов по какому-нибудь полю.</p>
<p><span class="text-bold">Значение по умолчанию</span> - определяется в контроллере</p>
<h2 class="page-header">Параметры выборки для произвольных таблиц (контроллер onetable)</h2>
<h3 class="sub-header text-bold">&amp;table</h3>
<p>Имя таблицы по которой будет производиться выборка. Если в таблице PrimaryKey отличается от id, то необходимо дополнительно задать имя этого поля в параметре idField. </p>
<p><span class="text-bold">Возможные значения</span> - любое имя таблицы без префикса таблиц MODX. </p>
<p><span class="text-bold">Значение по умолчанию</span> - site_content</p>
<h3 class="sub-header text-bold">&amp;idField</h3>
<p>Имя поля PrimaryKey. Документы, указанные через параметр documents, будут выбираться по этому полю.</p>
<p><span class="text-bold">Возможные значения</span> - любое имя поля доступного в таблице, указанной через параметр table. </p>
<p><span class="text-bold">Значение по умолчанию</span> - id</p>
<h3 class="sub-header text-bold">&amp;parentField</h3>
<p>Имя поля в котором хранятся значения idField родительских документов. Используется при выборке документов из параметра parents.</p>
<p><span class="text-bold">Возможные значения</span> - любое имя поля доступного в таблице, указанной через параметр table.</p>
<p><span class="text-bold">Значение по умолчанию</span> - parent.</p>
<h2 class="page-header">Выборка с TV-параметрами</h2>
<h3 class="sub-header text-bold">&amp;tvPrefix</h3>
<p>Префикс для плейсхолдеров создаваемых из имен TV-параметров.</p>
<p><span class="text-bold">Значение по умолчанию</span> - tv</p>
<h3 class="sub-header text-bold">&amp;tvList</h3>
<p>Список TV-параметров, которые должны быть в выборке.</p>
<p><span class="text-bold">Возможные значения</span> - имена TV-параметров, разделенные запятой.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h3 class="sub-header text-bold">&amp;renderTV</h3>
<p>TV-параметры, значение которых необходимо подготовить к отображению в соответствии с установленными виджетами. TV параметры которых нет в значении параметра tvList будут проигнорированы.</p>
<p><span class="text-bold">Возможные значения</span> - * или список имен TV параметров, разделенный запятой.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h2 class="page-header">Сортировка</h2>
<h3 class="sub-header text-bold">&amp;sortType</h3>
<p>Значение none определяет автоматическую сортировку правилами MySQL (как правило по primary key). </p>
<p><span class="text-bold">Возможные значения</span>:</p>
<p>** none - автоматическая сортировка правилами MySQL (обычно по primary key);</p>
<p>** doclist - вывод документов в том порядке, в каком они переданы в сниппет через параметр documents;</p>
<p>** other - сортировка по критериям указанным в параметрах orderBy, order и sortBy.</p>
<p><span class="text-bold">Значение по умолчанию</span> - none.</p>
<h3 class="sub-header text-bold">&amp;orderBy</h3>
<p>Единая строка сортировки (как минимум совокупность параметров sortBy и sortDir, но имеет больший приоритет). </p>
<p><span class="text-bold">Возможные значения</span> - любая строка удовлетворяющая правилам построения параметра ORDER BY в SQL запросе. При сортировке в контроллере site_content желательно использовать префикс c. для полей таблицы site_content. Имена TV-параметров указываются как есть.</p>
<p>Для сортировки в случайном порядке значение параметра orderBy будет "RAND()".</p>
<p><span class="text-bold">Значение по умолчанию</span> - id DESC (или определяется в контроллере)</p>
<h3 class="sub-header text-bold">&amp;sortBy</h3>
<p>Критерий сортировки без направления сортировки.</p>
<p><span class="text-bold">Возможные значения</span> - любая строка удовлетворяющая правилам построения параметра ORDER BY в SQL запросе. Имена TV-параметров указываются как есть.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто. Значение по умолчание может быть жестко задано в контроллере.</p>
<h3 class="sub-header text-bold">&amp;order</h3>
<p>Направление сортировки.</p>
<p><span class="text-bold">Возможные значения</span> - ASC, DESC. Значение данного параметра может быть переопределено значением параметра sortDir.</p>
<p><span class="text-bold">Значение по умолчанию</span> - DESC.</p>
<h3 class="sub-header text-bold">&amp;sortDir</h3>
<p>Синоним параметра order, но имеет больший приоритет. Если установлены 2 параметра order и sortDir, то будет использоваться значение параметра sortDir.</p>
<p><span class="text-bold">Возможные значения</span> - ASC, DESC. </p>
<p><span class="text-bold">Значение по умолчанию</span> - DESC (или определяется в контроллере).</p>
<h2 class="page-header">Сортировка по TV-параметрам</h2>
<h3 class="sub-header text-bold">&amp;tvSortType</h3>
<p>Правила приведения типов TV-параметров при сортировке.</p>
<p><span class="text-bold">Возможные значения</span> (перечисляются через запятую в том порядке, в котором указаны имена TV в параметре orderBy):</p>
<ul>
<li>DECIMAL - числа с 2 знаками после запятой;</li>
<li>UNSIGNED - беззнаковые целые числа;</li>
<li>SIGNED - целые больше нуля;</li>
<li>BINARY - бинарный режим;</li>
<li>DATETIME - дата;</li>
<li>TVDATETIME- приводит строку в дату согласно формату, который используется TV-параметром с типом ввода "Date" (доступно только из контроллеров на базе site_content).</li>
</ul>
<h3 class="sub-header text-bold">&amp;tvSortWithDefault</h3>
<p>В силу особенностей движка (TV-параметры значения которых совпадают со значениями по умолчанию не сохраняются в отдельную таблицу), сортировка записей может быть не корректа, если <span class="text-bold">Значение по умолчанию</span> отличается от пустой стрки. 
Поэтому рекомендуется дополнительно указывать ТВ параметры у которых принудительно указано <span class="text-bold">Значение по умолчанию</span>.</p>
<h2 class="page-header">Фильтрация</h2>
<h3 class="sub-header text-bold">&amp;showNoPublish</h3>
<p>Вывод удаленных или не опубликованных ресурсов (используется только в контроллерах на базе site_content)</p>
<p><span class="text-bold">Возможные значения</span> - 0/1.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0</p>
<h3 class="sub-header text-bold">&amp;filters</h3>
<p>Правила для фильтрации документов.</p>
<p><span class="text-bold">Возможные значения</span> - cтрока сформированая по правилам описанным в DocLister::getFilters(). Подробнее в разделе "Фильтры".</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<p>Пример строки:</p>
<pre class="brush: html;">
OR(AND(filter:field:operator:value;filter2:field:operator:value);(...))
</pre>
<h3 class="sub-header text-bold">&amp;filter_delimiter</h3>
<p>Разделитель фильтров для режима containsOne.</p>
<p><span class="text-bold">Возможные значения</span> - любая строка.</p>
<h2 class="page-header">Выборка по тэгам</h2>
<h3 class="sub-header text-bold">&amp;tagsData</h3>
<p>Строка определяющая источник тэгов.</p>
<p><span class="text-bold">Возможные значения</span> - cтрока с правилами разделеная двоеточием.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<p>Для автоматической подстановки тэгов из GET переменной необходимо указать имя этой переменной передав в этом параметре значение типа get:tag. В таком случае тэги должны подставляться в $<em>GET['tag']. В случае же если нужна статичная выборка, то можно get заменить на static и после двоеточия передать значение тэга, например, static:значение</em>тэга</p>
<h2 class="page-header">Дополнительные данные</h2>
<h3 class="sub-header text-bold">&amp;urlScheme</h3>
<p>Схема генерации URL</p>
<p><span class="text-bold">Возможные значения</span> - схемы доступные в MODX Evolution (относительные, http, https, full).</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто (относительные)</p>
<h3 class="sub-header text-bold">&amp;dateSource</h3>
<p>Поле документа в котором располагается дата. </p>
<p><span class="text-bold">Возможные значения</span> - название поля в таблице. Если в качестве значения была указана строка отличная от createdon и значение данного поля в базе равно 0, то тогда все равно берется значение из createdon. Для примера: Вы используете отложенную публикацию для некоторых документов и указываете сортировку по полю pub_date. Так вот, c DocLister у вас никогда не получится ситуации, что документы опубликованные без отложенной публикации всегда будут в конце списка. </p>
<p><span class="text-bold">Значение по умолчанию</span> - pub_date.</p>
<h3 class="sub-header text-bold">&amp;dateFormat</h3>
<p>Правила форматирования даты (format) для PHP функции strftime.</p>
<p>В качестве источника даты используется параметр dateSource. Помимо этого учитывается смещение даты на сервере (смотрите системный параметр server_offset_time). Таким образом, можно использовать персонализованную подстановку времени в зависимости от часового пояса пользователя.</p>
<p><span class="text-bold">Значение по умолчанию</span> - %d.%b.%y %H:%M.</p>
<h3 class="sub-header text-bold">&amp;summary</h3>
<p>Правила обработки текстов для формирования краткого описания. Загружает экстендер summary. В контроллере site_content есть дополнительное правило для обрабатываемого текста: по умолчанию на обработку отправляется поле content. Но если поле introtext не пустое, то текст именно из этого поля будет передан в дополнение summary. Аналогичным образом себе ведет и контроллер onetable.</p>
<p><span class="text-bold">Возможные значения</span> - cтрока сформированная по правилам экстендера summary:</p>
<pre class="brush: html;">
действие1:параметр1,действие2:параметр2А:параметр2Б,действие3
</pre>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h3 class="sub-header text-bold">&amp;introField</h3>
<p>Имя поля для источника краткого описания текста из contentField. Используется только если загружен экстендер summary.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h3 class="sub-header text-bold">&amp;contentField</h3>
<p>Имя поля в котором хранится основной текст документа. Используется только если загружен экстендер summary</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<h3 class="sub-header text-bold">&amp;e</h3>
<p>Экранирование значений полей. Имена полей доступны в шаблонах через плейсхолдеры с префиксом e: [+e.pagetitle+], [+e.longtitle+].</p>
<p><span class="text-bold">Возможные значения</span> - имена полей, через запятую.</p>
<h3 class="sub-header text-bold">&amp;jotcount</h3>
<p>Добавляет в выборку количество комментариев JotX с помощью экстендера jotcount.</p>
<p><span class="text-bold">Возможные значения</span> - 1 или 0.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>