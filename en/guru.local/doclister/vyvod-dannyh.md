
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: Вывод данных</h2>

<h3 class="sub-header text-bold">Задание шаблонов</h3>
<p>По умоланию считается, что в параметрах шаблона передано имя чанка. Но если имя чанка начинается с символа @, то происходит сверка начального слова в имени шаблона с заранее зарезервироваными правилами загрузки шаблонов. Все последующие слова используется в качестве параметра к выбранному правилу.</p>
<p><span class="text-bold">@FILE</span> Загрузка шаблона из html файла расположенного в папке или подпапках assets/templates/</p>
<p><span class="text-bold">@CHUNK</span> Обычная загрузка шаблона из чанка</p>
<p><span class="text-bold">@TPL, @CODE</span> Значение параметра используется в роли inline шаблона</p>
<p><span class="text-bold">@DOCUMENT, @DOC</span> Шаблон берется из content поля указанного документа</p>
<p><span class="text-bold">@PLH, @PLACEHOLDER</span> Шаблон загружается из глобального плейсхолдера MODX</p>
<p><span class="text-bold">@CFG, @CONFIG, @OPTIONS</span> Шаблон берется из глобальных настроек текущей установки MODX Evolution</p>
<p>Стоит заметить, что даже если начальный символ был @ и после обработки всех правил шаблон все равно оказался пустым, то происходит попытка обнаружить чанк по полному имени шаблона</p>

<h3 class="sub-header text-bold">Плейсхолдеры в DocLister:</h3>
<ul>
<li>плейсхолдер таблицы, имя такого плейсхолдера совпадает с названием колонки в таблице;</li>
<li>виртуальный плейсхолдер, который стал доступен после запуска экстендера или каких-то вычислений внутри контроллера;</li>
<li>глобальный плейсхолдер, который доступен из вне шаблонов передаваемых в сниппет (как правило имеет префикс dl и может быть переопределен при помощи параметров sysKey или id).</li>
</ul>
<blockquote>
<p>Экстендер в DocLister - это вспомогательный класс для каких-либо обработок, не имеет ничего общего с экстендерами Ditto.</p>
</blockquote>

<h3 class="sub-header text-bold">Плейсхолдеры таблицы</h3>
<p>Если указан контроллер site_content или любой другой его расширяющий, то по умолчанию используется таблица site_content. В случае с контроллером onetable имя таблицы определяется параметром table. Таким образом, получить полный список плейсхолдеров можно открыв таблицу mysql, например, через phpmyadmin и подсмотрев какие в этой таблице имеются поля.</p>

<h3 class="sub-header text-bold">Виртуальный плейсхолдер</h3>

<h4 class="text-bold">Плейсхолдеры устанавливаемые экстендером paginate</h4>
<p><span class="text-bold">[+параметр_id.pages+]</span> Пагинация</p>
<p><span class="text-bold">[+параметр_id.totalPages+]</span> Общее число страниц</p>
<p><span class="text-bold">[+параметр_id.isstop+]</span> 1 если текущая страница – последная</p>
<p><span class="text-bold">[+параметр_idisstart+]</span> 1 если текущая страница – первая</p>

<h4 class="text-bold text-info">Плейсхолдеры устанавливаемые экстендером jotcount</h4>
<p>Экстендер загружается, если при вызове сниппета задан параметр <span class="text-bold">&amp;jotcount</span>.</p>
<p><span class="text-bold">[+jotcount+]</span> Число комментариев из сниппета JOT</p>

<h4 class="text-bold text-info">Плейсхолдеры устанавливаемые экстендером tv</h4>
<p><span class="text-bold">[+tv.имяТВпараметра+]</span> Значение ТВ параметра</p>
<p>По умолчанию ко всем ТВ параметрам добавляется префикс tv, но от него можно избавиться или переопределить параметром tvPrefix.</p>

<h4 class="text-bold text-info">Плейсхолдеры устанавливаемые экстендером e</h4>
<p>Экстендер загружается, если при вызове сниппета задан параметр <span class="text-bold">&amp;е=<code>имена полей через запятую</code></span></p>
<p><span class="text-bold">[+e.имяПоля+]</span> Экранированное значение поля.</p>

<h4 class="text-bold text-info">Плейсхолдеры устанавливаемые экстендером summary</h4>
<p><span class="text-bold">[+summary+]</span> Аннотация к странице</p>

<h4 class="text-bold text-info">Плейсхолдеры устанавливаемые экстендером user</h4>
<p>Экстендер необходимо загрузить вручную, указав его имя в параметре &amp;extender. Также должны быть заданы параметры:</p>
<ul>
<li>usertype - <span class="text-bold">Возможные значения</span>: manager, mgr, web. Определяет из каких таблиц брать данные пользователей;</li>
<li>userFields - названия колонок через запятую, в которых указан id пользователя, например createdby, publishedby.</li>
</ul>
<p><span class="text-bold">[+user.id.НазваниеКолонки+]</span> ID пользователя</p>
<p><span class="text-bold">[+user.username.НазваниеКолонки+]</span> Логин пользователя</p>
<p><span class="text-bold">[+user.fullname.НазваниеКолонки+]</span> Полное имя пользователя</p>
<p><span class="text-bold">[+user.role.НазваниеКолонки+]</span> ID роли пользователя</p>
<p><span class="text-bold">[+user.email.НазваниеКолонки+]</span> e-mail</p>
<p><span class="text-bold">[+user.phone.НазваниеКолонки+]</span> Телефон</p>
<p><span class="text-bold">[+user.mobilephone.НазваниеКолонки+]</span> Мобильный телефон</p>
<p><span class="text-bold">[+user.blocked.НазваниеКолонки+]</span> Статус блокировки</p>
<p><span class="text-bold">[+user.blockeduntil.НазваниеКолонки+]</span> До какого UNIX-времени пользователь будет заблокирован</p>
<p><span class="text-bold">[+user.blockedafter.НазваниеКолонки+]</span> После какого UNIX-времени пользователь будет заблокирован</p>
<p><span class="text-bold">[+user.logincount.НазваниеКолонки+]</span> Общее число авторизаций</p>
<p><span class="text-bold">[+user.lastlogin.НазваниеКолонки+]</span> UNIX-время последней авторизации</p>
<p><span class="text-bold">[+user.thislogin.НазваниеКолонки+]</span> UNIX-время текущей авторизации</p>
<p><span class="text-bold">[+user.failedlogincount.НазваниеКолонки+]</span> Число неудачных попыток авторизоваться</p>
<p><span class="text-bold">[+user.lastlogin.НазваниеКолонки+]</span> UNIX-время последней авторизации</p>
<p><span class="text-bold">[+user.dob.НазваниеКолонки+]</span> Дата рождения</p>
<p><span class="text-bold">[+user.gender.НазваниеКолонки+]</span> Пол</p>
<p><span class="text-bold">[+user.country.НазваниеКолонки+]</span> Страна</p>
<p><span class="text-bold">[+user.state.НазваниеКолонки+]</span> Регион</p>
<p><span class="text-bold">[+user.zip.НазваниеКолонки+]</span> Почтовый индекс</p>
<p><span class="text-bold">[+user.fax.НазваниеКолонки+]</span> Факс</p>
<p><span class="text-bold">[+user.photo.НазваниеКолонки+]</span> Фотография</p>
<p><span class="text-bold">[+user.comment.НазваниеКолонки+]</span></p>

<h4 class="text-bold text-info">Плейсхолдеры устанавливаемые в контроллерах site_content</h4>
<p><span class="text-bold">[+title+]</span> Название документа для списков. Если menutitle пуст, то используется pagetitle</p>
<p><span class="text-bold">[+iteration+]</span>, <span class="text-bold">[+full_iteration+]</span> Порядковый номер элемента в списке; порядковый номер в списке с учетом пагинации.</p>
<p><span class="text-bold">[+url+]</span> Ссылка на документ</p>
<p><span class="text-bold">[+date+]</span> дата публикации документа сформированая по правилам указаным в параметре dateFormat (по умолчанию %d.%b.%y %H:%M). Помимо этого учитывается server_offset_time в настройках движка.</p>
<p><span class="text-bold">[+ЗначениеПараметраsysKey.active+]</span> Флаг определяющий, что обрабатываемый документ совпадает и документ на котором был вызван сниппет это одно и тоже (1 - если правда, 0 если нет)</p>
<p><span class="text-bold">[+ЗначениеПараметраsysKey.class+]</span> Классы которые могут быть автоматически присвоены документу (first, last, current, odd, even)</p>
<p><span class="text-bold">[+ЗначениеПараметраsysKey.wrap+]</span> HTML код списка подготовленный для вывода пользователю (используется только для шаблона ownerTPL)</p>

<h3>Параметры для установки плейсхолдеров</h3>
<h3 class="sub-header text-bold">&amp;sysKey</h3>
<p>Префикс для системных плейсхолдеров.</p>
<p><span class="text-bold">Возможные значения</span> - любая строка. На выходе получается плейсхолдер с именем [+sysKey.placeholder+], где sysKey это значение данного параметра</p>
<p><span class="text-bold">Значение по умолчанию</span> - dl</p>

<h3 class="sub-header text-bold">&amp;id</h3>
<p>Префикс для локальных плейсхолдеров.</p>
<p><span class="text-bold">Возможные значения</span> - любая строка. Если id указано, то на выходе получается [+id.placeholder+]. Где id это и есть переданое значение. В случае если id не задано, то перед именем плейсхолдера точка не ставится.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>

<h2 class="page-header">Параметры вывода в шаблоны</h2>

<h3 class="sub-header text-bold">&amp;ownerTPL</h3>
<p>Шаблон в который оборачивается список результатов. Если подходящих результатов не обнаружено, то по умолчанию результат с шаблоном noneTPL тоже оборачивается в этот шаблон. За подробностями обращайтесь к описанию параметра noneWrapOuter.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>
<p>Пример:</p>
<pre class="brush: html;">
&amp;ownerTPL=`@CODE:
&lt;ul class="pages-list"&gt;
	[+dl.wrap+]
&lt;/ul&gt;`
</pre>

<h3 class="sub-header text-bold">&amp;tpl</h3>
<p>Шаблон.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister. Значение параметра может быть изменено из prepare-сниппета c помощью свойства $_DocLister-&gt;renderTPL.</p>
<p><span class="text-bold">Значение по умолчанию</span> - определяется в контроллере.</p>
<p>Пример:</p>
<pre class="brush: html;">
&amp;tpl=`@CODE:
&lt;li&gt;
	&lt;img src="[+tv.image+]" alt="[+e.pagetitle+]"&gt;
	&lt;a href="[+url+]"&gt;[+title+] ([+id+])&lt;/a&gt;
&lt;/li&gt;`
</pre>

<h3 class="sub-header text-bold">&amp;tplId0, &amp;tplId1, &amp;tplId2, ..., &amp;tplIdN</h3>
<p>Шаблон для оформления блока с документами под номером 1, 2 и т.д...</p>
<p><span class="text-bold">Значение по умолчанию</span> берется из значения параметра tpl.</p>

<h3 class="sub-header text-bold">&amp;tplOdd, &amp;tplEven</h3>
<p>Шаблон для оформления блока с документами под четным/нечетным номером.</p>
<p><span class="text-bold">Значение по умолчанию</span> берется из значения параметра tpl.</p>

<h3 class="sub-header text-bold">&amp;tplFirst</h3>
<p>Шаблон для оформления первого блока с документами в списке. Синоним параметра tplId1, но имеет больший приоритет.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister. Если не задано, то совпадает с шаблоном tpl.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>

<h3 class="sub-header text-bold">&amp;tplLast</h3>
<p>Шаблон для оформления последнего блока с документами в списке.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister. Если не задано, то совпадает с шаблоном tpl.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>

<h3 class="sub-header text-bold">&amp;tplСurrent</h3>
<p>Шаблон для оформления блока с текущим документом в списке документов.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister. Если не задано, то совпадает с шаблоном tpl.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>

<h3 class="sub-header text-bold">&amp;noneTPL</h3>
<p>Шаблон с уведомлением о том, что по заданным критериям ничего не обнаружено.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span> - пусто.</p>

<h3 class="sub-header text-bold">&amp;noneWrapOuter</h3>
<p>Оборачивать ли ответ noneTPL в шаблон ownerTPL. Параметр актуален только в том случае, если нет документов для построения списка и задан ownerTPL.</p>
<p><span class="text-bold">Возможные значения</span> - 1 или 0.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 1.</p>

<h2 class="page-header">Пагинация</h2>

<h3 class="sub-header text-bold">&amp;paginate</h3>
<p>Вывод данных с пагинацией. Смотрите плейсхолдеры устанавливаемые экстендером paginate.</p>
<p><span class="text-bold">Возможные значения</span>:</p>
<ul>
<li>offset - пагинация в стиле Ditto;</li>
<li>pages - пагинация с прострелами.</li>
</ul>
<p><span class="text-bold">Значение по умолчанию</span> - pages.</p>

<h3 class="sub-header text-bold">&amp;TplFirstP</h3>
<p>Шаблон для вставки ссылки "первая страница".</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>: пусто.</p>

<h3 class="sub-header text-bold">&amp;TplLastP</h3>
<p>Шаблон для вставки ссылки "последняя страница".</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>: пусто.</p>

<h3 class="sub-header text-bold">&amp;TplNextP</h3>
<p>Шаблон для вставки ссылки "следующая страница".
<span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: &lt;a href="[+link+]"&gt;' . $this-&gt;DocLister-&gt;getMsg('paginate.next', 'Next') . ' &gt;&lt;/a&gt;
</pre>
<p>Плейсхолдеров для подстановки данных из языкового пакета пока нет.</p>

<h3 class="sub-header text-bold">&amp;TplPrevP</h3>
<p>Шаблон для вставки ссылки "предыдущая страница".</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: &lt;a href="[+link+]"&gt;&lt; ' . $this-&gt;DocLister-&gt;getMsg('paginate.prev', 'Prev') . '&lt;/a&gt;
</pre>
<p>Плейсхолдеров для подстановки данных из языкового пакета пока нет.</p>

<h3 class="sub-header text-bold">&amp;TplPage</h3>
<p>Шаблон для вставки номера страницы в пагинатор.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: &lt;a href="[+link+]" class="page"&gt;[+num+]&lt;/a&gt;
</pre>

<h3 class="sub-header text-bold">&amp;TplCurrentPage</h3>
<p>Шаблон оформления текущей страницы в пагинаторе</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: &lt;b class="current"&gt;[+num+]&lt;/b&gt;
</pre>

<h3 class="sub-header text-bold">&amp;TplWrapPaginate</h3>
<p>Шаблон контейнер для обертки страниц пагинации.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: &lt;div class="[+class+]"&gt;[+wrap+]&lt;/div&gt;
</pre>

<h3 class="sub-header text-bold">&amp;pageLimit</h3>
<p>Число страниц отображаемое в пагинаторе.</p>
<p><span class="text-bold">Возможные значения</span> - целое число больше ноля.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 1.</p>

<h3 class="sub-header text-bold">&amp;pageAdjacents</h3>
<p>Максимальное число страниц слева и справа относительно текущей страницы.</p>
<p><span class="text-bold">Возможные значения</span> - целое число больше ноля.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 4.</p>

<h3 class="sub-header text-bold">&amp;PaginateClass</h3>
<p>Класс для контейнера в который будут вложены страницы пагинации.</p>
<p><span class="text-bold">Возможные значения</span> - любая строка сформированная по правилам для подстановки в HTML аттрибут тегов class.</p>
<p><span class="text-bold">Значение по умолчанию</span> - paginate.</p>

<h3 class="sub-header text-bold">&amp;PrevNextAlwaysShow</h3>
<p>Всегда показывать "следующая страница" и "предыдущая страница".</p>
<p><span class="text-bold">Возможные значения</span> - 1 или 0.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>

<h3 class="sub-header text-bold">&amp;TplFirstI</h3>
<p>Шаблон для вставки ссылки "первая страница", используется совместно с PrevNextAlwaysShow.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>: пусто.</p>

<h3 class="sub-header text-bold">&amp;TplLastI</h3>
<p>Шаблон для вставки ссылки "последняя страница", используется совместно с PrevNextAlwaysShow.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>: пусто.</p>

<h3 class="sub-header text-bold">&amp;TplNextI</h3>
<p>Шаблон для вставки неактивной ссылки "следующая страница", используется совместно с PrevNextAlwaysShow.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: [%paginate.next%] &gt;
</pre>

<h3 class="sub-header text-bold">&amp;TplPrevI</h3>
<p>Шаблон для вставки неактивной ссылки "предыдущая страница", используется совместно с PrevNextAlwaysShow.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: &lt; [%paginate.prev%]
</pre>

<h3 class="sub-header text-bold">&amp;TplDotsPage</h3>
<p>Шаблон прострела.</p>
<p><span class="text-bold">Возможные значения</span> - имя шаблона указанное по правилам задания шаблонов в DocLister.</p>
<p><span class="text-bold">Значение по умолчанию</span>:</p>
<pre class="brush: html;">
@CODE: ...
</pre>

<h3 class="sub-header text-bold">&amp;noRedirect</h3>
<p>Запрещает переадресацию при запросе несуществующей страницы.</p>
<p><span class="text-bold">Возможные значения</span> - 0 или 1.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>

<h2 class="page-header">Вывод в плейсхолдеры</h2>
<h3 class="sub-header text-bold">&amp;contentPlaceholder</h3>
<p>Установка значений документов в персонализованные плейсхолдеры.</p>
<p><span class="text-bold">Возможные значения</span> - 0, 1. Если значение параметра равно 1, то DocLister создает плейсхолдеры вида [+id.item[x]+]. Где x это порядковый номер документа в списке, а id это значение параметра id (см. описание параметра id).</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0</p>

<h2 class="page-header">API-режим</h2>
<h3 class="sub-header text-bold">&amp;api</h3>
<p>Используется для формирования выдачи в формате JSON.</p>
<p><span class="text-bold">Возможные значения</span> - 0, 1 или список полей выбираемых документов.</p>
<p><span class="text-bold">Значение по умолчанию</span> - 0.</p>

<h3 class="sub-header text-bold">&amp;JSONformat</h3>
<p>По какому принципу формировать JSON-ответ.</p>
<p><span class="text-bold">Возможные значения</span> - old, new. В формате old ответ выглядит в виде обычного массива. В формате new ответ заворачивается в rows секцию + добавляется примесь total в которой указано общее число учавствующих в выборке</p>
<p><span class="text-bold">Значение по умолчанию</span> - old.</p>