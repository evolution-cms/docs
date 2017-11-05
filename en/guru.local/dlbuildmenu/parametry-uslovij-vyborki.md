
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLBuildMenu: Параметры условий выборки</h2>

<h3 class="sub-header text-bold">&amp;addWhereList</h3>
<p>Условия выборки документов для всех уровней.</p>
<p>Возможные значения: задаются как в DocLister (по правилам MySQL для условия WHERE).</p>
<p>Значение по умолчанию: <code>c.hidemenu = 0</code></p>
<h3 class="sub-header text-bold">&amp;addWhereListN</h3>
<p>Условия выборки документов N-го уровня, для соответствующих уровней &amp;addWhereListN имеет приоритет над &amp;addWhereList.</p>
<p>Возможные значения: задаются по правилам MySQL для условия WHERE.</p>
<p>Значение по умолчанию: нет</p>
<p>Примечание: Если &amp;addWhereListN не задан, для всех уровней используется &amp;addWhereList.</p>