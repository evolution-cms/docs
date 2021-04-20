
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Кількість переглядів сторінок для MODX Evolution </h3>
Кількість переглядів сторінок для  MODX Evolution.
<p>Встановлюємо лічильник кількості переглядів. Для цього нам потрібно буде створити додаткове поле в таблиці <span class="text-bold">modx_site_content</span> бази даних. Ось параметри нового поля – <span class="text-bold">count int(20) default = 0</span>.</p>
<p>Тепер створимо сніпет <span class="text-bold">inc</span>, який буде рахувати кількість відвідувань. Виклик сніпета inc потрібно встановити в самому верху шаблону матеріалів. Код сніпета:</p>
<pre class="brush: php;">
$table = $modx->getFullTableName("site_content");
$id = $modx->documentObject['id'];
$result = $modx->db->update("count=count+1", $table, "id=$id");
</pre>
<p>І нарешті, створюємо сніпет  <span class="text-bold">hits</span>, що відповідає за виведення кількості переглядів:</p>
<pre class="brush: php;">
$id = isset($id) ? $id : $modx->documentIdentifier;
return $modx->db->getValue($modx->db->select('count',$modx->getFullTableName('site_content'),'id='.$id));
</pre>
<p>Давайте розглянемо ще один спосіб підрахунку кількості переглядів. Даний спосіб має одну перевагу перед попереднім - його можна використовувати в шаблоні Ditto (<a rel="nofollow" href="http://rekill.ru/modx/snippet-kolichestvo-prosmotrov" target="_blank">вихідні матеріали</a>).</p>
<p>Отже, створимо TV-параметр <span class="text-bold">countViews</span>
з типом введення Text.</p>
<p>Далі створюємо сніпет  <span class="text-bold">countViews</span> з таким змістом:</p>
<pre class="brush: php;">
$type = isset($type) ? $type : 'output'; 
$table = $modx->getFullTableName('site_tmplvar_contentvalues'); 
$insert = false; 
$lock = ($lock == '1') ? true : false; 
$_SESSION['countViews'] = is_array($_SESSION['countViews']) ? $_SESSION['countViews'] : array(); 
$countViews = (isset($_SESSION['countViews'][$id]) && $_SESSION['countViews'][$id] === true) ? true : false; 
$usertype = isset($_SESSION['usertype']) ? $_SESSION['usertype'] : 'user'; 
switch($type) { 
	case 'output': 
		$count = $modx->getTemplateVar('countViews', '*', $id); 
		echo ($count['value'] == '' ? '0' : $count['value']); 
	break; 
	case 'counter': 
		if($usertype == 'manager' || ($lock && $countViews)) {
			break;
		} 
		else {
			$tvar = $modx->db->select('value', $table, 'tmplvarid ="'.$tvid.'" and contentid="'.$id.'"'); 
			if($modx->db->getRecordCount($tvar) == 0) {
				$insert = true; $count = 0;
			} 
			else {
				$row = $modx->db->getRow($tvar); 
				$count = $row['value'];
			} 
			$count++; 
			$_SESSION['countViews'][$id] = true; 
			$fields = array('value'	=> $count, 'tmplvarid' => $tvid, 'contentid' => $id); 
 
			if($insert) {
				$modx->db->insert($fields, $table);
			} 
			else {
				$modx->db->update($fields, $table, 'tmplvarid = "'.$tvid.'" and contentid = "'.$id.'"');
			}
		} 
	break;
}
</pre>
<p>На сторінках, де буде відбуватися підрахунок відвідувань, вставляємо цей код:</p>
<pre class="brush: php;">
[!countViews? &type=`counter` &id=`[*id*]` &tvid=`id TV-параметра countViews`!]
</pre>
<p>І, нарешті, в тому місці, де Ви ходите бачити кількість переглядів, вставляємо такий код:</p>
<pre class="brush: php;">
[[countViews? &type=`output` &id=`[*id*]` &tvid=`id TV-параметра countViews`]] - в документі MODX
[[countViews? &type=`output` &id=`[+id+]` &tvid=`id TV-параметра countViews`]] - в шаблоні Ditto
</pre>
<p><em><span class="text-bold">Зверніть увагу</span></em>: перегляд сторінки авторизованим користувачем в системі MODX не враховується.</p>
