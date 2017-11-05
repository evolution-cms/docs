
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLMenu: Шаблоны</h2>

<h3 class="sub-header text-bold">outerTpl</h3>
<p>Обертка всего меню.</p>
<p>Возможные значения - имя шаблона, указанное по правилам задания шаблонов в DocLister.</p>
<p>Значение по умолчанию:</p>
<pre class="brush: html;">@CODE:&lt;ul[+classes+]&gt;[+wrap+]&lt;/ul&gt;</pre>
<h3 class="sub-header text-bold">rowTpl, rowHereTpl</h3>
<p>Шаблон для вывода пункта меню первого уровня без потомков. Для текущего документа может быть задан шаблон rowHereTpl.</p>
<p>Возможные значения - имя шаблона, указанное по правилам задания шаблонов в DocLister.</p>
<p>Значение по умолчанию:</p>
<pre class="brush: html;">@CODE:&lt;li[+classes+]&gt;&lt;a href="[+url+]"&gt;[+title+]&lt;/a&gt;&lt;/li&gt;</pre>
<h3 class="sub-header text-bold">parentRowTpl, parentRowHereTpl, parentRowActiveTpl</h3>
<p>Шаблон для вывода документа, у которого есть потомки. Для текущего документа может быть задан шаблон parentRowHereTpl, для активного - parentRowActiveTpl.</p>
<p>Возможные значения - имя шаблона, указанное по правилам задания шаблонов в DocLister.</p>
<p>Значение по умолчанию:</p>
<pre class="brush: html;">@CODE:&lt;li[+classes+]&gt;&lt;a href="[+url+]"&gt;[+title+]&lt;/a&gt;[+wrap+]&lt;/li&gt;</pre>
<h3 class="sub-header text-bold">innerTpl</h3>
<p>Обертка блока дочерних документов.</p>
<p>Возможные значения - имя шаблона, указанное по правилам задания шаблонов в DocLister.</p>
<p>Значение по умолчанию - значение параметра outerTpl.</p>
<h3 class="sub-header text-bold">innerRowTpl, innerRowHereTpl</h3>
<p>Шаблон для вывода дочернего документа. Для текущего документа может быть задан шаблон innerRowHereTpl.</p>
<p>Возможные значения - имя шаблона, указанное по правилам задания шаблонов в DocLister.</p>
<p>Значение по умолчанию - значение параметра rowTpl.</p>
<h3 class="sub-header text-bold">categoryFolderTpl</h3>
<p>Шаблон для вывода категории (документа с полем isfolder=1 и шаблоном _blank или значением поля link_attributes содержащим слово category).</p>
<p>Возможные значения - имя шаблона, указанное по правилам задания шаблонов в DocLister.</p>
<p>Значение по умолчанию - значение параметра parentRowTpl.</p>