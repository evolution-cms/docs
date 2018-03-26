
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Личный кабинет веб пользователя MODx Evo </h3>
Сниппет для регистрации, входа, напоминания пароля и личного кабинета пользователя.
<h3 class="sub-header">Установка</h3>
<p>Создётся сниппет <span class="text-bold">account</span> с кодом</p>
<pre class="brush: php;">
&lt;?php
require MODX_BASE_PATH.'assets/snippets/account/snippet.account.php';
?>
</pre>
<p>Создаётся документ "Личный кабинет" -&gt; псевдоним -&gt; <span class="text-bold">account</span></p>
<p>Далее в нём дочерние ресурсы</p>
<p>Регистрация -&gt; <span class="text-bold">register</span></p>
<p>Профиль -&gt; <span class="text-bold">profile</span></p>
<p>Восстановление пароля -&gt; <span class="text-bold">forgot</span></p>
<p>и на каждой странице ставится вызов сниппета</p>
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
<p>Вместо псевдонимов контроллеров &amp;controller..., можно поставить id страниц на которых расположен тот или иной вызов сниппета.</p>
<p><span class="text-bold">&amp;success</span> - перенаправление после удачного действия сниппета.</p>
<p><span class="text-bold">&amp;userGroupId</span> - id групп, через запятую для нового зарегистрированного пользователя.</p>
<p>При создании вложенности документов, как указанно выше и используя вложенные URL, вызов сниппета можно сократить до одной строчки</p>
<pre class="brush: html">
[!account?&amp;userGroupId=``!]
</pre>
<p>либо использовать свои шаблоны</p>
<pre class="brush: html">
[!account?
&amp;tpl=`@FILE:assets/snippets/account/view/register.tpl.txt`
&amp;userGroupId=``
!]
</pre>

<h3 class="sub-header">AJAX</h3>
<p>Для работы через ajax используется <span class="text-bold">ModxLoader</span> - <a href="https://github.com/64j/ModxLoader" rel="nofollow" target="_blank">ModxLoader</a> </p>

<h3 class="sub-header">Капча</h3>
<p>Используется эта <a href="https://github.com/64j/ModxCaptcha" rel="nofollow" target="_blank">ModxCaptcha</a></p>
<p>Пример использования</p>
<pre class="brush: html;">
&lt;img src="assets/captcha" alt="captcha" width="120px" height="60px"/>
</pre>
<p>либо создать сниппет captcha и вывести его на отдельной странице с шаблоном blank и типом text/plain</p>
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
<p>Ветка обсуждения сниппета на форуме <a href="http://modx.im/blog/addons/4750.html" rel="nofollow" target="_blank">modx.im</a></p>

<h3 class="sub-header">Примеры использование</h3>
<p><span class="text-bold">Регистрация</span></p>
<p>Например поле Адрес, вместо того чтобы предложить юзеру записать весь адрес одной строчкой, можно поставить поля для каждого значения.</p>
<pre class="brush: html;">
<label>Город</label>
<input type="text" name="custom_field[address][city]" />

<label>Улица</label>
<input type="text" name="custom_field[address][street]" />

<label>Дом</label>
<input type="text" name="custom_field[address][house]" />

<label>Квартира</label>
<input type="text" name="custom_field[address][flat]" />
</pre>
<p>далее эти данные запишутся в базу в виде json строки.</p>
<p>Уровень вложенности можно использовать любой, но разумнее дальше 3-4 ого не залезать.</p>
<pre class="brush: html;">
<input type="text" name="custom_field[1][2][3][4]" />
</pre>
<p><span class="text-bold">Шаблоны</span></p>
<p>Шаблоны для формы в html со вставками php кода, можно использовать php сразу в шаблоне, либо все теги modx.</p>
<pre class="brush: php;">
<input type="text" name="email" value="&lt;?= $email ?>" placeholder="mail@mail.ru">
&lt;? if($error_email) { ?>
<div class="text-danger">
	&lt;?= $error_email ?>
</div>
&lt;? } ?>
</pre>
<p>либо использовать чанки, подключив их в <code>&tpl=`ваш чанк`</code></p>
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