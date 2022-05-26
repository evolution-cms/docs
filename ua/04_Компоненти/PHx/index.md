<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>PHx Додаткові можливості для тегів MODX Evolution</h3>
Додаткові можливості для відображення плейсхолдерів, тегів MODx (включаючи параметри TV) і теги налаштувань сайту.
<p>PHx (Placeholders Xtended) додає нові можливості для відображення плейсхолдерів, тегів MODx (включаючи TV параметри) та теги налаштувань сайту. Рекурсивний парсер дає змогу використовувати вкладені теги. Можна створювати свої модифікатори шляхом створення сніппетів.</p>
<p>PHx підтримує такі теги MODx:</p>
<pre class="brush: html;">
[+placeholder+]
[*теги вмісту*] ([*content*], [*pagetitle*], наприклад)
[*TV параметри*]
[(теги налаштування)] (наприклад, [(base_url)], [(site_name)] та інші)
</pre>
<h3 class="sub-header text-bold">Використання</h3>
<p>Звичайний плейсхолдер виду <code>[+placeholder+]</code> легко перетворюється на плейсхолдер PHx: <code>[+placeholder:esc+]</code>. Те саме можна зробити з тегом вмісту:</p>
<p><code>[*createdby*]</code></p>
<p>Додаємо модифікатор:</p>
<pre class="brush: html;">[*createdby:date=`%a %B %d, %Y at %H:%M`*]</pre>
<p>Також можна використовувати кілька модифікаторів одразу. Вони будуть оброблені ліворуч:</p>
<pre class="brush: html;">somevar:esc:nl2br:strip</pre>
<h4>Розширене застосування</h4>
<p>Наявність спеціального плейсхолдера "phx" дозволяє використовувати синтаксис PHx без реальної змінної.</p>
<pre class="brush: html;">[+phx:if=`[+this+]`:is=`[+that+]`:then=`do this`:else=`do that`+]</ pre>
<p>З деякими модифіакторами цей плейсхолдер набуває певного значення. У випадку модифікатора "userinfo" він повертає відповідне значення з інформації про поточного користувача:</p>
<p><code>[+phx:userinfo=`username`+]</code></p>
<h5>Синтаксис</h5>
<p>Хоч це і здається логічним, але на цьому варто загострити увагу. Уникайте використання наступних конструкцій у шаблоні, якщо вони не є частиною тегу MODx:</p>
<pre class="brush: html;">
[+
[*
[(
+]
*]
)]
]]
</pre>
<p>Парсер спробує їх обробити та MODx видасть помилку. Зазвичай такої проблеми немає. Але у випадку з JavaScript у вас може бути конструкція, подібна до цієї:</p>
<code>array[counter++]</code>
<p>що спровокує дивну поведінку через +].</p>
<p>Також CDATA, що закриває тег, може створити проблеми.</p>
<code>/* ]]&gt; */</code>
<p>Пам'ятайте, що ви не зможете втратити дані вашого сайту, використовуючи неправильний синтаксис PHx. Найгірше, що може статися, - ваш шаблон неправильно відобразиться.</p>

<h2 class="page-header">Модифікатори</h2>
<h3 class="sub-header text-bold"><span class="text-bold">lcase</span></h3>
<p>- Повертає рядок, наведений до нижнього регістру.</p>
<pre class="brush: html;">[+string:lcase+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">ucase</span></h3>
<p>- Приведе всі символи рядка до верхнього регістру.</p>
<pre class="brush: html;">[+ucase:lcase+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">ucfirst</span></h3>
<p>- Перша літера в рядку стане великою.</p>
<pre class="brush: html;">[+ucfirst:lcase+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">ellipsis</span></h3>
<p>- Обрізає рядок.</p>
<pre class="brush: html;">[+description:ellipsis=`150`]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">length | len</span></h3>
<p>- Поверне довжину рядка.</p>
<pre class="brush: html;">[+string:len+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">notags</span></h3>
<p>- Виріже всі HTML теги з рядка.</p>
<pre class="brush: html;">[+string:notags+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">esc</span></h3>
<p>- Видаляє html теги та розриви рядків</p>
<pre class="brush: html;">[+string:esc+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">htmlent</span></h3>
<p>- Конвертує вихідну змінну в html сутності. Аналог htmlentities() у PHP.</p>
<pre class="brush: html;">[+string:htmlent+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">nl2br</span></h3>
<p>- Конвертує символи перекладу рядка на теги.</p>
<pre class="brush: html;">[+string:nl2br+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">strip</span></h3>
<p>- Видалити символи нового рядка(\n), табулятори(\t), що йдуть пробіли підряд.</p>
<pre class="brush: html;">[+string:strip+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">reverse</span></h3>
<p>- Переверне задом навпаки літери.</p>
<pre class="brush: html;">[+string:reverse+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">wordwrap</span></h3>
<p>- Встановлює переноси в залежності від кількості символів слова, аналогічно функції php (За замовчуванням: 70).</p>
<pre class="brush: html;">[*pagetitle:wordwrap=`10`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">limit</span></h3>
<p>- Поверне перші символи X від поточного значення (За замовчуванням: 100).</p>
<pre class="brush: html;">[*pagetitle:limit=`50`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">date</span></h3>
<p>- Перетворює мітку часу unix timestamps відповідно до заданого формату.</p>
<pre class="brush: html;">[*createdon:date=`%d.%m.%Y`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">md5</span></h3>
<p>- Створює MD5-хеш поточного значення.</p>
<pre class="brush: html;">[*pagetitle:md5*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">userinfo</span></h3>
<p>- Повертає запитані модифікатори дані про користувача.</p>
<pre class="brush: html;">[+phx:userinfo=`username`+]</pre>
<ul>
<li><span class="text-bold">cachepwd</span>&nbsp;: Cache password</li>
<li><span class="text-bold">comment</span>&nbsp;: Comment</li>
<li><span class="text-bold">country</span>&nbsp;: Країна</li>
<li><span class="text-bold">dob</span>&nbsp;: Дата народження у форматі часу UNIX</li>
<li><span class="text-bold">email</span>&nbsp;: Email</li>
<li><span class="text-bold">fax</span>&nbsp;: Факс</li>
<li><span class="text-bold">fullname</span>&nbsp;: Повне ім'я</li>
<li><span class="text-bold">gender</span>&nbsp;: Пол</li>
<li><span class="text-bold">internalKey</span>&nbsp;: User internal key</li>
<li><span class="text-bold">lastlogin</span>&nbsp;: Last login, in UNIX time format</li>
<li><span class="text-bold">logincount</span>&nbsp;: Number of logins</li>
<li><span class="text-bold">mobilephone</span>&nbsp;: Мобільний телефон</li>
<li><span class="text-bold">password</span>&nbsp;: Пароль</li>
<li><span class="text-bold">phone</span>&nbsp;: Телефон</li>
<li><span class="text-bold">photo</span>&nbsp;: Фотографія</li>
<li><span class="text-bold">role</span>&nbsp;: Роль</li>
<li><span class="text-bold">state</span>&nbsp;: Статус</li>
<li><span class="text-bold">thislogin</span>&nbsp;: Цей сайт, в UNIX time format</li>
<li><span class="text-bold">username</span>&nbsp;: Логін</li>
<li><span class="text-bold">zip</span>&nbsp;: Поштовий індекс</li>
</ul>

<h3 class="sub-header text-bold"><span class="text-bold">math</span></h3>
<p>- Використовувати обчислення, такі, як - * + /.</p>
<p>"?" символ замінюється поточним значенням розширення, але також можна використовувати вкладені теги.</p>
<pre class="brush: html;">[+price:math=`?*[+curs+]`+] </pre>

<h3 class="sub-header text-bold"><span class="text-bold">ifempty</span></h3>
<p>- Використовувати "інше значення" якщо значення placeholder або templatevar порожнє.</p>
<pre class="brush: html;">[*longtitle:ifempty=`[*pagetitle*]`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">select</span></h3>
<p>- Приймає значення, залежно від значень placeholder або templatevar.</p>
<pre class="brush: html;">[+placeholder:select=`0=OFF&1=ON&2=UNKNOWN`+]</pre>

<h3 class="sub-header text-bold">Умовні вирази</h3>
<h3 class="sub-header text-bold"><span class="text-bold">is - одно (==)</span></h3>
<p>- аліаси: eq</p>
<h3 class="sub-header text-bold"><span class="text-bold">ne - не одно (!=)</span></h3>
<p>- аліаси: isnot, isnt</p>
<h3 class="sub-header text-bold"><span class="text-bold">eg - більше або одно (>=)</span></h3>
<p>- аліаси: isgt</p>
<h3 class="sub-header text-bold"><span class="text-bold">el - менше або одно (<=)</span></h3>
<p>- аліаси: islt</p>
<h3 class="sub-header text-bold"><span class="text-bold">gt - більше (>)</span></h3>
<p><span class="text-bold">lt - менше (<)</span> </h3>

<h3 class="sub-header text-bold"><span class="text-bold">mo=`Webgroups`</span></h3>
<p>- аліаси: isinrole, ir, memberof</p>
<p>Приймає як параметр розділений комами список веб-груп і повертає значення true/false залежно від того, чи належить поточний користувач до будь-якої з цих груп чи ні (замінює собою модифікатор <b>"inrole"</b> , який необхідно було поєднувати з умовним оператором).</p>
<pre class="brush: html;">[+phx:mo=`Адміністратори`:then=`Я адмін`:else=`Я простий смертний`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">if=`value`</span></h3>
<p>- Приймає як параметр змінну для порівняння. Також може бути використане у поєднанні з <code>:or</code> або <code>:and</code>.</p>
<pre class="brush: html;">[+phx:if=`[+price+]`:gt=`0`:then=`Ціна: [+price+]`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">or</span></h3>
<p>- Логічне АБО (перевіряється, чи вірна перша чи друга умова).</p>
<pre class="brush: html;">[+phx:if=`[*id*]`:is=`2`:or:is=`3`:then=`{{Chunk}}`:else =`{{OtherChunk}}`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">and</span></h3>
<p>- Логічне І (перевіряється, чи правильні обидві умови).</p>
<pre class="brush: html;">[+phx:if=`[!UltimateParent!]`:is=`1`:and:isnot=`[*id*]`:then=`{{ChildChunk} }`:else=`{{ParentChunk}}`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">then=`template`</span></h3>
<p>- Значення <span class="text-bold">template</span> відображається, коли всі умови правильні. Тут можна вказати виклик <code>{{чанка}}</code>, <code>[[сніппета]]</code> або чистий HTML.</p>
<h3 class="sub-header text-bold"><span class="text-bold">else=`template`</span></h3>
<p>- Значення <span class="text-bold">template</span> відображається, коли всі умови не правильні. Тут можна вказати виклик <code>{{чанка}}</code>, <code>[[сніппета]]</code> або чистий HTML.</p>

<h3 class="sub-header text-bold"><span class="text-bold">show</span></h3>
<p>- Використовується подібно до then, але як шаблон для виведення використовується вихідне значення. Виконується, якщо умови правильні.</p>
<pre class="brush: html;">[+myplaceholder:len:gt=`3`:show+]</pre>

<h2 class="page-header">Приклади</h2>
<pre class="brush: html;">
[+myplaceholder:is=`myvalue`:then=`Правильно`:else=`Неправильно`+]
</pre>
<pre class="brush: html;">
[+myplaceholder:isnot=`myvalue`:then=`Правильно`:else=`Неправильно`+]
[+myplaceholder:is=`othervalue`:then=`Правильно`:else=`Неправильно`+]
</pre>
<pre class="brush: html;">
[+myplaceholder:is=`2`:then=``:else=``+]
</pre>
<pre class="brush: html;">
[+myplaceholder:gt=`1`:then=`Yes`:else=`No`+]
[+myplaceholder:lt=`3`:and:gt=`1`:then=`Yes`:else=`No`+]
[+myplaceholder:lt=`[+someplaceholder+]`:then=`Yes`:else=`No`+]
[+myplaceholder:islt=`2`:then=`Yes`:else=`No`+]
[+myplaceholder:isnot=`2`:or:lt=`3`:then=`Yes`:else=`No`+]
</pre>
<pre class="brush: html;">
[+myplaceholder:isnot=`2`:then=`Yes`:else=`No`+]
[+myplaceholder:gt=`[+someplaceholder+]`:then=`Yes`:else=`No`+]
[+myplaceholder:lt=`2`:then=`Yes`:else=`No`+]
[+myplaceholder:gt=`2`:then=`Yes`:else=`No`+]
[+myplaceholder:lt=`1`:then=`Yes`:else=`No`+]
</pre>
