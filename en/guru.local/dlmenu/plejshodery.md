
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLMenu: Плейсходеры</h2>

<ul>
<li><span class="text-bold">[+wrap+]</span> - вывод дочерних документов (в api-режиме - children); если значение плейсхолдера - массив, то он преобразуется в строку с применением соответствующих шаблонов, если строка - остается без изменений;</li>
<li><span class="text-bold">[+classNames+]</span> - список классов, доступных в шаблоне (только имена); </li>
<li><span class="text-bold">[+classes+]</span> - список классов, доступных в шаблоне (включая class=" ");</li>
<li><span class="text-bold">[+maxLevel+]</span> - если установлен, то указывает на то, что документ находится в самом низу ветки, к которой принадлежит;</li>
<li><span class="text-bold">[+iteration+]</span> - порядковый номер документа в группе;</li>
<li><span class="text-bold">[+here+]</span> - если установлен, то документ является текущим документов;</li>
<li><span class="text-bold">[+active+]</span> - если установлен, то документ является активным документов;</li>
<li><span class="text-bold">[+state+]</span> - если задан параметр hideSubMenus, то плейсхолдер содержит значение open для развернутой ветви и closed для свернутой;</li>
<li><span class="text-bold">[+title+]</span> - название документа, равно полю menutitle, если оно не пустое, или pagetitle;</li>
<li><span class="text-bold">[+url+]</span> - ссылка на документ;</li>
<li><span class="text-bold">[+count+]</span> - количество непосредственных потомков;</li>
<li><span class="text-bold">[+_renderRowTpl+]</span> - если установлен, то его значение будет использовано в качестве шаблона при выводе документов;</li>
<li><span class="text-bold">[+_renderOuterTpl+]</span> - если установлен, то его значение будет использовано в качестве шаблона при выводе обертки дочерних документов.</li>
</ul>
<p>Также доступны плейсхолдеры, устанавливаемые экстендером e, и плейсхолдеры отдельных классов: <span class="text-bold">[+oddClass+]</span>, <span class="text-bold">[+rowClass+]</span> и т.д.</p>