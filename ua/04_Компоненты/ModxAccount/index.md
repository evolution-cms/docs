
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Особистий кабінет веб користувача MODx Evo </h3>
Сніппет для реєстрації, входу, нагадування пароля і особистого кабінету користувача.
<h3 class="sub-header">Установка</h3>
<p>Створюється сніппет <span class="text-bold">account</span> з кодом</p>
<pre class="brush: php;">
&lt;?php
require MODX_BASE_PATH.'assets/snippets/account/snippet.account.php';
?>
</pre>
<p>Створюється документ "Особистий кабінет" -&gt; псевдонім -&gt; <span class="text-bold">account</span></p>
<p>Далі в ньому дочірні ресурси</p>
<p>Реєстрація -&gt; <span class="text-bold">register</span></p>
<p>Профіль -&gt; <span class="text-bold">profile</span></p>
<p>Відновлення паролю -&gt; <span class="text-bold">forgot</span></p>
<p> І на кожній сторінці ставиться виклик сніппета</p>
<p><span class="text-bold">account</span></p>
<pre class="brush: html">
[!account?
&amp;controller=`account`
&amp;controllerRegister=`account/register`
&amp;controllerLogin=`account`
&amp;controllerForgot=`account/forgot`
&amp;controllerProfile=`account/profile`
&amp;success=``
&amp;userGroupId=``
!]
</pre>
<p><span class="text-bold">register</span></p>
<pre class="brush: html">
[!account?
&amp;controller=`account/register`
&amp;controllerRegister=`account/register`
&amp;controllerLogin=`account`
&amp;controllerForgot=`account/forgot`
&amp;controllerProfile=`account/profile`
&amp;success=``
&amp;userGroupId=``
!]
</pre>
<p><span class="text-bold">profile</span></p>
<pre class="brush: html">
[!account?
&amp;controller=`account/profile`
&amp;controllerRegister=`account/register`
&amp;controllerLogin=`account`
&amp;controllerForgot=`account/forgot`
&amp;controllerProfile=`account/profile`
&amp;success=``
&amp;userGroupId=``
!]
</pre>
<p><span class="text-bold">forgot</span></p>
<pre class="brush: html">
[!account?
&amp;controller=`account/forgot`
&amp;controllerRegister=`account/register`
&amp;controllerLogin=`account`
&amp;controllerForgot=`account/forgot`
&amp;controllerProfile=`account/profile`
&amp;success=``
&amp;userGroupId=``
!]
</pre>
<p>Замість псевдонімів контролерів &amp;controller..., можна поставити id сторінок на яких розташований той чи інший виклик сніппета.</p>
<p><span class="text-bold">&amp;success</span> - перенаправлення після вдалої дії сніппета.</p>
<p><span class="text-bold">&amp;userGroupId</span> - id груп, через кому для нового зареєстрованого користувача.</p>
<p>При створенні вкладеності документів, як вказано вище і використовуючи вкладені URL, виклик сніппета можна скоротити до одного рядка</p>
<pre class="brush: html">
[!account?&amp;userGroupId=``!]
</pre>
<p>або використовувати свої шаблони</p>
<pre class="brush: html">
[!account?
&amp;tpl=`@FILE:assets/snippets/account/view/register.tpl.txt`
&amp;userGroupId=``
!]
</pre>

<h3 class="sub-header">AJAX</h3>
<p>Для роботи через ajax використовується <span class="text-bold">ModxLoader</span> - <a href="https://github.com/64j/ModxLoader" rel="nofollow" target="_blank">ModxLoader</a> </p>

<h3 class="sub-header">Капча</h3>
<p>Використовується ця <a href="https://github.com/64j/ModxCaptcha" rel="nofollow" target="_blank">ModxCaptcha</a></p>
<p>Приклад використання</p>
<pre class="brush: html;">
&lt;img src="assets/captcha" alt="captcha" width="120px" height="60px"/>
</pre>
<p>або створити сніппет captcha і вивести його на окремій сторінці з шаблоном blank і типом text/plain</p>
<pre class="brush: php;">
&lt;?php
$chars = !empty($modx->config['captcha_words']) ? preg_replace('![^\w\d]*!', '', $modx->config['captcha_words']) : '1234567890';
$chars = substr(str_shuffle($chars), 0, 5);
if(isset($_REQUEST['key'])) {
    $_SESSION['veriword_' . md5($_REQUEST['key'])] = $chars;
} else {
    $_SESSION['veriword'] = $chars;
}
header("Pragma: no-cache");
header("Content-Type:image/png");
$img = imagecreate(210, 100);
imagecolorallocatealpha($img, 255, 255, 255, 127);
$color = imagecolorallocate($img, 0, 0, 0);
$x = 10;
for($i = 0; $i < strlen($chars); $i++) {
    $letter = mb_substr($chars, $i, 1, 'UTF-8');
    imagettftext($img, 70, rand(-10, 10), $x, 75, $color, MODX_MANAGER_PATH . "includes/ttf/ftb_____.ttf", $letter);
    $x += 35;
}
imagepng($img);
imagedestroy($img);
?>
</pre>
<p>Гілка обговорення сніппета на форумі <a href="http://modx.im/blog/addons/4750.html" rel="nofollow" target="_blank">modx.im</a></p>

<h3 class="sub-header">Приклади використання</h3>
<p><span class="text-bold">Реєстрація</span></p>
<p>Наприклад поле Адреса, замість того щоб запропонувати користувачеві записати весь адреса одним рядком, можна поставити поля для кожного значення.</p>
<pre class="brush: html;">
<label>Місто</label>
<input type="text" name="custom_field[address][city]" />

<label>Вулиця</label>
<input type="text" name="custom_field[address][street]" />

<label>Дім</label>
<input type="text" name="custom_field[address][house]" />

<label>Квартира</label>
<input type="text" name="custom_field[address][flat]" />
</pre>
<p>далі ці дані запишуться в базу у вигляді json рядка.</p>
<p>Рівень вкладеності можна використовувати будь-який, але розумніше дальше 3-4 ого НЕ залазити.</p>
<pre class="brush: html;">
<input type="text" name="custom_field[1][2][3][4]" />
</pre>
<p><span class="text-bold">Шаблони</span></p>
<p>Шаблони для форми в html зі вставками php коду, можна використовувати php відразу в шаблоні, або всі тегі modx.</p>
<pre class="brush: php;">
<input type="text" name="email" value="&lt;?= $email ?>" placeholder="mail@mail.ru">
&lt;? if($error_email) { ?>
<div class="text-danger">
	&lt;?= $error_email ?>
</div>
&lt;? } ?>
</pre>
<p>або використовувати чанкі, підключивши їх в <code>&tpl=`ваший чанк`</code></p>
<pre class="brush: html;">
<input type="text" name="email" value="[+email+]" placeholder="mail@mail.ru">
&lt;@IF:[+error_email+]>
	<div class="text-danger">
		[+error_email+]
	</div>
&lt;@ENDIF>

<input class="form-control" type="text" id="address" name="custom_field[address][street]" value="">
&lt;@IF:[+error_custom_field.address.street+]>
	<div class="text-danger">
		[+error_custom_field.address.street+]
	</div>
&lt;@ENDIF>
</pre>