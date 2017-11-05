
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Preview Next</h2>

<h2 class="page-header">Вариант 1</h2>
<p>На многих сайтах после текста статьи часто можно встретить блок ссылок на другие материалы сайта. Например, ссылки «Следующая статья», «Предыдущая статья». Также на странице товара, помимо самого товара, можно увидеть ссылки на соседние товары из той же категории.</p>
<p>У Ditto, как и у Wayfinder, я такой возможности не нашел. Поэтому написал простой сниппет и решил поделиться им здесь. Надеюсь кому-то он пригодится. Сниппет, как и было сказано выше, очень простой – отличный пример для тех, кто только начинает писать свои решения для MODX. В коде множество комментариев, так что проблем с пониманием возникнуть не должно.</p>
<p>Сниппету можно передавать 4 параметра:</p>
<ul>
<li><b>&tpl</b> – чанк-шаблон для вывода списка ссылок (обязательный параметр)</li>
<li><b>&prevDocs</b> – количество документов с меньшим ID (необязательный параметр)</li>
<li><b>&nextDocs</b> – количество документов с большим ID (необязательный параметр)</li>
<li><b>&sortRevert</b> – порядок сортировки документов (необязательный параметр)</li>
</ul>
<p>Чанк-шаблон:</p>
<pre class="brush: html;">
&lt;a href="[~[+id+]~]">[+pagetitle+]&lt;/a&gt;
</pre>
<pre class="brush: php;">
&lt;?php
	// определяем значения по умолчанию 
	$prevDocs = (isset($prevDocs)) ? $prevDocs : 2; // количество соседних документов с меньшим ID
	$nextDocs = (isset($nextDocs)) ? $nextDocs : 2; // количество соседних документов с большим ID

	$sortRevert = (isset($sortRevert)) ? $sortRevert : 0; // параметр определяющий порядок сортировки

	// небольшая проверка предоставленных в параметрах значений
	$prevDocs = (int) $prevDocs;
	$nextDocs = (int) $nextDocs;
	$sortRevert = (int) $sortRevert;

	// получаем ID документа на котором происходит вызов данного сниппета
	$id = $modx->documentIdentifier;

	// получаем ID документа-родителя 
	$parent = $modx->documentObject['parent'];

	// проверяем задан ли чанк
	if (!isset($tpl)) {
		echo "No chunk defined for siblings-snippet!";
		return;
	}

	// проверяем существует ли чанк
	if ($modx->parseChunk($tpl,array()) === NULL) {
		echo "Chunk specified, but not found!";
		return;
	}

	// получаем данные о соседних документах с меньшим ID
	$prev = $modx->db->makeArray($modx->db->select('id, pagetitle', 'modx_site_content', "id < {$id} and parent = {$parent} and published = 1", 'id DESC', $prevDocs));

	// получаем данные о соседних документах с большим ID
	$next = $modx->db->makeArray($modx->db->select('id, pagetitle', 'modx_site_content', "id > {$id} and parent = {$parent} and published = 1", 'id ASC', $nextDocs));

	// объединяем полученные данный в один массив
	$siblings = array_merge($next, $prev);

	// определяем массив в котором будет храниться индексированный массив
	$indexed = array();

	// создаем массив с индексами составленными из ID документов
	foreach ($siblings as $sibling) {
		$indexed[$sibling['id']] = $sibling;	
	}

	// сортируем
	if ($sortRevert === 1) {
		rsort($indexed);
	} else {
		sort($indexed);
	}

	// формируем html
	foreach($indexed as $sibling){
		$html .= $modx->parseChunk(
			$tpl,
			array(
				'id' => $sibling['id'],
				'pagetitle' => $sibling['pagetitle']		
			),
			'[+','+]'
		);
	}
	echo $html;
?>
</pre>
<hr>	
<h2 class="page-header">Вариант 2</h2>
<pre class="brush: php;">
&lt;?php
$ID = $modx->documentIdentifier;
$parentId = array_pop($modx->getParentIds($modx->documentIdentifier, 1));

$children = $modx->getActiveChildren($parentId, 'menuindex', 'ASC');

$i=0;
$key = false;
while(!$key && $i < count($children)){
	$key = array_search($ID, $children[$i]);
	$i++;
}

if(!empty($key) && count($children) > 1){
	$placeholders = array(
		'prev'=>($i-2 >= 0 ? '&lt;a href="'.$modx->makeUrl($children[$i-2]['id']).'"&gt;« назад&lt;/a&gt;' : ''),
		'next'=>($i < count($children) ? '&lt;a href="'.$modx->makeUrl($children[$i]['id']).'"&gt;вперед »&lt;/a&gt;' : '')
	);
	$output = $modx->parseChunk('prevnext', $placeholders, '[+', '+]');
}
return $output;
?&gt;
</pre>
<p>Сниппет выводит результат в чанк prevnext, в котором используются два плейсхолдера:</p>
<p>[+prev+] [+next+]</p>
<p><a href="formlister/leksikony.html" title="Пример Сниппета вывода соседних документов">Пример Сниппета вывода соседних документов</a></p>