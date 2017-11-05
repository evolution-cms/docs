
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLBuildMenu: Параметры сортировки</h2>

<h3 class="sub-header text-bold">&amp;orderBy</h3>
<p>Условия сортировки документов всех уровней</p>
<p>Возможные значения: задаются как в DocLister (по правилам MySQL для ORDER BY).</p>
<p>Значение по умолчанию: menuindex ASC, id ASC</p>
<h3 class="sub-header text-bold">&amp;orderByN</h3>
<p>Условия сортировки документов N-го уровня вложенности, для соответствующих уровней &amp;orderBy имеет приоритет над &amp;orderBy.</p>
<p>Возможные значения: задаются по правилам MySQL для ORDER BY.</p>
<p>Значение по умолчанию: нет</p>
<p>Примечание: Если &amp;orderByN не задан, для всех уровней используется &amp;orderBy.</p>