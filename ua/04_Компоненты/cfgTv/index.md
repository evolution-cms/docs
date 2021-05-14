
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>CfgTv: системные настройки из списка ТВ параметров из указанного документа Создает системные настройки из списка ТВ параметров из указанного документа</h3>
Создает системные настройки из списка ТВ параметров из указанного документа.
<p>Многие любят и активно юзают настройки сайта через <code>[[getField? name=`tv_name` ...]]]</code>, создавая ресурс где все эти настройки в TV лежат. Но вот незадача, каждая такая настройка = 1 запросу, а значит и время генерации больше + неудобно.</p>
<p>А что если делать также, но вызов на странице будет <code>[(cfg_footer_phone)]</code>, <code>[(cfg_icq)]</code> и так далее удобно правда?</p>
<p>Решение: CfgTv</p>
<p>Событие: <code>OnBeforeDocFormSave</code></p>
<pre class="brush: php;">
/**
 * CfgTv 0.1
 * Save TV as system setting from some resourse 
 * 
 *
 * @category    plugin
 * @version     1.0.0b
 * @author      Bumkaka
 * @internal    @properties &ids=ID ресурсов настроек;text;347 &prefix=Префикс;text;cfg_
 * @internal    @events OnBeforeDocFormSave
 * @internal    @modx_category Manager and Admin
 */

$e = &$modx->event;
switch($e->name){
    case 'OnBeforeDocFormSave':
		$list_id = explode(',',$ids);
		if(!in_array($_POST['id'],$list_id)) return;
		
		$SQL = "SELECT * FROM ".$modx->getFullTableName('site_tmplvars').";";
		$result = $modx->db->query($SQL);
		
		while($row = $modx->db->getRow($result)){
			$TVNAME[$row['id']] = $row['name'];
		}
		
		foreach($_POST as $key => $value){
			if (substr($key,0,2)!='tv') continue;
			$id=substr($key,2,strlen($key));
			$name=$prefix.$TVNAME[$id];
			$settings[$name]=$value;
			$SQL="SELECT * FROM ".$modx->getFullTableName('system_settings')." WHERE `setting_name`='".$name."'";
			$count=$modx->db->getRow($modx->db->query($SQL));
			if (!empty($count['setting_name'])){
				$SQL="UPDATE ".$modx->getFullTableName('system_settings')." SET `setting_value`='".$value."' WHERE `setting_name`='".$name."'";
				$modx->db->query($SQL);
			} else {
				$SQL="INSERT into ".$modx->getFullTableName('system_settings')." SET `setting_name`='".$name."',`setting_value`='".$value."'";
				$modx->db->query($SQL);
			}
		}
    break;
}
</pre>