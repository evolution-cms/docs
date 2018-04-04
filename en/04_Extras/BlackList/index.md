
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>BlackList: Защита от спама без каптчи </h3>
Плагин Защиты от спама без каптчи на Evolution CMS.
<h3 class="page-header">Пример используя платного веб-сервиса Akismet</h3>
<p>Автор: <i class="fa fa-modx fa-lg"></i> <a href="https://modx.ru/razrabotchiki-na-modx/8423/" rel="nofollow" target="_blank">Алексей Либер</a></p>
<p>Первое, что надо сделать – зарегистрироваться на сайте <a href="https://akismet.com/" rel="nofollow" target="_blank">Akismet</a> и получить ключ API. (Там просит регистрацию на Wordpress.com, т.к. класс изначально под него заточен был). Затем перейти на страницу с плагинами и библиотеками, выбрать и <a href="https://github.com/kenmoini/akismet/blob/master/src/Kenmoini/Akismet/Akismet.php" rel="nofollow" target="_blank">загрузить класс PHP 5 Akismet</a>.</p>
<p>Загруженный файлик akismet.class.php кидаем в assets/lib/<p>
<p>Далее создаем табличку для нежелательных ip чтобы сразу блокировать ip с которых рассылался спам.</p>
<p>Инструменты -&gt; Резервное копирование -&gt; Восстановить -&gt; Выполнить произвольную команду SQL.</p>
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
<p>Далее создаем плагин на события <span class="text-bold">OnBeforeLoadDocumentObject</span> и <span class="text-bold">OnLoadWebPageCache</span> и вставляем следующий код:</p>
<pre class="brush: php;">
$blockip = 1; //Блокировать пользователей по ip. 1 - да. 0 - нет.
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
<p>Данная конструкция проверяет имя пользователя, его email и само сообщение. В примере выше используется имя поля message. Если у вас другое имя – поменяйте на ваше.</p>
<p>На момент написания поста прошло около 12-ти часов с момента установки данного решения на одном из сайтов, поймано пять писем содеражих спам, и два от клиентов доставлены адресату – т.е. вроде работает исправно.</p>

<h3 class="page-header">Бесплатный пример используя доп. таблицу с емаил адресами или доменные имена</h3>
<p>Автор: <i class="fa fa-modx fa-lg"></i> <a href="http://saniock.com" rel="nofollow" target="_blank">Saniock</a></p>
<p><i class="fa fa-plus fa-fw"></i> бесплатна</p>
<p><i class="fa fa-minus fa-fw"></i> надо в ручную добавлять емаил адреса или доменные имена</p>

<p>Cоздаем ту же таблицу для нежелательных ip</p>
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

<p>Cоздаем таблицу в котором будем хранить емаил адреса, или подозрительные доменные имена</p>
<pre class="brush: sql;">
CREATE TABLE `modx_email_blocked` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `email` varbinary(50) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `id` (`id`),
  UNIQUE KEY `email` (`email`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8
</pre>

<p>Далее создаем плагин на события <span class="text-bold">OnBeforeLoadDocumentObject</span>, <span class="text-bold">OnLoadWebPageCache</span>, <span class="text-bold">OnPageNotFound</span> и вставляем следующий код:</p>
<pre class="brush: php;">
$blockip = 1; //Блокировать пользователей по ip. 1 - да. 0 - нет.
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