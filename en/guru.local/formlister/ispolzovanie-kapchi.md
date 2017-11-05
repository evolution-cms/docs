
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>FormLister: Использование капчи</h2>

<p>По умолчанию FormLister может использовать модицифированную капчу MODX и Google Recaptcha. Также в наличии SmsCaptcha - для отправки формы необходимо ввести код, полученный в смс-сообщении (отправку сообщения необходимо реализовывать отдельно).</p>
<p>Для подключения необходимо указать имя папки с файлами капчи (папки находятся в assets/snippets/FormLister/lib/captcha/) в параметре &amp;captcha.</p>
<p>В параметре &amp;captchaParams задаются в виде массива настройки капчи. Например:</p>
<pre class="brush: html;">&amp;captchaParams=`{
	"width":200,
	"height":120
}`</pre>
<p>Имя поля, в которое пользователь вводит значение капчи, задается параметром captchaField (по умолчанию - vericode). Правило валидации для этого поля создается автоматически.</p>
<p>Капча выводится в шаблоне формы с помощью плейсхолдера [+captcha+].</p>
<h3 class="sub-header text-bold">modxCaptcha</h3>
<p>Модификация стандартной капчи MODX.</p>
<p>Настройки:</p>
<ul>
<li>width и height - ширина и высота картинки с капчей (значение по умолчанию - 100 и 60);</li>
<li>inline - формат вывода. Если значение параметра равно 1, то в плейсхолдер [+captcha+] выводится картинка в base64-формате. Если 0, то выводится ссылка на файл connector.php, генерирующий картинку. Значение по умолчанию - 1;</li>
<li>connectorDir - путь к папке с файлом connector.php, если параметр inline равен 0. Значение по умолчанию - assets/snippets/FormLister/lib/captcha/modxCaptcha/;</li>
<li>errorEmptyCode - текст сообщения об ошибке, если поле со значением капчи не заполнено. Значение по умолчанию - "Введите проверочный код";</li>
<li>errorCodeFailed - текст сообщения об ошибке, если введено неверное значение капчи. Значение по умолчанию - "Неверный проверочный код" </li>
</ul>
<h3 class="sub-header text-bold">reCaptcha</h3>
<p>Капча Google reCAPTCHA V2. На странице с формой должен быть подключен скрипт:</p>
<pre class="brush: html;">&lt;script src='https://www.google.com/recaptcha/api.js'&gt;&lt;/script&gt;</pre>
<p>Значение параметра captchaField должно быть "g-recaptcha-response" (см. <a href="https://developers.google.com/recaptcha/docs/verify" rel="nofollow" taget="_blank">документацию</a>). </p>
<p>Настройки:</p>
<ul>
<li>secretKey, siteKey - ключи для доступа к api reCAPTCHA; </li>
<li>size, theme, badge, callback, expired_callback, tabIndex, type - см. <a href="https://developers.google.com/recaptcha/docs/display#render_param" rel="nofollow" taget="_blank">документацию</a>;</li>
<li>errorCodeFailed - текст сообщения об ошибке, если пользователь не прошел проверку. Значение по умолчанию - "Вы не прошли проверку"</li>
</ul>
<h3 class="sub-header text-bold">smsCaptcha</h3>
<p>Настройки: </p>
<ul>
<li>codeLifeTime - срок действия введенного кода, секунд. Если пользователь попытается ввести код до истечения срока, то будет выведено сообщение errorCodeUsed. Значение по умолчанию - 86400 (сутки);</li>
<li>errorEmptyCode - сообщение об ошибке, если пользователь получил, но не ввел код. Значение по умолчанию - "Введите код авторизации"; </li>
<li>errorCodeRequired - сообщение об ошибке, если пользователь не запросил код. Значение по умолчанию - "Получите код авторизации"; </li>
<li>errorCodeFailed - сообщение об ошибке, если пользователь ввел неверный код авторизации. Значение по умолчанию - "Неверный код авторизации";</li>
<li>errorCodeExpired - сообщение об ошибке, если пользователь не ввел полученный код в течение заданного времени. Значение по умолчанию - "Код авторизации истек, получите новый"; </li>
<li>errorCodeUsed - сообщение об ошибке, если пользователь уже вводил код для текущей формы. Значение по умолчанию - "Код авторизации уже использовался".</li>
</ul>
<p>Чтобы использовать эту капчу необходимо предварительно создать таблицу в базе данных:</p>
<pre class="brush: php;">&lt;?php
include_once(MODX_BASE_PATH.'assets/snippets/FormLister/lib/captcha/smsCaptcha/model.php');
$sms = new \SmsModel($modx);
$sms-&gt;createTable();</pre>
<p>Для отправки кода необходимо создать отдельную форму и указать в параметре prepareProcess сниппет:</p>
<pre class="brush: php;">&lt;?php
//удаляем из номера телефона все, кроме цифр
$rawPhone = preg_replace('/[^\d]+/','',$data['phone']);
//задаем значение, по которому будет определяться для какой формы генерируется код
$formid = 'basic';
//в сессии будем хранить номер телефона, это нужно для проверки кода в основной форме, потом его можно использовать в каких-то целях, например убрать из основной формы поле для ввода телефона, а в письме использовать телефон из сессии
$session_key = $formid.'.smscaptcha';
if (empty($rawPhone)) {
	$FormLister-&gt;setValid(false);
	$FormLister-&gt;addError('phone','phone','Неверный номер телефона');   
} else {
	//загружаем класс для работы с таблицей
	$sms = $FormLister-&gt;loadModel('SmsModel','assets/snippets/FormLister/lib/captcha/smsCaptcha/model.php');
	$flag = false;
	//проверяем, есть ли в таблице запись для заданного номера и идентификатора формы
	$data = $sms-&gt;getData('+'.$rawPhone,$formid);
	if ($data-&gt;getID()) {
		//если есть и код не истек
		if ($sms-&gt;get('expires') &gt; time()) {
			//смотрим, использован ли код
			if ($sms-&gt;get('active')) {
				$FormLister-&gt;addMessage('Вы уже использовали код.');
			} else {
				$FormLister-&gt;addMessage('Код уже был отправлен. Подождите несколько минут прежде чем запросить новый.');
			}
		//если код истек, то удаляем запись и разрешаем выдать новый
		} else {
			$sms-&gt;delete($sms-&gt;getID());
			$flag = true;
		}
	} else {
		$flag = true;
	}
	//если можно выдать новый код
	if ($flag) {
		$code = mt_rand(1000,9999);

		//здесь отправляется смс и результат помещается в переменную $result
		/** 
		 *  
		 */ 
		$result = array('status'=&gt;true);

		//проверяем отправлена ли смс
		if (is_array($result) &amp;&amp; $result['status']) {
			//создаем запись в таблице, время жизни кода - 3 минуты
			$result = $sms-&gt;create()-&gt;fromArray(array(
				'phone'=&gt;('+'.$rawPhone),
				'formid'=&gt;$formid,
				'expires'=&gt;(time() + 60*3),
				'ip'=&gt; \APIhelpers::getUserIP(),
				'code'=&gt;$code
			))-&gt;save(); 
			//если получилось записать, то сохраняем в сессию номер телефона
		if ($result) {
			$_SESSION[$session_key] = '+'.$rawPhone;
		} else {
			$FormLister-&gt;setValid(false);
			$FormLister-&gt;addMessage('Не удалось отправить смс');
		}
	} else {
		//если нельзя выдать код, то запрещаем дальнейшую обработку формы
		$FormLister-&gt;setValid(false);
	}
}
?&gt;</pre>
<p>Полностью вызов FormLister:</p>
<pre class="brush: html;">
&lt;div class="row"&gt;
	&lt;div class="col-md-8 col-md-offset-2"&gt;
		&lt;div class="well"&gt;
			&lt;form class="form-horizontal" method="post"&gt;
				&lt;input type="hidden" name="formid" value="code"&gt;
				&lt;div class="form-group[+phone.errorClass+][+phone.requiredClass+]"&gt;
					&lt;label for="phone" class="col-sm-2 control-label"&gt;* Телефон&lt;/label&gt;
					&lt;div class="col-sm-10"&gt;
						&lt;input type="text" class="form-control" placeholder="+375 29 123 45 67" name="phone" value="[+phone.value+]"&gt;
						[+phone.error+]
					&lt;/div&gt;
				&lt;/div&gt;
				[+form.messages+]
				&lt;div class="form-group"&gt;
					&lt;div class="col-sm-offset-2 col-sm-10"&gt;
						&lt;button type="submit" class="btn btn-primary"&gt;&lt;i class="glyphicon glyphicon-envelope"&gt;&lt;/i&gt; Отправить&lt;/button&gt;
					&lt;/div&gt;
				&lt;/div&gt;
				&lt;img src="[+captcha+]"&gt;
				&lt;input name="vericode"&gt;
				[+vericode.error+]
			&lt;/form&gt;
		&lt;/div&gt;
	&lt;/div&gt;
&lt;/div&gt;</pre>