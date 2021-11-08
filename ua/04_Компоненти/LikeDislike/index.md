
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>LikeDislike - можливість ставити оцінки </h3>
LikeDislike - можливість ставити оцінки на Evolution CMS.
<p>завантажувати тут: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/LikeDislike" rel="nofollow" target="_blank">Pathologic</a></p>
<p>В коробцы:</p>
<ul>
	<li>сніпет Like Dislike, який і дає можливість ставити оцінки;</li>
	<li>сніпет ldController для запуску DocLister з розширеним контролером site_content;</li>
	<li>модуль LikeDislike, щоб бачити оцінки в адмінці.</li>
</ul>
<p>Захист від накруток <s>ныяка</s> проста – кукы, ip, також можна дозволити оцінювати тільки зареєстрованим користувачам.</p>
<h3 class="sub-header">Встановлення</h3>
<p>Після установки потрібно запустити модуль, щоб створилися таблиці.</p>
<p>На сторінці документа потрібно підключити скрипт jGrowl:</p>
<pre class="brush: html;">
&lt;script type="text/javascript" src="assets/js/jGrowl/jquery.jgrowl.min.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet" href="assets/js/jGrowl/jquery.jgrowl.min.css"&gt;
</pre>

<p>І скрипт для ajax-розбробника:</p>
<pre class="brush: html;">
&lt;script type="text/javascript" src="assets/snippets/LikeDislike/likedislike.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet" href="assets/snippets/LikeDislike/likedislike.css"&gt;
</pre>

<p>Виклик сниппета виглядає так:</p>
<pre class="brush: html;">
[!LikeDislike? 
&amp;enabledTpl=`@CODE:
&lt;div class="likedislike" data-id="[+rid+]"&gt;
	&lt;a href="#" class="like"&gt;
		&lt;i class="fa fa-lg fa-thumbs-up"&gt;&lt;/i&gt;
		&lt;span&gt;[+like+]&lt;/span&gt;
	&lt;/a&gt;
	&lt;a href="#" class="dislike"&gt;
		&lt;i class="fa fa-lg fa-thumbs-down"&gt;&lt;/i&gt;
		&lt;span&gt;[+dislike+]&lt;/span&gt;
	&lt;/a&gt;
&lt;/div&gt;
` 
&amp;disabledTpl=`@CODE: 
&lt;div class="likedislike"&gt;
	&lt;span class="like"&gt;За: &lt;span&gt;[+like+]&lt;/span&gt;&lt;/span&gt;
	&lt;span class="dislike"&gt;Против: &lt;span&gt;[+dislike+]&lt;/span&gt;&lt;/span&gt;
&lt;/div&gt;
`
!]
</pre>
<p>Скрипт likedislike.jsнаписаний під верстку в цьому прикладі.</p>
<p>Крім виведення шаблонів сниппет задає плейсхолдери [+modResource.like.{id}+] і [+modResource.dislike.{id}+].</p>
<h3 class="sub-header">Параметри сніпета LikeDislike</h3>
<ul>
	<li><span class="text-bold">rid</span> – id оцінюваного ресурсу, якщо параметр не заданий, то по можливості використовується id поточного ресурсу;</li>
	<li><span class="text-bold">classKey</span> – параметр дозволяє розділяти оцінювані суті. Зроблено на майбутнє, раптом знадобиться ставити оцінки користувачам або ще чого-небудь. За замовчуванням</span> – modResource.</li>
	<li><span class="text-bold">action</span> – дія: like, dislike, stat (за замовчуванням – stat);</li>
	<li><span class="text-bold">enabledTpl</span> – шаблон, якщо дозволено оцінювати;</li>
	<li><span class="text-bold">disabledTpl</span> – шаблон, якщо заборонено оцінювати;</li>
	<li><span class="text-bold">onlyUsers</span> – дозволено оцінювати тільки зареєстрованим користувачам;</li>
</ul>
<p>Якщо не ставити шаблони, то сниппет поверне масив з ключами like і dislike.</p>

<h3 class="sub-header">Параметри сніпета ldController</h3>
<ul>
	<li><span class="text-bold">allowLD</span> – дозволити оцінювати в списку (за замовчуванням - 0);</li>
	<li><span class="text-bold">enabledTpl</span> – шаблон, якщо дозволено оцінювати;</li>
	<li><span class="text-bold">disabledTpl</span> – шаблон, якщо заборонено оцінювати;</li>
	<li><span class="text-bold">onlyUsers</span> – дозволено оцінювати тільки зареєстрованим користувачам;</li>
	<li><span class="text-bold">classKey;</span></li>
</ul>
<p>Для виведення в основному шаблоні (&tpl) потрібно використовувати плейсхолдер [+likedislike+]. Імена полів в параметрах для вибірки і сортування краще ставити з префіксом таблиці («c» для site_content і «ld» для likedislike). Поле like обов'язково повинно бути в зворотних лапках - `like`, інакше поламаються запити.</p>
