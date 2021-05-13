
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>SimpleTube - плагін і сніппет для створення відеогалерей </h3>
SimpleTube - плагін і сніппет для створення відеогалерей.
<p>Основних відмінностей всього дві, проте мені здається, вони достатньо суттєві, щоб змінити назву:</p>
<ul>
	<li>тепер використовується окрема таблиця для зберігання данних, замість TV-параметра з json;</li>
	<li>новий зручний інтерфейс з jQuery EasyUI</li>
</ul>
<p>Для роботи всього цього необхіна наявність <a href="https://github.com/AgelxNash/DocLister" rel="nofollow" target="_blank">DocLister і MODxAPI</a>, а також PHP 5.6.</p>
<p>Скачати тут: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/SimpleTube" rel="nofollow" target="_blank">Pathologic</a></p>
<p><span class="text-bold">Сніппет</span> уміє находити за допомогою классу <a href="http://frandieguez.github.io/panorama-php/" rel="nofollow" target="_blank">Panorama-PHP</a> інформацію про відео за посиланням, а також при можливості скачати Зображення-прев'ю. Підтримуються youtube, rutube, vimeo, metacafe і dailymotion. Взагалі класс підтримує більше відеохостингів, але це в теорії; тому я залишив тільки те, що більш-менш працює (при цьому, наприклад, про metacafe і dailymotion я ні разу не чув).</p>
<p>З допомогою цього сніппета плагін отримує інформацію для додавання в таблицю, але нічого не заважає використовувати його без плагіна, як сніппет getVideo з MultiVideos.</p>
<h3 class="sub-header">Параметри Сніппета:</h3>
<ul>
	<li><span class="text-bold">&input</span> – посилання;</li>
	<li><span class="text-bold">&forceDownload</span> – якщо 1, то завжди скачувати прев'ю, якщо 0, то тільки в тому випадку, якщо зображення немає в папці; за замовчуванням – 0;</li>
	<li><span class="text-bold">&folder</span> – папка для зберігання прев'ю; за замовчуванням – assets/images/video/;</li>
	<li><span class="text-bold">&noImage</span> – шлях до зображення, котре виводиться в режимі &api=`0` при відсутності прев'ю; за замовчуванням – assets/snippets/simpletube/noimage.png;</li>
	<li><span class="text-bold">&api</span> – якщо 0, то виводиться чанк &tpl, 1 – json, 2 – массив; за замовчуванням – 0;</li>
	<li><span class="text-bold">&tpl</span> – чанк для виведення в режимі &api=`0`, вказується так само, як в DocLister. Доступні плейсхолдері: [+st_title+] (назва відео), [+st_thumbUrl+] (посилання на прев'ю або зображення noImage), [+st_embedUrl+] (посилання для вбудови), [+st_service+] (назва відеохостинга), [+st_duration+] (довжина відео, секунд);</li>
	<li><span class="text-bold">&ytApiKey</span> – ключ для роботи з Youtube, якщо параметр не вказаний, то сніппет намагатиметься отримати це значення з налаштувань плагіна.</li>
</ul>
<h3 class="sub-header">Параметри Плагіна:</h3>
<p>Плагін використовується для керування галереями на сторінці ресурсу.</p>
<ul>
	<li><span class="text-bold">Tab name</span> – назва вкладки;</li>
	<li><span class="text-bold">Templates</span> – id шаблонів ресурсів з відео, <span class="text-bold">обов'язковоо</span> – ;</li>
	<li><span class="text-bold">Roles</span> – id дозволених ролей;</li>
	<li><span class="text-bold">Thumbs folder</span> – папка для прев'ю;</li>
	<li><span class="text-bold">Thumbs cache folder</span> – папка для прев'ю прев'ю (:</li>
	<li><span class="text-bold">No image picture</span> – зображення, якщо немає прев'ю;</li>
	<li><span class="text-bold">Thumbs width</span> – її ширина;</li>
	<li><span class="text-bold">Thumbs height</span> – і висота;</li>
	<li><span class="text-bold">Force download</span> – скачувати прев'ю завжди або при необхідності;</li>
	<li><span class="text-bold">Youtube API Key</span> – ключ для работы з YouTube.</li>
</ul>
<p>Вивід такий ж, як в SimpleGallery – c поправкой на назву таблиці і полей. Тому дивитись <a href="http://modx.im/blog/docs/2762.html" rel="nofollow" target="_blank">тут</a>.</p>
<h3 class="sub-header">Поля в таблиці st_videos:</h3>
<ul>
	<li><span class="text-bold">st_id</span> – id відео (idField);</li>
	<li><span class="text-bold">st_index</span> – позиція в списку;</li>
	<li><span class="text-bold">st_title</span> – назва відео;</li>
	<li><span class="text-bold">st_videoUrl</span> – вихідне посилання на відео;</li>
	<li><span class="text-bold">st_thumbUrl</span> – посилання на прев'ю;</li>
	<li><span class="text-bold">st_embedUrl</span> – посилання для вбудови;</li>
	<li><span class="text-bold">st_duration</span> – довжина відео, секунди;</li>
	<li><span class="text-bold">st_isactive</span> – прапорець, щоб приховати якісь відео з виведення;</li>
	<li><span class="text-bold">st_service</span> – назва відеохостинга;</li>
	<li><span class="text-bold">st_rid</span> – id ресурсу, котрому належить відео (parentField).</li>
	<li><span class="text-bold">st_createdon</span> – дата додавання відео.</li>
</ul>

<h3 class="page-header">Отримання ключа для Youtube</h3>
<p>Старий API, з котрим можна було працювати без ключів, більше не доступний, тому прийдеться реєструвати аккаунт і отримати ключ:</p>
<ol>
	<li>ІдемО сюдИ <a href="https://console.developers.google.com/" rel="nofollow" target="_blank">console.developers.google.com/</a></li>
	<li>Створюємо проєкт.</li>
	<li>В розділі APIs вибираємо YouTube Data API, нажимаєм Enable API.</li>
	<li>В розділі Credentials нажимаєм Create New Key, вибираємо Browser Key і відразу Create (в текстове поле нічого писати не потрібно).</li>
	<li>Копируем API Key и вставляємо в налаштування плагіна.</li>
</ol>
