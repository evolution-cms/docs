
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Breadcrumbs: Шаблоны</h2>

<pre class="brush: php;">
$templates = array(
	'defaultString' => array(
		'crumb' => '[+crumb+]',
		'separator' => ' &raquo; ',
		'crumbContainer' => '<span class="[+crumbBoxClass+]">[+crumbs+]</span>',
		'lastCrumbWrapper' => '<span class="[+lastCrumbClass+]">[+lastCrumbSpanA+]</span>',
		'firstCrumbWrapper' => '<span class="[+firstCrumbClass+]">[+firstCrumbSpanA+]</span>'
	),
	'defaultList' => array(
		'crumb' => '<li>[+crumb+]</li>',
		'separator' => '',
		'crumbContainer' => '<ul class="[+crumbBoxClass+]">[+crumbs+]</ul>',
		'lastCrumbWrapper' => '<span class="[+lastCrumbClass+]">[+lastCrumbSpanA+]</span>',
		'firstCrumbWrapper' => '<span class="[+firstCrumbClass+]">[+firstCrumbSpanA+]</span>'
	),
);
</pre>