
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ListChild: Параметры</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="798"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse798"><span class="text-bold">&docid</span> - id папок (через запятую), дочерние документы которых необходимо отобразить</a></h4>
</div>
<div id="collapse798" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ID документов, разделенных запятой<br>
<span class="text-bold">Значение по умолчанию:</span> текущий документ<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&docid=`10,11,12`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="799"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse799"><span class="text-bold">&depth</span> - Глубина сканирования</a></h4>
</div>
<div id="collapse799" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&depth=`2`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="800"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse800"><span class="text-bold">&published</span> - Выводить неопубликованные/опубликованные документы</a></h4>
</div>
<div id="collapse800" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&published=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="801"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse801"><span class="text-bold">&deleted</span> - Выводить неудаленные/удаленные документы</a></h4>
</div>
<div id="collapse801" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&deleted=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="802"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse802"><span class="text-bold">&where</span> - Дополнительные условия запроса в БД</a></h4>
</div>
<div id="collapse802" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> <br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Соответствует where в MySQL <span class="alert alert-error">Во фронтенде необходимо заменять все "=" на "@eq".</span><br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&where=`isfolder @eq 1 and hidemenu @eq 0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="803"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse803"><span class="text-bold">&amp;param</span> - Параметр для выборки</a></h4>
</div>
<div id="collapse803" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле документа<br>
<span class="text-bold">Значение по умолчанию:</span> pagetitle<br>
<span class="text-bold">Примечание:</span> Любое поле документа, кроме TV-параметров<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&amp;param=`longtitle`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="804"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse804"><span class="text-bold">&value</span> - Значение параметра для выборки</a></h4>
</div>
<div id="collapse804" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле документа<br>
<span class="text-bold">Значение по умолчанию:</span> id<br>
<span class="text-bold">Примечание:</span> Любое поле документа, кроме TV-параметров<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&value=`pagetitle`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="805"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse805"><span class="text-bold">&sort</span> - Поле для сортировки</a></h4>
</div>
<div id="collapse805" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле документа<br>
<span class="text-bold">Значение по умолчанию:</span> &param<br>
<span class="text-bold">Примечание:</span> Значение по умолчанию - &param (параметр для выборки)<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&sort=`menuindex`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="806"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse806"><span class="text-bold">&dir</span> - Направление сортировки</a></h4>
</div>
<div id="collapse806" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> ASC | DESC<br>
<span class="text-bold">Значение по умолчанию:</span> ASC<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&dir=`DESC`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="807"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse807"><span class="text-bold">&limit</span> - Максимальное количество документов</a></h4>
</div>
<div id="collapse807" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> число<br>
<span class="text-bold">Значение по умолчанию:</span> без ограничения<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&limit=`10`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="808"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse808"><span class="text-bold">&name</span> - Значение атрибута name тега select или input (frontend)</a></h4>
</div>
<div id="collapse808" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> <br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Только для вызова во frontend. Используется для запоминания выбранных значений.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&name=`country`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="810"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse810"><span class="text-bold">&emptyfield</span> - Не добавлять/добавлять пустое поле в начале списка</a></h4>
</div>
<div id="collapse810" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 1<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&emptyfield=`0`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="811"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse811"><span class="text-bold">&selectedValue</span> - Значение для плейсхолдера [+selected+] (frontend)</a></h4>
</div>
<div id="collapse811" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> selected | selected="selected" | checked | checked="checked"<br>
<span class="text-bold">Значение по умолчанию:</span> selected="selected"<br>
<span class="text-bold">Примечание:</span> Только для вызова во frontend.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&selectedValue=`checked`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="812"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse812"><span class="text-bold">&tpl</span> - Имя чанка с шаблоном (frontend)</a></h4>
</div>
<div id="collapse812" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> имя чанка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> Только для вызова во frontend.
<br>Доступные плейсхолдеры: 
<br>[+param+] - название параметра для выборки (см. &param);
<br>[+value+] - значение параметра для выборки (см. &value);
<br>[+desc+] - краткое описание (см. &desc);
<br>[+selected+] - место для вывода атрибута selected для запоминания выбранных значений (см. &selectedValue);
<br>Шаблон, используемый по умолчанию:
<br>&lt;option value="[+value+]" [+selected+]&gt;[+param+]&lt;/option&gt;
<br>Пример шаблона для переключателей:
<br>&lt;input type="radio" name="country" value="[+value+]" [+selected+]&gt; [+param+]<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&tpl=`countryTpl`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="814"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse814"><span class="text-bold">&count</span> - Вывод количества найденных документов</a></h4>
</div>
<div id="collapse814" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> 0 | 1<br>
<span class="text-bold">Значение по умолчанию:</span> 0<br>
<span class="text-bold">Примечание:</span> <br>0 - работа в обычном режиме. По умолчанию.
<br>1 - вывод количества найденных документов
<br>При использовании параметра count со значением 1, параметры tpl, name, selectedValue, value и param не используются.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&count=`1`</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="815"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse815"><span class="text-bold">&separator</span> - Разделитель между выводимыми документами</a></h4>
</div>
<div id="collapse815" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> строка<br>
<span class="text-bold">Значение по умолчанию:</span> нет<br>
<span class="text-bold">Примечание:</span> <br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&separator=`, `</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="816"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse816"><span class="text-bold">&desc</span> - Параметр для вывода описания к документу</a></h4>
</div>
<div id="collapse816" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> поле документа<br>
<span class="text-bold">Значение по умолчанию:</span> introtext<br>
<span class="text-bold">Примечание:</span> Любое поле документа, кроме TV-параметров.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&desc=`description`</pre>
</div>
</div>
</div>
</div>