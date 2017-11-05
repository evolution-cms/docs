
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Ditto: Плейсхолдеры</h2>

<p>Создавая шаблон Дитто, вы указываете плэйсхолдеры там, где вы хотите увидеть свои данные. У Дитто есть свои собственные пдэйсхолдеры, плюс он поддерживает переменные (поля) используемые в каждом документе. (<span class="text-bold">Примечание:</span> если вы хотите использовать переменные (поля) документа непосредственно на странице с обычным шаблоном, вы должны использовать формат <code>[*alias*]</code>)</p>
<h3 class="sub-header text-bold"><a id="938"></a>Плейсхолдеры документа</h3>
<div class="well bordered-left bordered-blue">
<p><code>[~[+id+]~]</code> – Создает полный URL, основанный на ID, но не создает саму ссылку.</p>
<p>Например:</p>
<pre class="brush: html;">&lt;h3&gt;&lt;a href="[~[+id+]~]"&gt;[+title+]&lt;/a&gt;&lt;/h3&gt;</pre>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Параметр</th><th>Описание</th></tr>
</thead>
<tbody>
<tr><th><code>[+alias+]</code></th><td>Псевдоним страницы, используется для создания ЧПУ</td></tr>
<tr><th><code>[+cacheable+]</code></th><td>Возвращает 1 (true) or 0 (false) если этот документ должен быть кэширован. По умолчанию установлено в false для нормального функционирования динамических сниппетов</td></tr>
<tr><th><code>[+content+]</code></th><td>Содержимое документа</td></tr>
<tr><th><code>[+contentType+]</code></th><td>Возвращает строчный параметр типа содержимого из выпадающего меню Content Type в панели администратора</td></tr>
<tr><th><code>[+content_dispo+]</code></th><td>Строка внедрения или прикрепления. Внедренные документы показываются в веб-браузерах. Прикрепленные документ могут быть загружены на локальную машину через диалоговое окно загрузки файла веб-браузера</td></tr>
<tr><th><code>[+createdby+]</code></th><td>Возвращает идентификатор пользователя, создавшего документ</td></tr>
<tr><th><code>[+createdon+]</code></th><td>Дата (в секундах с 1 января 1970 г.), когда документ был создан</td></tr>
<tr><th><code>[+deleted+]</code></th><td>Возвращает 1 (true) or 0 (false). Когда true, этот документ находится в корзине до ее очистки. После этого запись стирается полностью из базы данных (удаляется ПО-НАСТОЯЩЕМУ)</td></tr>
<tr><th><code>[+deletedby+]</code></th><td>Возвращает идентификатор пользователя, удалившего этот документ</td></tr>
<tr><th><code>[+deletedon+]</code></th><td>Возвращает дату удаления документа (в секундах с 1 января 1970 г.)</td></tr>
<tr><th><code>[+description+]</code></th><td>Описание документа</td></tr>
<tr><th><code>[+donthit+]</code></th><td>True (1) or False (0) показывает установлен или нет счетчик посещений страницы</td></tr>
<tr><th><code>[+editedby+]</code></th><td>Возвращает идентификатор пользователя, который последний редактировал документ</td></tr>
<tr><th><code>[+editedon+]</code></th><td>Возвращает дату последнего редактирования (в секундах с 1 января 1970 г.)</td></tr>
<tr><th><code>[+haskeywords+]</code></th><td>True (1) or False (0) показывает установлены или нет ключевые слова для данного документа</td></tr>
<tr><th><code>[+hasmetatag+]</code></th><td>True (1) or False (0) показывает установлены или нет метатэги для данного документа</td></tr>
<tr><th><code>[+hidemenu+]</code></th><td>Возвращает 1 (true) или 0 (false) – соответственно если этот документ показывается в меню или нет</td></tr>
<tr><th><code>[+id+]</code></th><td>Целое число обозначающее или показывающее идентификатор документа</td></tr>
<tr><th><code>[+introtext+]</code></th><td>Аннотация документа</td></tr>
<tr><th><code>[+isfolder+]</code></th><td>Целое число: true (1) если документ является контейнером или false (0) если нет.</td></tr>
<tr><th><code>[+longtitle+]</code></th><td>Расширенный заголовок документа</td></tr>
<tr><th><code>[+menuindex+]</code></th><td>Целое число показывающее позицию в меню</td></tr>
<tr><th><code>[+menutitle+]</code></th><td>Название документа в меню</td></tr>
<tr><th><code>[+pagetitle+]</code></th><td>Заголовок документа</td></tr>
<tr><th><code>[+parent+]</code></th><td>идентификатор родительского документа</td></tr>
<tr><th><code>[+privatemgr+]</code></th><td>True (1) or False (0) показывает установлены ли разрешения на просмотр этого документа для менеджеров</td></tr>
<tr><th><code>[+privateweb+]</code></th><td>True (1) or False (0) показывает установлены ли разрешения на просмотр этого документа для веб-пользователей</td></tr>
<tr><th><code>[+pub_date+]</code></th><td>Дата с которой документ опубликуется (в секундах с 1 января 1970 г.). Примечание: если этот параметр указан, published автоматически устанавливается в true (1)</td></tr>
<tr><th><code>[+published+]</code></th><td>Целое число показывающее статус публикования (0 = нет, 1 = да)</td></tr>
<tr><th><code>[+richtext+]</code></th><td>true (1) или false (0), устанавливается, если в администраторской панели должен использоваться rich text editor</td></tr>
<tr><th><code>[+searchable+]</code></th><td>Возвращает 1 (true) или 0 (false), что означает что этот документ доступен или не доступен для поиска</td></tr>
<tr><th><code>[+template+]</code></th><td>идентификатор шаблона, используемого для этого документа</td></tr>
<tr><th><code>[+type+]</code></th><td>Возвращает строчный параметр document для страниц или "reference" для ссылок</td></tr>
<tr><th><code>[+unpub_date+]</code></th><td>Дата окончания публикации документа (в секундах с 1 января 1970 г.). Примечание: установка этого параметра НЕ имеет эффекта на изменение статуса установок published</td></tr>
</tbody>
</table>
</div>
</div>
<h3 class="sub-header text-bold"><a id="939"></a>Плейсхолдеры Дитто</h3>
<div class="well bordered-left bordered-blue">
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Параметр</th><th>Описание</th></tr>
</thead>
<tbody>
<tr><th><code>[+author+]</code></th><td> Имя автора. Сначала createdby-&gt;fullname, createdby-&gt;username, admin</td></tr>
<tr><th><code>[+date+]</code></th><td>Дата в установленном формате. По умолчанию используется createdon (editedon и pub_date как варианты)</td></tr>
<tr><th><code>[+ditto_iteration+]</code></th><td>Порядковый номер полученного документа в пределах текущей страницы</td></tr>
<tr><th><code>[+ditto_sort+]</code></th><td>Порядковый номер полученного документа в пределах полного набора документов</td></tr>
<tr><th><code>[+title+]</code></th><td>Содержимое поля заголовка</td></tr>
<tr><th><code>[+url+]</code></th><td>Ссылка на документ</td></tr>
<tr><th><code>[+ditto+] или [+wrapper+]</code></th><td>С версии 2.1.1. Используется в шаблоне &outerTpl. Место вывода результата работы сниппета</td></tr>
<tr><th><code>[+ditto_class+]</code></th><td>С версии 2.1.1. Выводит классы even/odd, first/last и current</td></tr>
</tbody>
</table>
</div>
</div>
<h3 class="sub-header text-bold"><a id="940"></a>Плейсхолдеры пагинации</h3>
<div class="well bordered-left bordered-blue">
<div class="flip-scroll"><table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Параметр</th><th>Описание</th></tr>
</thead>
<tbody>
<tr><th><code>[+next+]</code></th><td>Кнопка «Следующее»</td></tr>
<tr><th><code>[+previous+]</code></th><td>Кнопка «Предыдущее»</td></tr>
<tr><th><code>[+splitter+]</code></th><td>Разделитель если всегда показывается 0</td></tr>
<tr><th><code>[+start+]</code></th><td>Номер первой показываемой страницы</td></tr>
<tr><th><code>[+urlStart+]</code></th><td>Номер текущей страницы, как показано в адресной строке (?start=)</td></tr>
<tr><th><code>[+stop+]</code></th><td>Номер последней показываемой страницы</td></tr>
<tr><th><code>[+total+]</code></th><td>Общее количество страниц</td></tr>
<tr><th><code>[+pages+]</code></th><td>Список страниц</td></tr>
<tr><th><code>[+currentPage+]</code></th><td>Номер показываемой текущей страницы</td></tr>
<tr><th><code>[+perPage+]</code></th><td>Отображаемых элементов на странице (равно display)</td></tr>
<tr><th><code>[+totalPages+]</code></th><td>Общее количество страниц</td></tr>
<tr><th><code>[+ditto_pagination_set+]</code></th><td>1 если paginate включено</td></tr>
<tr><th><code>[+item[x]+]</code></th><td>Сформированный вывод индивидуального документа</td></tr>
</tbody>
</table>
</div>
</div>
<h3 class="sub-header text-bold"><a id="941"></a>Плейсхолдеры summary</h3>
<div class="well bordered-left bordered-blue">
<div class="flip-scroll"><table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Параметр</th><th>Описание</th></tr>
</thead>
<tbody>
<tr><th><code>[+summary+]</code></th><td>Поле аннотация (введение) полностью, если указано, или начальная часть содержимого страницы</td></tr>
<tr><th><code>[+link+]</code></th><td>Ссылка на полный текст. Текст ссылки установливается параметром &trunctText. По умолчанию из файла языка Ditto</td></tr>
</tbody>
</table>
</div>
</div>
<h3 class="sub-header text-bold"><a id="942"></a>Плейсхолдеры tagging</h3>
<div class="well bordered-left bordered-blue">
<div class="flip-scroll"><table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Параметр</th><th>Описание</th></tr>
</thead>
<tbody>
<tr><th><code>[+tagLinks+]</code></th><td>Список тэгов, связанных с документом, разделенных &tagDelimiter</td></tr>
<tr><th><code>[+tags+]</code></th><td>На странице, содержащей результат: теги, используемые для фильтрации отображаемых документов</td></tr>
</tbody>
</table>
</div>
</div>
<h3 class="sub-header text-bold"><a id="943"></a>Плейсхолдеры dateFilter</h3>
<div class="well bordered-left bordered-blue">
<div class="flip-scroll"><table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Параметр</th><th>Описание</th></tr>
</thead>
<tbody>
<tr><th><code>[+year+]</code></th><td>Год для фильтра. Двух или четырех значное значение</td></tr>
<tr><th><code>[+month+]</code></th><td>Месяц для фильтра</td></tr>
<tr><th><code>[+day+]</code></th><td>День для фильтра</td></tr>
<tr><th><code>[+month_numeric+]</code></th><td>Численное значение месяца</td></tr>
</tbody>
</table>
</div>
</div>