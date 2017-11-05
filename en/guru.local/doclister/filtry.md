
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: Фильтры</h2>

<p>В комплекте следующие фильтры:</p>
<ul>
<li>content - для фильтрации по полям таблицы site_content, можно заменить параметром addWhereList;</li>
<li>tv - для фильтрации по TV-параметрам;</li>
<li>tvd - для фильтрации по TV-параметрам с учетом значений по умолчанию;</li>
<li>private - для фильтрации документов с учетом прав доступа.</li>
</ul>
<h3>Пример Построение фильтра</h3>
<pre class="brush: html;">
OR(AND(filter:field:operator:value;filter2:field:operator:value);(...))
</pre>
<h3>Операторы</h3>
<h3 class="sub-header text-bold">=, eq, is</h3>
<p>Равно.</p>
<h3 class="sub-header text-bold">!=, no, isnot</h3>
<p>Не равно.</p>
<h3 class="sub-header text-bold">&gt;, gt</h3>
<p>Больше.</p>
<h3 class="sub-header text-bold">&lt;, lt</h3>
<p>Меньше.</p>
<h3 class="sub-header text-bold">&lt;=, elt</h3>
<p>Меньше или равно.</p>
<h3 class="sub-header text-bold">&gt;=, egt</h3>
<p>Больше или равно.</p>
<h3 class="sub-header text-bold">%, like</h3>
<p>Содержит строку.</p>
<h3 class="sub-header text-bold">like-r</h3>
<p>Заканчивается строкой.</p>
<h3 class="sub-header text-bold">like-l</h3>
<p>Начинается строкой.</p>
<h3 class="sub-header text-bold">regexp</h3>
<p>Выборка с использованием регулярных выражений .</p>
<h3 class="sub-header text-bold">against</h3>
<p>Полнотекстовый поиск.
Для примера:</p>
<pre class="brush: html;">
[[DocLister? &amp;filters=`AND(content:pagetitle,description,content,introtext:against:искомая строка)`]]
</pre>
<p>Из данного примера предполагается, что в базе данных имеется FULLTEXT индекс по полям pagetitle,description,content,introtext</p>
<h3 class="sub-header text-bold">containsOne</h3>
<p>Поиск любого слова или его части в тексте при помощи LIKE. Для примера:</p>
<pre class="brush: html;">
[[DocLister? &amp;filters=`AND(content:content:containsOne:когда,наступит,мир)`]]
</pre>
<p>Будет построен SQL запрос вида</p>
<pre class="brush: sql;">
(content LIKE '%когда%' OR content LIKE '%наступит%' OR content LIKE '%мир%')
</pre>
<p>Т.е. в конечном счете из базы будут выбраны документы в тексте которых используется слова "когда" или "наступит" или "мир".</p>
<p>Из примера вызова видно, что слова разделены запятой. Это поведение можно переопределить параметром <span class="text-bold"><em>filter_delimiter</em></span>.</p>
<h3 class="sub-header text-bold">in</h3>
<p>Входит в множество.</p>
<h3 class="sub-header text-bold">notin</h3>
<p>Не входит в множество.</p>
<p>Вот пример вызова с фильтрацией по цене от 0 до 300:</p>
<pre class="brush: html;">
[[DocLister? &amp;filters=`AND(tv:price:gt:0;tv:price:lt:300)`]]
</pre>
<p>А теперь тоже самое, только с учетом значений по умолчанию</p>
<pre class="brush: html;">
[[DocLister? &amp;filters=`AND(tvd:price:gt:0;tvd:price:lt:300)`]]
</pre>