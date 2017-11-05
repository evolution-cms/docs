
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>TvTagCloud: Примеры</h2>

<p>1. Создаем TV-пареметр tags со значением Text и указываем все шаблоны, для которых он будет применяться. Теперь на тех страницах, где должны быть теги, заполняем параметр tags, указывая теги через запятую.</p>
<p>2. Создаем новый документ в дереве ресурсов. В настройках страницы убираем галочки с «<span class="warning">Использовать HTML-редактор</span>», «<span class="warning">Доступен для поиска</span>» и «<span class="warning">Кэшируемый</span>», также убираем галочку с «<span class="warning">Показывать в меню</span>». Сохраняем ресурс, потом опять заходим в него и в содержимом ресурса помещаем такой вызов Ditto:</p>
<pre class="brush: html;">[!Ditto? &tagData=`tags` &tagDelimiter=`,` &parents=`0` &extenders=`tagging`!]</pre>
<p>3. В месте, где должно быть облако, помещаем вызов TvTagCloud:</p>
<pre class="brush: html;">[!TvTagCloud? &parent=`1` &landing=`22` &tvTags=`tags` &showCount=`1` &caseSensitive=`1`!]</pre>