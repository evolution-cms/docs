
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>LikeDislike</h2>

<p>Скачивать здесь: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/LikeDislike" rel="nofollow" target="_blank">Pathologic</a></p>
<p>В коробке:</p>
<ul>
	<li>сниппет LikeDislike, который и дает возможность ставить оценки;</li>
	<li>сниппет ldController для запуска DocLister с расширенным контроллером site_content;</li>
	<li>модуль LikeDislike, чтобы видеть оценки в админке.</li>
</ul>
<p>Защита от накруток <s>никакая</s> простая – куки, ip, также можно разрешить оценивать только зарегистрированным пользователям.</p>
<h3 class="sub-header">Установка</h3>
<p>После установки нужно запустить модуль, чтобы создались таблицы.</p>
<p>На странице документа нужно подключить скрипт jGrowl:</p>
<pre class="brush: html;">
&lt;script type="text/javascript" src="assets/js/jGrowl/jquery.jgrowl.min.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet" href="assets/js/jGrowl/jquery.jgrowl.min.css"&gt;
</pre>

<p>И скрипт для ajax-обработчика:</p>
<pre class="brush: html;">
&lt;script type="text/javascript" src="assets/snippets/LikeDislike/likedislike.js"&gt;&lt;/script&gt;
&lt;link rel="stylesheet" href="assets/snippets/LikeDislike/likedislike.css"&gt;
</pre>

<p>Вызов сниппета выглядит так:</p>
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
<p>Скрипт likedislike.js написан под верстку в этом примере.</p>
<p>Кроме вывода шаблонов сниппет задает плейсхолдеры [+modResource.like.{id}+] и [+modResource.dislike.{id}+].</p>
<h3 class="sub-header">Параметры сниппета LikeDislike</h3>
<ul>
	<li><span class="text-bold">rid</span> – id оцениваемого ресурса, если параметр не задан, то по возможности используется id текущего ресурса;</li>
	<li><span class="text-bold">classKey</span> – параметр позволяющий разделять оцениваемые сущности. Сделано на будущее, вдруг понадобится ставить оценки пользователям или еще чему-нибудь. По умолчанию</span> – modResource.</li>
	<li><span class="text-bold">action</span> – действие: like, dislike, stat (по умолчанию – stat);</li>
	<li><span class="text-bold">enabledTpl</span> – шаблон, если разрешено оценивать;</li>
	<li><span class="text-bold">disabledTpl</span> – шаблон, если запрещено оценивать;</li>
	<li><span class="text-bold">onlyUsers</span> – разрешено оценивать только зарегистрированным пользователям;</li>
</ul>
<p>Если не задавать шаблоны, то сниппет вернет массив с ключами like и dislike.</p>

<h3 class="sub-header">Параметры сниппета ldController</h3>
<ul>
	<li><span class="text-bold">allowLD</span> – разрешить оценивать в списке (по умолчанию – 0);</li>
	<li><span class="text-bold">enabledTpl</span> – шаблон, если разрешено оценивать;</li>
	<li><span class="text-bold">disabledTpl</span> – шаблон, если запрещено оценивать;</li>
	<li><span class="text-bold">onlyUsers</span> – разрешено оценивать только зарегистрированным пользователям;</li>
	<li><span class="text-bold">classKey;</span></li>
</ul>
<p>Для вывода в основном шаблоне (&tpl) нужно использовать плейсхолдер [+likedislike+]. Имена полей в параметрах для выборки и сортировки лучше задавать с префиксом таблицы («c» для site_content и «ld» для likedislike). Поле like обязательно должно быть в обратных кавычках – `like`, иначе поломаются запросы.</p>