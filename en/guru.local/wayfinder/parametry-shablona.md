
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Wayfinder: Параметры Шаблона</h2>

<div class="panel-group">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse765"><span class="text-bold">&amp;activeParentRowTpl</span> - Шаблон родителей текущего пункта меню</a></h4>
</div>
<div id="collapse765" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;activeParentRowTpl=`activeParentRowTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse766"><span class="text-bold">&amp;categoryFoldersTpl</span> - Шаблон вывода категории</a></h4>
</div>
<div id="collapse766" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Категория определяется установкой шаблона <code>blank</code> или атрибутом ссылки <code>rel="category"</code>.<br>
Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;categoryFoldersTpl=`categoryFoldersTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse779"><span class="text-bold">&amp;cssTpl</span> - Имя чанка содержащего CSS</a></h4>
</div>
<div id="collapse779" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> <br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;cssTpl=`cssTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse761"><span class="text-bold">&amp;hereTpl</span> - Шаблон текущего пункта</a></h4>
</div>
<div id="collapse761" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;span&gt;[+wf.linktext+]&lt;/span&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;hereTpl=`hereTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse764"><span class="text-bold">&amp;innerHereTpl</span> - Шаблон текущего пункта подменю</a></h4>
</div>
<div id="collapse764" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;span&gt;[+wf.linktext+]&lt;/span&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;innerHereTpl=`innerHereTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse763"><span class="text-bold">&amp;innerRowTpl</span> - Шаблон для пункта подменю</a></h4>
</div>
<div id="collapse763" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;innerRowTpl=`innerRowTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse762"><span class="text-bold">&amp;innerTpl</span> - Шаблон для подпапок</a></h4>
</div>
<div id="collapse762" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.wrapper+] - место где будет выводиться содержимое меню. <br>
<b>Пример шаблона:</b> <code>&lt;ul [+wf.classes+]&gt;[+wf.wrapper+]&lt;/ul&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;innerTpl=`innerTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse780"><span class="text-bold">&amp;jsTpl</span> - Имя чанка содержащего JavaScript</a></h4>
</div>
<div id="collapse780" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> <br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;jsTpl=`jsTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse856"><span class="text-bold">&amp;lastRowTpl</span> - Шаблон последнего пункта меню (v 2.0.3)</a></h4>
</div>
<div id="collapse856" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> rowTpl<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;lastRowTpl=`lastRowTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse130"><span class="text-bold">&amp;outerTpl</span> - Шаблон контейнера меню</a></h4>
</div>
<div id="collapse130" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> <code>&lt;ul[+wf.classes+]&gt;[+wf.wrapper+]&lt;/ul&gt;</code><br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.wrapper+] - место где будет выводиться содержимое меню. <br>
<b>Пример шаблона:</b> <code>&lt;ul id="topnav" [+wf.classes+]&gt;[+wf.wrapper+]&lt;/ul&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;outerTpl=`outerTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse759"><span class="text-bold">&amp;parentRowHereTpl</span> - Шаблон вывода активного документа-контейнера</a></h4>
</div>
<div id="collapse759" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]»&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;parentRowHereTpl=`parentRowHereTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse760"><span class="text-bold">&amp;parentRowTpl</span> - Шаблон документа контейнера</a></h4>
</div>
<div id="collapse760" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]»&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;parentRowTpl=`parentRowTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse758"><span class="text-bold">&amp;rowTpl</span> - Шаблон пункта меню</a></h4>
</div>
<div id="collapse758" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> <code>&lt;li[+wf.id+][+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]" [+wf.attributes+]&gt;[+wf.linktext+]&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Примечание:</span> Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;li[+wf.classes+]&gt;&lt;a href="[+wf.link+]" title="[+wf.title+]"&gt;[+wf.linktext+]&lt;/a&gt;[+wf.wrapper+]&lt;/li&gt;</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;rowTpl=`rowTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a class="accordion-toggle" data-toggle="collapse" data-parent="#accordion" href="#collapse767"><span class="text-bold">&amp;startItemTpl</span> - Шаблон ссылки на начальную папку, указанную в startId</a></h4>
</div>
<div id="collapse767" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> <code>&lt;h2[+wf.id+][+wf.classes+]&gt;[+wf.linktext+]&lt;/h2&gt;[+wf.wrapper+]</code><br>
<span class="text-bold">Примечание:</span> Используется при &amp;displayStart=`1`<br>
Возможные плэйсхолдеры:<br>
[+wf.classes+] - место для указания используемого CSS-класса (включает class=" ")<br>
[+wf.classnames+] - содержит только название CSS-класса (не включает class=" ")<br>
[+wf.link+] - адрес (href) для ссылки<br>
[+wf.title+] - текст для title ссылки<br>
[+wf.linktext+] - текст названия ссылки<br>
[+wf.wrapper+] - место для вывода подменю<br>
[+wf.id+] - вывод уникального идентификатора (id)<br>
[+wf.attributes+] - вывод дополнительных атрибутов ссылки<br>
[+wf.docid+] - идентификатор документа для текущего элемента<br>
[+wf.subitemcount+] -количество элементов в папке<br>
[+wf.description+] - выводит значения поля описания<br>
[+wf.introtext+] - выводит значения поля интротекста <br>
<b>Пример шаблона:</b> <code>&lt;h2&gt;[+wf.linktext+]&lt;/h2&gt;[+wf.wrapper+]</code><br>
<span class="text-bold">Пример:</span>
<pre class="brush: html;">&amp;startItemTpl=`startItemTpl`</pre>
</div>
</div>
</div>
</div>