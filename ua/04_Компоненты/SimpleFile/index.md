
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>SimpleFiles - прикріплюємо до сторінки файли </h3>
SimpleFiles - прикріплюємо до сторінки файли Evolution CMS.
<p>Ще одне доповнення на базі DocLister і EasyUI. Цього разу до сторінки прикріплюються файли і редагуються в таблиці </span> – як в MultiFiles, але трохи зручніше (особлив, коли йде мова про велику кількість файлів) (:</p>
<p>Для роботи необхідна наявність<a href="https://github.com/AgelxNash/DocLister" rel="nofollow" target="_blank">DocLister і MODxAPI</a>, а також PHP не менше 5.6.</p>
<p>Завантажувати тут: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/SimpleFiles" rel="nofollow" target="_blank">Pathologic</a></p>
<h3 class="sub-header">Налаштування плагіну</h3>
<ul>
	<li><span class="text-bold">Tab name</span> – назва вкладки;</li>
	<li><span class="text-bold">Controller class</span> – клас контролера відмінний від стандартного;</li>
	<li><span class="text-bold">Templates</span> – id шаблонів, з якими працює плагін, <strong>обов'язково</strong>;</li>
	<li><span class="text-bold">Documents</span> – те ж саме, але для окремих ресурсів;</li>
	<li><span class="text-bold">Ignore Documents</span> – id ресурсів що виключаються;</li>
	<li><span class="text-bold">Roles</span> – id дозволених ролей;</li>
	<li><span class="text-bold">Storage folder</span> – папка, в якій зберігаються файли, за замовчуванням assets/storage/;</li>
	<li><span class="text-bold">Icons folder</span> – папка, в якій зберігаються іконки файлів, за замовчуванням assets/snippets/simplefiles/icons/;</li>
	<li><span class="text-bold">Allowed files</span> – розширення файлів, дозволених для завантаження, через кому; якщо не вказувати, то будуть використані системні налаштування;</li>
</ul>
<p>Maximum file size</span> – обмеження розміру файлу, в мегабайтах.</p>
<p>Іконки повинні іменуватися як <em>розширення_файлу_рядковими_буквами.png</em></p>
<p>Іконка file.png підставляється, якщо не знайшлось підходящої.</p>

<h3 class="sub-header">Вивід записів</h3>
<p>Після виводу записів читаємо про <a href="simplegallery/index.html" rel="nofollow" target="_blank">SimpleGallery</a>.</p>
<p>При виведенні через сніпети-обгортки sfLister і sfController доступні додатково віртуальні плейсхолдери:</p>
<ul>
	<li><span class="text-bold">[+icon+]</span> – Іконка;</li>
	<li><span class="text-bold">[+fSize+]</span> – відформатоване значення розміру;</li>
	<li><span class="text-bold">[+mime+]</span> – MIME-тип файлу;</li>
	<li><span class="text-bold">[+ext+]</span> – розширення файлу;</li>
	<li><span class="text-bold">[+filename+]</span> – ім'я файлу без розширення;</li>
	<li><span class="text-bold">[+basename+]</span> – ім'я файлу з розширенням;</li>
	<li><span class="text-bold">[+e.sf_title+]</span> – назва файлу з екрануванням символів;</li>
	<li><span class="text-bold">[+e.sf_description+]</span> – опис файлу з екрануванням символів.</li>
</ul>

<h3 class="sub-header">Поля в таблиці sf_files:</h3>
<ul>
	<li><span class="text-bold">sf_id</span> – id файлу (idField);</li>
	<li><span class="text-bold">sf_index</span> – позиція в списку;</li>
	<li><span class="text-bold">sf_title</span> – назва файлу;</li>
	<li><span class="text-bold">sf_description</span> – опис файлу;</li>
	<li><span class="text-bold">sf_file</span> – посилання на файл;</li>
	<li><span class="text-bold">sf_size</span> – розмір файлу;</li>
	<li><span class="text-bold">sf_isactive</span> – прапорець, щоб приховати якісь файли з виведення;</li>
	<li><span class="text-bold">sf_rid</span> – id ресурсу, якому належить файл (parentField);</li>
	<li><span class="text-bold">sf_createdon</span> – дата додавання файлу.</li>
</ul>
