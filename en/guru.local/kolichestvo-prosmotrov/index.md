
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>countViews</h2>

<p>Устанавливаем счетчик количества просмотров. Для этого нам нужно будет создать дополнительное поле в таблице <span class="text-bold">modx_site_content</span> базы данных. Вот параметры нового поля – <span class="text-bold">count int(20) default = 0</span>.</p>
<p>Теперь создадим сниппет <span class="text-bold">inc</span>, который будет считать количество посещений. Вызов сниппета inc нужно установить в самом верху шаблона материалов. Код сниппета:</p>
<pre class="brush: php;">
$table = $modx->getFullTableName("site_content");
$id = $modx->documentObject['id'];
$result = $modx->db->update("count=count+1", $table, "id=$id");
</pre>
<p>И наконец, создаем сниипет <span class="text-bold">hits</span>, отвечающий за вывод количества просмотров:</p>
<pre class="brush: php;">
$id = isset($id) ? $id : $modx->documentIdentifier;
return $modx->db->getValue($modx->db->select('count',$modx->getFullTableName('site_content'),'id='.$id));
</pre>
<p>Давайте рассмотрим еще один способ подсчета количества просмотров. Данный способ имеет одно преимущество перед предыдущим – его можно использовать в шаблоне Ditto (<a rel="nofollow" href="http://rekill.ru/modx/snippet-kolichestvo-prosmotrov" target="_blank">исходные материалы</a>).</p>
<p>Итак, создадим TV-параметр <span class="text-bold">countViews</span>
с типом ввода Text.</p>
<p>Далее создаем сниппет <span class="text-bold">countViews</span> с таким содержанием:</p>
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
<p>На страницах, где будет происходить подсчет посещений, вставляем этот код:</p>
<pre class="brush: php;">
[!countViews? &type=`counter` &id=`[*id*]` &tvid=`id TV-параметра countViews`!]
</pre>
<p>И, наконец, в том месте, где Вы ходите видеть количество просмотров, вставляем такой код:</p>
<pre class="brush: php;">
[[countViews? &type=`output` &id=`[*id*]` &tvid=`id TV-параметра countViews`]] - в документе MODX
[[countViews? &type=`output` &id=`[+id+]` &tvid=`id TV-параметра countViews`]] - в шаблоне Ditto
</pre>
<p><em><span class="text-bold">Обратите внимание</span></em>: просмотр страницы авторизованным пользователем в системе MODX не учитывается.</p>