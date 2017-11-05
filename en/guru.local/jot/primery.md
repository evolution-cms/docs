
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Jot: Примеры</h2>

<h3 class="sub-header text-bold"><a id="1082"></a>Простой вызов</h3><div class="well bordered-left bordered-blue"><ul>
<li>с оповещением на эл.почту.</li>
<li>с постраничной навигацией: 10 комментариев на странице.</li>
</ul>
<div class="well-box-shadow"><pre class="brush: html;">[!Jot? &subscribe=`1` &pagination=`10`!]</pre></div></div>
<h3 class="sub-header text-bold"><a id="1083"></a>С альтернативной сортировкой</h3><div class="well bordered-left bordered-blue"><ul>
<li>с оповещением на эл.почту.</li>
<li>с постраничной навигацией: 10 комментариев на странице.</li>
<li>комментарии сортируются начиная с самого старого.</li>
</ul>
<div class="well-box-shadow"><pre class="brush: html;">[!Jot? &subscribe=`1` &pagination=`10` &sortby=`createdon:a`!]</pre></div></div>
<h3 class="sub-header text-bold"><a id="1084"></a>Модерация</h3><div class="well bordered-left bordered-blue"><ul>
<li>с оповещением на эл.почту.</li>
<li>с постраничной навигацией: 10 комментариев на странице.</li>
<li>новые комментарии не публикуются, их опубликовывает модератор.</li>
<li>автору не будут приходить уведомления. Вы должны создать веб-группу с веб-пользователями, которые бы выступали в качестве модераторов.</li>
<li>Но автор будет получать уведомления
<ul>
<li>если используется Jot 1.1.3+</li>
<li>менеджером является автор комментария</li>
<li>вы добавите &notifyAuthor=`1`</li>
</ul>
</li>
</ul>
<div class="well-box-shadow"><pre class="brush: html;">[!Jot? &subscribe=`1` &pagination=`10` &moderated=`1`!]</pre></div></div>
<h3 class="sub-header text-bold"><a id="1085"></a>Расширенная модерация</h3><div class="well bordered-left bordered-blue"><ul>
<li>с оповещением на эл.почту.</li>
<li>с постраничной навигацией: 10 комментариев на странице.</li>
<li>новые комментарии не публикуются, их опубликовывает модератор.</li>
<li>новые комментарии будут опубликованы лишь в том случае, если автор входит в состав группы "Доверенные Пользователи".</li>
</ul>
<div class="well-box-shadow"><pre class="brush: html;">[!Jot? &subscribe=`1` &pagination=`10` &moderated=`1` &trusted=`Доверенные Пользователи`!]</pre></div></div>
<h3 class="sub-header text-bold"><a id="1086"></a>Анти-спам: автоматический</h3><div class="well bordered-left bordered-blue"><ul>
<li>с постраничной навигацией: 10 комментариев на странице.</li>
<li>с предоставлением динамически меняющейся картинкой с кодом (captcha).</li>
<li>если в чёрный список слов входит слово, используемое в комментарии, комментарий будет отклонён, возможно, что даже потерян.</li>
<li>чёрным списком фраз является чанк "myBadwordList"</li>
</ul>
<div class="well-box-shadow"><pre class="brush: html;">[!Jot? &pagination=`10` &captcha=`1` &badwords=`{{myBadwordList}}` &bw=`2`!]</pre></div></div>
<h3 class="sub-header text-bold"><a id="1087"></a>Анти-спам: с модерацией</h3><div class="well bordered-left bordered-blue"><ul>
<li>с постраничной навигацией: 10 комментариев на странице.</li>
<li>с предоставлением динамически меняющейся картинкой с кодом (captcha).</li>
<li>если в чёрный список слов входит слово, используемое в комментарии, комментарий не будет опубликован, и модератор при этом будет оповещён.</li>
<li>веб-пользователи из группы "Модераторы комментариев" могут редактировать комментарии.</li>
<li>чёрным списком фраз является чанк "myBadwordList".</li>
</ul>
<div class="well-box-shadow"><pre class="brush: html;">[!Jot? &pagination=`10` &captcha=`1` &canmoderate=`Модераторы комментариев` &badwords=`{{myBadwordList}}` &bw=`1`!]</pre></div></div>
<h3 class="sub-header text-bold"><a id="1088"></a>Расположение блоков</h3><div class="well bordered-left bordered-blue"><p>Для того, чтобы изменить на странице место и порядок вывода блоков (форма, модерация, комментарии, навигация), поместите вызов сниппета, как обычно:</p>
<p>[!Jot? &placeholders=`1` &output=`0` &pagination=`10` &captcha=`1` &canmoderate=`Jot Moderators` &badwords=`{{myBadwordList}}` &bw=`1`!]</p>
<p>Обратите внимание, следующие параметры вы должны указать обязательно:</p>
<div class="well-box-shadow"><pre class="brush: html;">&placeholders=`1` &output=`0`</pre></div>
<p>Теперь, разместите на странице с вызовом сниппета Jot следующие плейсхолдеры:</p>
<div class="well-box-shadow"><pre class="brush: html;">[+jot.html.navigation+] - Первый. Место на странице для навигации
[+jot.html.comments+] - Второй. Место на странице для комментариев
[+jot.html.moderate+] - Третий. Место на странице для модерации
[+jot.html.form+] - Четвертый. Место на странице для формы</pre></div>
<p>Вы можете изменить порядок блоков так, как считаете нужным:</p>
<div class="well-box-shadow"><pre class="brush: html;">[+jot.html.form+] - Первый. Место на странице для формы
[+jot.html.comments+] - Второй. Место на странице для комментариев
[+jot.html.moderate+] - Третий. Место на странице для модерации
[+jot.html.navigation+] - Четвертый. Место на странице для навигации</pre></div></div>