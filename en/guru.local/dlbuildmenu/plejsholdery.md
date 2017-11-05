
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLBuildMenu: Плейсхолдеры</h2>

<h2 class="page-header">Основные плейсхолдеры</h2>
<h3 class="sub-header text-bold">[+dl.wrap+]</h3>
<p>С его помощью в шаблон-обёртку подставляется сформированный HTML-код меню/субменю для вывода.</p>
<p>Примечание: используется только для шаблонов-обёрток &amp;TplMainOwner, &amp;TplSubOwner и &amp;TplOwnerN.</p>
<h3 class="sub-header text-bold">[+dl.submenu+]</h3>
<p>Сюда подставляется сформированный HTML-код субменю вместе с шаблоном-обёрткой.</p>
<p>Примечание: используется для шаблонов пункта меню, как не текущих, так и текущих.</p>
<h3 class="sub-header text-bold">[+dl.currentDepth+]</h3>
<p>Текущий уровень вложенности (текущая глубина).</p>
<p>Примечание: обратите внимание, что отсчёт текущего уровня вложенности начинается с 1.</p>
<h3 class="sub-header text-bold">[+dl.class+]</h3>
<p>Работает так же, как и в DocLister, автоматически добавляя классы last, first, current, even, odd соответственно для последнего, первого, текущего, четного и нечетного пункта. Кроме того, добавляет класс из параметра &amp;activeClass для текущего элемента и его родительских элементов всех уровней.</p>
<p>Примечание: классы last, first, current, even, odd и active могут быть переопределены в параметрах &amp;lastClass, &amp;currentClass, &amp;firstClass, &amp;evenClass, &amp;oddClass и &amp;activeClass.</p>
<h3 class="sub-header text-bold">[+url+]</h3>
<p>УРЛ ресурса аналогично ДокЛистеру.</p>
<h3 class="sub-header text-bold">[+e.title+]</h3>
<p>Экранированное значение menutitle или pagetitle (если menutitle пуст) аналогично Доклистеру.</p>
<h3 class="sub-header text-bold">[+id+]</h3>
<p>ID ресурса аналогично ДокЛистеру.</p>
<h2 class="page-header">Другие плейсхолдеры из DocLister</h2>
<p>Вы можете использовать и другие плейсхолдеры ДокЛистера, устанавливаемые контроллером site_content и различными экстендерами.</p>
<p>Например, плейсхолдеры вида [+tvPrefix.tvName+], плейсхолдеры экранированных значений вида [+e.fieldName+] (где fieldName - это имя поля таблицы site_content), [+date+] и другие (см. документацию к DocLister).</p>