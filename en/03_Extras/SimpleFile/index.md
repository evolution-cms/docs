
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>SimpleFiles - прикрепляем к странице файлы </h3>
SimpleFiles - прикрепляем к странице файлы Evolution CMS.
<p>Еще одно дополнение на базе DocLister и EasyUI. На этот раз к странице прикрепляются файлы и редактируются в таблице</span> – как в MultiFiles, но немного удобнее (особенно если речь идет о большом количестве файлов) (:</p>
<p>Для работы необходимо наличие <a href="https://github.com/AgelxNash/DocLister" rel="nofollow" target="_blank">DocLister и MODxAPI</a>, а также PHP не меньше 5.6.</p>
<p>Скачивать здесь: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Pathologic/SimpleFiles" rel="nofollow" target="_blank">Pathologic</a></p>
<h3 class="sub-header">Настройки плагина</h3>
<ul>
	<li><span class="text-bold">Tab name</span> – название вкладки;</li>
	<li><span class="text-bold">Controller class</span> – класс контроллера отличный от стандартного;</li>
	<li><span class="text-bold">Templates</span> – id шаблонов, с которыми работает плагин, <strong>обязательно</strong>;</li>
	<li><span class="text-bold">Documents</span> – то же самое, но для отдельных ресурсов;</li>
	<li><span class="text-bold">Ignore Documents</span> – id исключаемых ресурсов;</li>
	<li><span class="text-bold">Roles</span> – id разрешенных ролей;</li>
	<li><span class="text-bold">Storage folder</span> – папка, где хранятся файлы, по умолчанию assets/storage/;</li>
	<li><span class="text-bold">Icons folder</span> – папка, в которой хранятся иконки файлов, по умолчанию assets/snippets/simplefiles/icons/;</li>
	<li><span class="text-bold">Allowed files</span> – расширения файлов, разрешенных для загрузки, через запятую; если не указывать, то будет использована системная настройка;</li>
</ul>
<p>Maximum file size</span> – ограничение размера файла, в мегабайтах.</p>
<p>Иконки должны именоваться как <em>расширение_файла_строчными_буквами.png</em></p>
<p>Иконка file.png подставляется, если не нашлось подходящей.</p>

<h3 class="sub-header">Вывод записей</h3>
<p>По выводу записей читаем про <a href="simplegallery/index.html" rel="nofollow" target="_blank">SimpleGallery</a>.</p>
<p>При выводе через сниппеты-обертки sfLister и sfController доступны дополнительно виртуальные плейсхолдеры:</p>
<ul>
	<li><span class="text-bold">[+icon+]</span> – иконка;</li>
	<li><span class="text-bold">[+fSize+]</span> – отформатированное значение размера;</li>
	<li><span class="text-bold">[+mime+]</span> – MIME-тип файла;</li>
	<li><span class="text-bold">[+ext+]</span> – расширение файла;</li>
	<li><span class="text-bold">[+filename+]</span> – имя файла без расширения;</li>
	<li><span class="text-bold">[+basename+]</span> – имя файла с расширением;</li>
	<li><span class="text-bold">[+e.sf_title+]</span> – название файла с экранированием символов;</li>
	<li><span class="text-bold">[+e.sf_description+]</span> – описание файла с экранированием символов.</li>
</ul>

<h3 class="sub-header">Поля в таблице sf_files:</h3>
<ul>
	<li><span class="text-bold">sf_id</span> – id файла (idField);</li>
	<li><span class="text-bold">sf_index</span> – позиция в списке;</li>
	<li><span class="text-bold">sf_title</span> – название файла;</li>
	<li><span class="text-bold">sf_description</span> – описание файла;</li>
	<li><span class="text-bold">sf_file</span> – ссылка на файл;</li>
	<li><span class="text-bold">sf_size</span> – размер файла;</li>
	<li><span class="text-bold">sf_isactive</span> – флажок, чтобы скрыть какие-то файлы из вывода;</li>
	<li><span class="text-bold">sf_rid</span> – id ресурса, которому принадлежит файл (parentField);</li>
	<li><span class="text-bold">sf_createdon</span> – дата добавления файла.</li>
</ul>