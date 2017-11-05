
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>reCAPTCHA для eForm</h2>

<h3 class="sub-header text-bold">Установка</h3>
<p>1. Прежде всего нужно получить ключи для сайта (siteKey и secretKey) – <a href="https://www.google.com/recaptcha/admin" rel="nofollow" target="_blank">здесь</a></p>
<p>2. Скачиваем готовую PHP библиотеку каптчи здесь: <a href="https://github.com/google/recaptcha" rel="nofollow" target="_blank">github</a> (Clone or download, Download ZIP)</p>
<p>3. Из архива, вытаскиваем папку src, закачиваем в папку /assets/snippets и переименовываем эту папку в recaptcha</p>
<p>4. Создаем сниппет <code>ReCaptcha</code> и вставляем в него данный код:</p>
<pre class="brush: php;">
&lt;?php
if(!defined('MODX_BASE_PATH')) {die('What are you doing? Get out of here!');}
include_once MODX_BASE_PATH.'assets/snippets/recaptcha/autoload.php';

if(!defined('siteKey')) {define('siteKey', 'siteKeyCodestring');}
if(!defined('secretKey')) {define('secretKey', 'secretKeyCodestring');}

$lang = isset($lang) ? $lang : 'ru';
$text = isset($text) ? $text : 'Вы не подтвердили, что вы не робот!';

unset($_SESSION['veriword']);

$script = '&lt;script src="//google.com/recaptcha/api.js?hl='.$lang.'">&lt;/script>';
$modx->regClientStartupScript($script);

$Recaptcha = new \ReCaptcha\ReCaptcha(secretKey);

if(isset($_REQUEST['g-recaptcha-response'])){
	$resp = $Recaptcha->verify($_REQUEST['g-recaptcha-response'], $_SERVER['REMOTE_ADDR']);
	if($resp->isSuccess()){
		$_SESSION['veriword'] = $_SESSION['eForm.VeriCode'];
		$_POST['vericode'] = $_SESSION['eForm.VeriCode'];
	} else {
		$response = $resp->getErrorCodes();            
		if(!empty($response)){
			$codes='';
			foreach ($response as $code) { $codes.= $code; }
			$_SESSION['veriword'] = 'ReCaptchaErrors : '.$codes;
		}
	}
}
        
if(!function_exists('setReCaptcha')){
	function setReCaptcha(&$fields){
		$fields['ReCaptcha']= '<div class="g-recaptcha" data-sitekey="'.siteKey.'"></div>';
		return true;
	}
}

if(!function_exists('verifyReCaptcha')){
	function verifyReCaptcha(&$fields,&$vMsg,&$rMsg,&$rClass){
		if($_SESSION['veriword'] !== $_SESSION['eForm.VeriCode']){
			$vMsg[] = $text; 
		}
		return true;
	}
}
?&gt;
</pre>
<p>5. В темплейты eForm прописываем плейсхолдер <code>[+ReCaptcha+]</code> в том месте, где хотим ее видеть (если вы используете в темплейтах вызов veriword.php, закройте его комментарием или удалите)</p>
<p>6. Перед вызовом eForm ставим вызов сниппета ReCaptcha <code>[[ReCaptcha]]</code>, а в вызов самого eForm добавляем параметры:</p>
<pre class="brush: html;">
&vericode=`1`
&eFormOnBeforeFormMerge=`setReCaptcha`
&eFormOnValidate=`verifyReCaptcha`
</pre>