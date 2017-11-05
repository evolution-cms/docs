
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLBuildMenu: Шаблоны</h2>

<p>Шаблоны DLBuildMenu задаются по правилам DL, то есть могут быть и инлайн-шаблонами, и именами чанков, или загружаться из файла, из документа MODx, из конфига, из глобального плейсхолдера.</p>
<h2 class="page-header">Шаблоны-обёртки</h2>
<h3 class="sub-header text-bold">&amp;TplMainOwner</h3>
<p>Основной шаблон-обертка (для уровня глубины 1).</p>
<div class="dark">Значение по умолчанию:</div>
<pre class="brush: html;">@CODE:&lt;ul id="nav" class="menu level-1"&gt;[+dl.wrap+]&lt;/ul&gt;</pre>
<p>Примечание: у вас должен быть задан шаблон &amp;TplMainOwner или &amp;TplOwner1, иначе будет использовано дефолтное значение шаблона &amp;TplMainOwner.</p>
<h3 class="sub-header text-bold">&amp;TplSubOwner</h3>
<p>Шаблон-обертка для вложенных уровней (для субменю).</p>
<div class="dark">Значение по умолчанию:</div>
<pre class="brush: html;">@CODE:&lt;ul class="sub-menu level-[+dl.currentDepth+]"&gt;[+dl.wrap+]&lt;/ul&gt;</pre>
<p>Примечание: для вывода N-уровневого меню у вас в дополнение к основной обёртке должен быть задан по крайней мере &amp;TplSubOwner и/или шаблоны &amp;TplOwnerN. Иначе будет использовано дефолтное значение &amp;TplSubOwner.</p>
<h3 class="sub-header text-bold">&amp;TplOwnerN</h3>
<p>Шаблон-обертка для субменю N-го уровня вложенности, для соответствующих уровней &amp;TplOwnerN имеет приоритет над &amp;TplMainOwner и &amp;TplSubOwner (см. Примечание).</p>
<p>Значение по умолчанию: нет</p>
<p>Примечание: Если заданы и &amp;TplOwner1, и &amp;TplMainOwner, то будет использован &amp;TplOwner1. Если заданы и &amp;TplOwner2 и &amp;TplSubOwner, то для уровня 2 будет использован &amp;TplOwner2, а для уровней начиная с 3-го – &amp;TplSubOwner.</p>

<h2 class="page-header">Шаблоны пункта меню</h2>
<h3 class="sub-header text-bold">&amp;TplOneItem</h3>
<p>Основной шаблон для каждого пункта меню всех уровней.</p>
<div class="dark">Значение по умолчанию:</div>
<pre class="brush: html;">
@CODE:&lt;li id="menu-item-[+id+]" class="menu-item [+dl.class+]"&gt;
 &lt;a href="[+url+]" title="[+e.title+]"&gt;[+title+]&lt;/a&gt;
 [+dl.submenu+]
&lt;/li&gt;
</pre>
<p>Примечание: у вас должны быть заданы все нужные вам шаблоны пунктов меню, по крайней мере &amp;TplOneItem. Иначе для пунктов, у которых шаблон не определен вами, будет использовано дефолтное значение &amp;TplOneItem.</p>
<h3 class="sub-header text-bold">&amp;TplDepthN</h3>
<p>Шаблон пункта меню вложенности N, для соответствующих уровней &amp;TplDepthN имеет приоритет над &amp;TplOneItem.</p>
<p>Значение по умолчанию: нет</p>
<p>Примечание: Например, если задан &amp;TplDepth2, он заменит собой шаблон &amp;TplOneItem на 3-м уровне вложенности.</p>

<h2 class="page-header">Шаблоны пункта без дочерних элементов</h2>
<h3 class="sub-header text-bold">&amp;noChildrenRowTPL</h3>
<p>Основной шаблон пункта меню без дочерних элементов для всех уровней.</p>
<p>Значение по умолчанию: нет</p>
<h3 class="sub-header text-bold">&amp;TplNoChildrenDepthN</h3>
<p>Шаблон пункта меню без дочерних элементов вложенности N. Для соответствующих уровней &amp;TplNoChildrenDepthN имеет приоритет над &amp;noChildrenRowTpl.</p>
<p>Значение по умолчанию: нет</p>
<p>Примечание: если для пункта меню не задан ни &amp;noChildrenRowTPL, ни &amp;TplNoChildrenDepthN, то в качестве шаблона для «бездетных» пунктов будет использован шаблон, заданный вами в других параметрах (&amp;TplOneItem или &amp;TplDepthN).</p>

<h2 class="page-header">Шаблоны текущего пункта</h2>
<h3 class="sub-header text-bold">&amp;TplCurrent</h3>
<p>Шаблон текущего пункта меню с дочерними, имеет приоритет перед всеми шаблонами пунктов меню, кроме &amp;TplCurrentN.</p>
<p>Значение по умолчанию: нет</p>
<h3 class="sub-header text-bold">&amp;TplCurrentN</h3>
<p>Шаблон текущего пункта меню вложенности N с дочерними , для N-го уровня шаблон &amp;TplCurrentN имеет приоритет перед всеми шаблонами пунктов меню с дочерними, включая &amp;TplCurrent.</p>
<p>Значение по умолчанию: нет.</p>
<h3 class="sub-header text-bold">&amp;TplCurrentNoChildrenN</h3>
<p>Шаблон текущего пункта меню без дочерних элементов, где N – номер уровня вложенности. Для уровня N имеет приоритет перед любыми другими шаблонами «бездетных» пунктов меню.</p>
<p>Значение по умолчанию: нет.</p>