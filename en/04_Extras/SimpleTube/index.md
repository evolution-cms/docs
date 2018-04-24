
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>SimpleTube - плагин и сниппет для создания видеогалерей </h3>
SimpleTube - плагин и сниппет для создания видеогалерей.
<p>Основных отличий всего два, но мне кажется, они достаточно существенные, чтобы сменить название:</p>
<ul>
	<li>теперь используется отдельная таблица для хранения данных, вместо TV-параметра с json;</li>
	<li>новый удобный интерфейс c jQuery EasyUI</li>
</ul>
<p>Для работы всего этого необходимо наличие <a href="https://github.com/AgelxNash/DocLister" rel="nofollow" target="_blank">DocLister и MODxAPI</a>, а также PHP 5.6.</p>
<p>Скачивать здесь: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/SimpleTube" rel="nofollow" target="_blank">Pathologic</a></p>
<p><span class="text-bold">Сниппет</span> умеет находить с помощью класса <a href="http://frandieguez.github.io/panorama-php/" rel="nofollow" target="_blank">Panorama-PHP</a> информацию о видео по ссылке, а также при возможности скачивать картинку-превью. Поддерживаются youtube, rutube, vimeo, metacafe и dailymotion. Вообще класс поддерживает больше видеохостингов, но это в теории; поэтому я оставил только то, что более-менее работает (при этом, например, о metacafe и dailymotion я ни разу не слышал).</p>
<p>С помощью этого сниппета плагин получает информацию для добавления в таблицу, но ничто не мешает использовать его без плагина, как сниппет getVideo из MultiVideos.</p>
<h3 class="sub-header">Параметры Сниппета:</h3>
<ul>
	<li><span class="text-bold">&input</span> – ссылка;</li>
	<li><span class="text-bold">&forceDownload</span> – если 1, то всегда скачивать превью, если 0, то только в том случае, если картинки нет в папке; по умолчанию – 0;</li>
	<li><span class="text-bold">&folder</span> – папка для хранения превью; по умолчанию – assets/images/video/;</li>
	<li><span class="text-bold">&noImage</span> – путь к картинке, которая выводится в режиме &api=`0` при отсутствии превью; по умолчанию – assets/snippets/simpletube/noimage.png;</li>
	<li><span class="text-bold">&api</span> – если 0, то выводится чанк &tpl, 1 – json, 2 – массив; по умолчанию – 0;</li>
	<li><span class="text-bold">&tpl</span> – чанк для вывода в режиме &api=`0`, указывается так же, как в DocLister. Доступные плейсхолдеры: [+st_title+] (название видео), [+st_thumbUrl+] (ссылка на превью или картинку noImage), [+st_embedUrl+] (ссылка для встраивания), [+st_service+] (название видеохостинга), [+st_duration+] (длина видео, секунд);</li>
	<li><span class="text-bold">&ytApiKey</span> – ключ для работы с Youtube, если параметр не указан, то сниппет попытается получить это значение из настроек плагина.</li>
</ul>
<h3 class="sub-header">Параметры Плагина:</h3>
<p>Плагин используется для управления галереями на странице ресурса.</p>
<ul>
	<li><span class="text-bold">Tab name</span> – название вкладки;</li>
	<li><span class="text-bold">Templates</span> – id шаблонов ресурсов с видео, <span class="text-bold">обязательно</span> – ;</li>
	<li><span class="text-bold">Roles</span> – id разрешенных ролей;</li>
	<li><span class="text-bold">Thumbs folder</span> – папка для превью;</li>
	<li><span class="text-bold">Thumbs cache folder</span> – папка для превью превью (:</li>
	<li><span class="text-bold">No image picture</span> – картинка, если нет превью;</li>
	<li><span class="text-bold">Thumbs width</span> – ее ширина;</li>
	<li><span class="text-bold">Thumbs height</span> – и высота;</li>
	<li><span class="text-bold">Force download</span> – скачивать превью всегда или при необходимости;</li>
	<li><span class="text-bold">Youtube API Key</span> – ключ для работы с YouTube.</li>
</ul>
<p>Вывод такой же, как в SimpleGallery – c поправкой на название таблицы и полей. Поэтому смотреть <a href="http://modx.im/blog/docs/2762.html" rel="nofollow" target="_blank">здесь</a>.</p>
<h3 class="sub-header">Поля в таблице st_videos:</h3>
<ul>
	<li><span class="text-bold">st_id</span> – id видео (idField);</li>
	<li><span class="text-bold">st_index</span> – позиция в списке;</li>
	<li><span class="text-bold">st_title</span> – название видео;</li>
	<li><span class="text-bold">st_videoUrl</span> – исходная ссылка на видео;</li>
	<li><span class="text-bold">st_thumbUrl</span> – ссылка на превью;</li>
	<li><span class="text-bold">st_embedUrl</span> – ссылка для встраивания;</li>
	<li><span class="text-bold">st_duration</span> – длина видео, секунды;</li>
	<li><span class="text-bold">st_isactive</span> – флажок, чтобы скрыть какие-то видео из вывода;</li>
	<li><span class="text-bold">st_service</span> – название видеохостинга;</li>
	<li><span class="text-bold">st_rid</span> – id ресурса, которому принадлежит видео (parentField).</li>
	<li><span class="text-bold">st_createdon</span> – дата добавления видео.</li>
</ul>

<h3 class="page-header">Получение ключа для Youtube</h3>
<p>Старый API, с которым можно было работать без ключей, больше не доступен, поэтому придется регистрировать аккаунт и получать ключ:</p>
<ol>
	<li>Идем сюда <a href="https://console.developers.google.com/" rel="nofollow" target="_blank">console.developers.google.com/</a></li>
	<li>Создаем проект.</li>
	<li>В разделе APIs выбираем YouTube Data API, нажимаем Enable API.</li>
	<li>В разделе Credentials нажимаем Create New Key, выбираем Browser Key и сразу Create (в текстовое поле ничего писать не нужно).</li>
	<li>Копируем API Key и вставляем в настройки плагина.</li>
</ol>