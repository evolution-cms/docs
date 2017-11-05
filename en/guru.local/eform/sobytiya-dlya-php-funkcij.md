
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>eForm: События для PHP функций</h2>

<div class="panel-group accordion">
<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="898"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse898"><span class="text-bold">&eFormOnBeforeMailSent</span> - Событие после проверки формы и перед отправкой отчета</a></h4>
</div>
<div id="collapse898" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> функция<br>
<span class="text-bold">Значение по умолчанию:</span> пусто<br>
<span class="text-bold">Примечание:</span> Определяет название функции. Эта функция будет запущена после того как форма будет проверена и перед отчетом и сообщением для пользователя, а также отправкой любых сообщений. Функции передаются следующие параметры: &$fields - массив полей и значений переменных.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&eFormOnBeforeMailSent=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="899"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse899"><span class="text-bold">&eFormOnMailSent</span> - Событие после отправки писем</a></h4>
</div>
<div id="collapse899" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> функция<br>
<span class="text-bold">Значение по умолчанию:</span> пусто<br>
<span class="text-bold">Примечание:</span> Определяет название функции. Эта функция будет запущена после обработки всех шаблонов и любое сообщение будет послано. Функции передаются следующие параметры: &$fields - массив полей и значений переменных.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&eFormOnMailSent=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="900"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse900"><span class="text-bold">&eformOnBeforeFormParse</span> - Событие после загруки шаблона</a></h4>
</div>
<div id="collapse900" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> функция<br>
<span class="text-bold">Значение по умолчанию:</span> пусто<br>
<span class="text-bold">Примечание:</span> Определяет название функции. Эта функция будет запущена после загрузки шаблонов и определения идентификатора формы. Функции передаются следующие параметры: <br>&$fields - массив полей и значений переменных.<br>&$templates - массив всех шаблонов с индексами 'tpl','report','thankyou' и 'autotext'. Последние три будут иметь значение только после отправки формы.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&eformOnBeforeFormParse=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="901"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse901"><span class="text-bold">&eFormOnBeforeFormMerge</span> - Событие до определения плэйсхолдеров шаблона</a></h4>
</div>
<div id="collapse901" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> функция<br>
<span class="text-bold">Значение по умолчанию:</span> пусто<br>
<span class="text-bold">Примечание:</span> Определяет название функции. Эта функция будет запущена только при показе форм и до определения всех переменных шаблона. Функции передаются следующие параметры: &$fields - массив полей и значений переменных.<br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&eFormOnBeforeFormMerge=``</pre>
</div>
</div>
</div>

<div class="panel panel-default">
<div class="panel-heading">
<h4 class="panel-title"><a id="902"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse902"><span class="text-bold">&eFormOnValidate</span> - Событие после проверки данных формы</a></h4>
</div>
<div id="collapse902" class="panel-collapse collapse">
<div class="panel-body">
<span class="text-bold">Формат:</span> функция<br>
<span class="text-bold">Значение по умолчанию:</span> пусто<br>
<span class="text-bold">Примечание:</span> Определяет название функции. Эта функция будет запущена после проверки данных формы. Это можно использовать для определения собственного алгоритма обработки. Функции передаются следующие параметры:
<pre class="brush: html;">&$fields - массив полей и значений переменных
&$vMsg - числовой массив ошибок проверки данных формы
&$rMsg - числовой массив пропущенных обязательных полей
&$rClass - ассоциативный массив имен полей и классов
</pre><br>
<p><span class="text-bold">Пример:</span></p>
<pre class="brush: html;">&eFormOnValidate=``</pre>
</div>
</div>
</div>
</div>