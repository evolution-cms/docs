
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>multiTV: Переменная шаблона</h2>

<p>Все параметры задаются в конфигурационном файле в папке <span class="text-bold">configs</span> с тем же именем, как и переменная шаблона в виде PHP-массива <code>.config.inc.php</code> или JSON файла <code>.config.json</code> (файл JSON имеет приоритет перед PHP-массивом). </p>
<h3 class="sub-header text-bold">Параметр display</h3>
<p>Отображение полей ввода настраивается с помощью параметра <code>display</code></p>
<ul>
<li><code>horizontal</code> - горизонтальное расположение (пример event.config.inc.php)</li>
<li><code>vertical</code> - вертикальное расположение (пример images.config.inc.php)</li>
<li><code>single</code> - содержит только один элемент</li>
<li><code>datatable</code> - пример links.config.inc.php или multicontent.config.inc.php</li>
<li><code>dbtable</code> - пример dbtabledemo.config.json</li>
</ul>
<h3 class="sub-header text-bold">Параметр fields</h3>
<p>Поля ввода одного элемента списка определяются в параметре <code>fields</code></p>
<p>Эта переменная содержит массив имен полей и каждое имя поля содержит массив свойств поля.</p>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Поле</th><th>Описание</th><th>Значение по умолчанию</th></tr>
</thead>
<tbody>
<tr>
<td>caption</td>
<td>Заголовок (при horizontal) или лейбл (при vertical) для поля ввода</td>
<td>-</td>
</tr>
<tr>
<td>type</td>
<td>Тип поля ввода (используются все типы ввода MODX кроме url и richtext, добавлен thumb для отображения эскизов изображений)</td>
<td>text</td>
</tr>
<tr>
<td>elements</td>
<td>Для ввода возможных значений переменной, например, для выпадающего списка всех дочерних документов корневой папки сайта: <code>@SELECT `pagetitle`, `id` FROM `modx_site_content` WHERE parent = 0 ORDER BY `menuindex` ASC</code></td>
<td>-</td>
</tr>
<tr>
<td>default</td>
<td>Значение по умолчанию. Это значение может содержать вычисления. Может содержать два плэйсхолдера: <code>[+i+]</code> - автоматически увеличивающийся индекс, <code>[+alias+]</code> - псевдоним редактируемого документа.</td>
<td>-</td>
</tr>
<tr>
<td>thumbof</td>
<td>Имя переменной для миниатюры изоображения. Миниатюра будет отображена в этой области.</td>
<td>-</td>
</tr>
<tr>
<td>width</td>
<td>Ширина поля ввода (только если тип отображения полей horizontal)</td>
<td>100</td>
</tr>
</tbody>
</table>
</div>
<p><span class="text-bold">Поддерживаемые типы полей:</span> text, rawtext, email, number, textareamini, textarea, rawtextarea, htmlarea, date, dropdown, listbox, listbox-multiple, checkbox, option, image, file</p>
<h3 class="sub-header text-bold">Параметр columns</h3>
<p>В режимах datatable и dbtable могут быть определены в качестве ключа параметры columns. Этот ключ содержит массив параметров столбцов. Каждый столбец содержит массив свойств. Если свойство не задано, в качестве ключа используется <code>fields</code>.</p>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Свойство</th><th>Описание</th><th>Значение по умолчанию</th></tr>
</thead>
<tbody>
<tr>
<td>fieldname</td>
<td><b>(обязательный параметр)</b> Имя свойства</td>
<td>-</td>
</tr>
<tr>
<td>caption</td>
<td>Заголовок столбца</td>
<td>caption параметра fields</td>
</tr>
<tr>
<td>width</td>
<td>Ширина столбца</td>
<td>width параметра fields</td>
</tr>
<tr>
<td>render</td>
<td>Enable rengering of the column content with this PHx capable strin</td>
<td>-</td>
</tr>
<tr>
<td>sortable</td>
<td>Включить сортировку по этой колонке, нажав на Заголовок столбца в datatable или dbtable режиме. Активно только при отключенной сортировке в других опциях</td>
<td>true</td>
</tr>
</tbody>
</table>
</div>
<h3 class="sub-header text-bold">Редактирование слоев</h3>
<p>В режимах datatable и dbtable редактирование содержимого слоя может быть определено в ключе <code>form</code>. Этот ключ содержит массив параметров вкладки form.</p>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Свойство</th><th>Описание</th><th>Значение по умолчанию</th></tr>
</thead>
<tbody>
<tr>
<td>caption</td>
<td><b>(обязательный параметр)</b> Заголовок вкладки form</td>
<td>-</td>
</tr>
<tr>
<td>content</td>
<td><b>(обязательный параметр)</b> Ассоциативный массив параметров полей</td>
<td>caption параметра fields</td>
</tr>
</tbody>
</table>
</div>
<p>Each form tab setting contains an associative array of field properties (the key contains the fieldname in <code>fields</code>). If a field property is not set, the field property in <code>fields</code> is used.</p>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Свойство</th><th>Описание</th><th>Значение по умолчанию</th></tr>
</thead>
<tbody>
<tr>
<td>caption</td>
<td>Заголовок для input</td>
<td>caption параметра fields</td>
</tr>
</tbody>
</table>
</div>
<h3 class="sub-header text-bold">Шаблоны по умолчанию</h3>
<p>Шаблоны для сниппета <span class="text-bold">multiTV</span> используемые по умолчанию, могут быть определены в параметре <code>templates</code></p>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Свойство</th><th>Описание</th><th>Значение по умолчанию</th></tr>
</thead>
<tbody>
<tr>
<td>rowTpl</td>
<td>Шаблон вывода строки. Может быть изменен в вызове сниппета</td>
<td>-</td>
</tr>
<tr>
<td>outerTpl</td>
<td>Шаблон вывода внешнего блока. Может быть изменен в вызове сниппета</td>
<td>-</td>
</tr>
</tbody>
</table>
</div>
<h3 class="sub-header text-bold">Другие опции</h3>
<p>Другие опции могут быть определены в параметре <code>configuration</code></p>
<div class="flip-scroll">
<table class="table table-bordered table-vcenter flip-content">
<thead class="flip-content bordered-palegreen">
<tr><th>Свойство</th><th>Описание</th><th>Значение по умолчанию</th></tr>
</thead>
<tbody>
<tr>
<td>enablePaste</td>
<td>multiTV может содержать ссылку для вставки данных. В этом окне вы могли бы вставить Word/HTML таблицы данных из буфера обмена, Google Docs таблицы и данные в формате csv.</td>
<td>true</td>
</tr>
<tr>
<td>enableClear</td>
<td>Ссылка на удаление всех элементов multiTV</td>
<td>true</td>
</tr>
<tr>
<td>csvseparator</td>
<td>Разделитель столбцов при вставке данных csv. Каждая строка должна начинаться с новой строки.</td>
<td>,</td>
</tr>
<tr>
<td>radioTabs</td>
<td>Tabs in the datatable editing layer are displayed as radio buttons. The button state is saved in fieldTab key of each multiTV row.</td>
<td>false</td>
</tr>
<tr>
<td>sorting</td>
<td>Включить сортировку по щелчку на заголовке столбца в datatable или dbtable режиме.</td>
<td>false</td>
</tr>
<tr>
<td>hideHeader</td>
<td>Скрыть заголовок в datatable или dbtable режиме.</td>
<td>,</td>
</tr>
</tbody>
</table>
</div>
<p>Смотрите файл конфигурации для TV-параметра <code>multidemo</code> для всех используемых вертикальных настроек и <code>multicontent</code> для всех используемых datatable настроек.</p>