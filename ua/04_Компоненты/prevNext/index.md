
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Сніпет Навігація по сусідніх документах Modx Evo </h3>
Сніпет виведення сусідніх документів в MODX Evolution. Наприклад, посилання «Наступна стаття», «Попередня стаття», «Попередній товар», «Наступний товар».
<h2 class="page-header">Варіант 1</h2>
<p>На багатьох сайтах після тексту статті часто можна зустріти блок посилань на інші матеріали сайту. Наприклад, посилання «Наступна стаття», «Попередня стаття». Також на сторінці товару, крім самого товару, можна побачити посилання на сусідні товари з тієї ж категорії.</p>
<p>У Ditto, як і у Wayfinder, я такої можливості не знайшов. Тому написав простий сніпет і вирішив поділитися їм тут. Сподіваюся комусь він стане в нагоді. Сніпет, як і було сказано вище, дуже простий - відмінний приклад для тих, хто тільки починає писати свої рішення для MODX. У коді безліч коментарів, так що проблем з розумінням виникнути не повинно.</p>
<p>Сніпету можна передавати 4 параметра:</p>
<ul>
<li><b>&tpl</b> – чанк-шаблон для виведення списку посилань (обов'язковий параметр)</li>
<li><b>&prevDocs</b> – кількість документів з меншим ID (необов'язковий параметр)</li>
<li><b>&nextDocs</b> – кількість документів з великим ID (необов'язковий параметр)</li>
<li><b>&sortRevert</b> – порядок сортування документів (необов'язковий параметр)</li>
</ul>
<p>Чанк-шаблон:</p>
<pre class="brush: html;">
&lt;a href="[~[+id+]~]">[+pagetitle+]&lt;/a&gt;
</pre>
<pre class="brush: php;">
&lt;?php
	// визначаємо значення за замовчуванням 
	$prevDocs = (isset($prevDocs)) ? $prevDocs : 2; // кількість сусідніх документів з меншим ID
	$nextDocs = (isset($nextDocs)) ? $nextDocs : 2; // кількість сусідніх документів з великим ID

	$sortRevert = (isset($sortRevert)) ? $sortRevert : 0; // параметр визначає порядок сортування

	// невелика перевірка наданих в параметрах значень
	$prevDocs = (int) $prevDocs;
	$nextDocs = (int) $nextDocs;
	$sortRevert = (int) $sortRevert;

	// отримуємо ID документа на якому відбувається виклик даного сніпета
	$id = $modx->documentIdentifier;

	// отримуємо ID документа-батька 
	$parent = $modx->documentObject['parent'];

	// перевірити чи не встановлено чанк
	if (!isset($tpl)) {
		echo "No chunk defined for siblings-snippet!";
		return;
	}

	// перевіряємо чи існує чанк
	if ($modx->parseChunk($tpl,array()) === NULL) {
		echo "Chunk specified, but not found!";
		return;
	}

	// отримуємо дані про сусідні документи з меншим ID
	$prev = $modx->db->makeArray($modx->db->select('id, pagetitle', 'modx_site_content', "id < {$id} and parent = {$parent} and published = 1", 'id DESC', $prevDocs));

	// отримуємо дані про сусідні документи з великим ID
	$next = $modx->db->makeArray($modx->db->select('id, pagetitle', 'modx_site_content', "id > {$id} and parent = {$parent} and published = 1", 'id ASC', $nextDocs));

	// об'єднуємо отримані даний в один масив
	$siblings = array_merge($next, $prev);

	// визначаємо масив в якому буде зберігатися індексований масив
	$indexed = array();

	// створюємо масив з індексами складеними з ID документів
	foreach ($siblings as $sibling) {
		$indexed[$sibling['id']] = $sibling;	
	}

	// сортуємо
	if ($sortRevert === 1) {
		rsort($indexed);
	} else {
		sort($indexed);
	}

	// формуємо html
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
<h2 class="page-header">Варіант 2</h2>
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
<p>Сніпет виводить результат в чанк prevnext, в якому використовуються два плейсхолдера:</p>
<p>[+prev+] [+next+]</p>
<p><a href="formlister/leksikony.html" title="Приклад сніпетів виведення сусідніх документів">Приклад сніпетів виведення сусідніх документів</a></p>
