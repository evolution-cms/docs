
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>BlackList: Захист від спаму без капчі </h3>
Плагін Захисту від спаму без капчі на Evolution CMS.
<h3 class="page-header">Приклад використовуючи платного веб-сервісу Akismet</h3>
<p>Автор: <i class="fa fa-modx fa-lg"></i> <a href="https://modx.ru/razrabotchiki-na-modx/8423/" rel="nofollow" target="_blank">Олексій Лібер</a></p>
<p>Перше, що треба зробити - зареєструватися на сайті <a href="https://akismet.com/" rel="nofollow" target="_blank">Akismet</a> і отримати ключ API. (Там просить реєстрацію на Wordpress.com, тому що клас спочатку під нього заточений був). Потім перейти на сторінку з плагінами і бібліотеками, вибрати і <a href="https://github.com/kenmoini/akismet/blob/master/src/Kenmoini/Akismet/Akismet.php" rel="nofollow" target="_blank">завантажити клас PHP 5 Akismet</a>.</p>
<p>Завантажений файлик akismet.class.php кидаємо в assets/lib/<p>
<p>Далі створюємо табличку для небажаних ip щоб відразу блокувати ip з яких розсилався спам.</p>
<p>Інструменти -&gt; Резервне копіювання -&gt; Відновити -&gt; Виконати довільну команду SQL.</p>
<pre class="brush: sql;">
CREATE TABLE `modx_ip_blocked` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `ip` varchar(16) NOT NULL,
  `blocked` tinyint(4) NOT NULL,
  `when` varchar(18) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `id` (`id`),
  UNIQUE KEY `ip` (`ip`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8
</pre>
<p>Далі створюємо плагін на події <span class="text-bold">OnBeforeLoadDocumentObject</span> и <span class="text-bold">OnLoadWebPageCache</span> і вставляємо наступний код:</p>
<pre class="brush: php;">
$blockip = 1; //Блокувати користувачів по ip. 1 - так. 0 - ні.
$e = $modx->Event;
if ($e->name == 'OnBeforeLoadDocumentObject' || $e->name == 'OnLoadWebPageCache'){
	if ($blockip){
		$ip = $_SERVER["REMOTE_ADDR"];
		$tbl = $modx->getFullTableName('ip_blocked');
		if ($modx->db->getValue("Select count(*) from $tbl where `ip`='$ip'") == 1){
			exit('Welcome to the blacklist!');			
		}
	}
	if (($_POST['name']) || ($_POST['email']) || ($_POST['message'])){
		require_once ('assets/lib/akismet.class.php');
		$akismet = new Akismet('http://site.com/', '905c97472xxx');
		$akismet->setCommentAuthor($_POST['name']);
		$akismet->setCommentAuthorEmail($_POST['email']);
		$akismet->setCommentContent($_POST['message']);
		if($akismet->isCommentSpam()){
			$modx->db->insert(array('ip'=>$ip,'blocked'=>1,'when'=>time()),$tbl);
			exit('Welcome to the blacklist!');
		}
	}
}
</pre>
<p>Дана конструкція перевіряє ім'я користувача, його email і саме повідомлення. В наведеному вище прикладі використовується ім'я поля message. Якщо у вас інше ім'я - поміняйте на ваше.</p>
<p>На момент написання посту пройшло близько 12-ї години з моменту установки даного рішення на одному з сайтів, спіймано п'ять листів які містять спам, і два від клієнтів доставлені адресату - тобто начебто працює справно.</p>

<h3 class="page-header">Безкоштовний приклад використовуючи дод. таблицю з емейл адресами або доменні імена</h3>
<p>Автор: <i class="fa fa-modx fa-lg"></i> <a href="http://saniock.com" rel="nofollow" target="_blank">Saniock</a></p>
<p><i class="fa fa-plus fa-fw"></i> безкоштовна</p>
<p><i class="fa fa-minus fa-fw"></i> Потрібно вручну додавати емейл адреси і доменні імена</p>

<p>Створюємо ту ж таблицю для небажаних ip</p>
<pre class="brush: sql;">
CREATE TABLE `modx_ip_blocked` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `ip` varchar(16) NOT NULL,
  `blocked` tinyint(4) NOT NULL,
  `when` varchar(18) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `id` (`id`),
  UNIQUE KEY `ip` (`ip`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8
</pre>

<p>Створюємо таблицю в якій будемо зберігати емейл адреси, або підозрілі доменні імена</p>
<pre class="brush: sql;">
CREATE TABLE `modx_email_blocked` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `email` varbinary(50) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `id` (`id`),
  UNIQUE KEY `email` (`email`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8
</pre>

<p>Далі створюємо плагін на події <span class="text-bold">OnBeforeLoadDocumentObject</span>, <span class="text-bold">OnLoadWebPageCache</span>, <span class="text-bold">OnPageNotFound</span> і вставляємо наступний код:</p>
<pre class="brush: php;">
$blockip = 1; //Блокувати користувачів по ip. 1 - так. 0 - ні.
$e = $modx->Event;
switch($e->name){
	case 'OnBeforeLoadDocumentObject':
	case 'OnLoadWebPageCache':
	case 'OnPageNotFound':
		$tbl_ip = $modx->getFullTableName('app_ip_blocked');
		$tbl_email = $modx->getFullTableName('app_email_blocked');
		
		if($blockip){
			$ip = $_SERVER["REMOTE_ADDR"];
			if($modx->db->getValue("Select count(*) from $tbl_ip where ip = '$ip'") == 1){
				exit('Welcome to the blacklist!');
			}
		}
		if($_POST['email']){
			$email = $modx->db->escape($_POST['email']);
			$email_domen = array_pop(explode('@', $email));
			
			if($modx->db->getValue("Select count(*) from $tbl_email where email = '$email' or email = '$email_domen'") > 0){
				$modx->db->insert(array('ip' => $ip,'blocked' => 1,'when' => time()), $tbl_ip);
				exit('Welcome to the blacklist!');
			}
		}
}
</pre>