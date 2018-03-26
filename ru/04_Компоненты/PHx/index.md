
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>PHx Дополнительные возможности для тегов MODX Evolution</h3>
Дополнительные возможности для отображения плейсхолдеров, тегов MODx (включая TV параметры) и теги настроек сайта.
<p>PHx (Placeholders Xtended) добавляет новые возможности для отображения плейсхолдеров, тегов MODx (включая TV параметры) и теги настроек сайта. Рекурсивный парсер позволяет использовать вложенные теги. Возможно создавать свои модификаторы, путем создания сниппетов.</p>
<p>PHx поддерживает следующие теги MODx:</p>
<pre class="brush: html;">
[+placeholder+]
[*теги содержимого*] ([*content*], [*pagetitle*], например)
[*TV параметры*]
[(теги настройки)] (например, [(base_url)], [(site_name)] и другие)
</pre>
<h3 class="sub-header text-bold">Использование</h3>
<p>Обычный плейсхолдер вида <code>[+placeholder+]</code> легко превращается в плейсхолдер PHx: <code>[+placeholder:esc+]</code>. Тоже самое вы можете сделать с тегом содержимого:</p>
<p><code>[*createdby*]</code></p>
<p>Добавляем модификатор:</p>
<pre class="brush: html;">[*createdby:date=`%a %B %d, %Y at %H:%M`*]</pre>
<p>Также можно использовать несколько модификаторов сразу. Они будут обработаны слева направо:</p>
<pre class="brush: html;">somevar:esc:nl2br:strip</pre>
<h4>Расширенное применение</h4>
<p>Наличие специального плейсхолдера "phx" позволяет использовать синтаксис PHx без наличия реальной переменной.</p>
<pre class="brush: html;">[+phx:if=`[+this+]`:is=`[+that+]`:then=`do this`:else=`do that`+]</pre>
<p>С некоторыми модифиакторами этот плейсхолдер приобретает определенное значение. В случае с модификатором "userinfo" он возвращает соответствующее значение из информации о текущем пользователе:</p>
<p><code>[+phx:userinfo=`username`+]</code></p>
<h5>Синтаксис</h5>
<p>Хотя это и кажется логичным, но на этом стоит заострить внимание. Избегайте использования следующих конструкций в шаблоне, если они не являются частью тега MODx:</p>
<pre class="brush: html;">
[+
[*
[(
+]
*]
)]
]]
</pre>
<p>Парсер попытается их обработать и MODx выдаст ошибку. Обычно такой проблемы не возникает. Но в случае с JavaScript у вас может быть конструкция, похожая на эту:</p>
<code>array[counter++]</code>
<p>которая спровоцирует странное поведени из-за +].</p>
<p>Также закрывающий тег CDATA может создать проблемы.</p>
<code>/* ]]&gt; */</code>
<p>Помните, что вы не сможете потерять данные вашего сайта, используя неправильный синтаксис PHx. Худшее, что может случится - ваш шаблон неправильно отобразится.</p>

<h2 class="page-header">Модификаторы</h2>
<h3 class="sub-header text-bold"><span class="text-bold">lcase</span></h3>
<p>- Возвращает строку, приведенную к нижнему регистру.</p>
<pre class="brush: html;">[+string:lcase+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">ucase</span></h3>
<p>- Приведет все символы строки к верхнему регистру.</p>
<pre class="brush: html;">[+ucase:lcase+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">ucfirst</span></h3>
<p>- Первая буква в строке станет заглавной.</p>
<pre class="brush: html;">[+ucfirst:lcase+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">ellipsis</span></h3>
<p>- Обрежет строку.</p>
<pre class="brush: html;">[+description:ellipsis=`150`]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">length | len</span></h3>
<p>- Возвратит длину строки.</p>
<pre class="brush: html;">[+string:len+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">notags</span></h3>
<p>- Вырежет все HTML теги из строки.</p>
<pre class="brush: html;">[+string:notags+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">esc</span></h3>
<p>- Удаляет html теги и разрывы строк</p>
<pre class="brush: html;">[+string:esc+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">htmlent</span></h3>
<p>- Конвертирует исходную переменную в html сущности. Аналог htmlentities() в PHP.</p>
<pre class="brush: html;">[+string:htmlent+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">nl2br</span></h3>
<p>- Конвертирует символы перевода строки в теги.</p>
<pre class="brush: html;">[+string:nl2br+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">strip</span></h3>
<p>- Удалит символы новой строки(\n), табуляторы(\t), идущие подряд пробелы.</p>
<pre class="brush: html;">[+string:strip+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">reverse</span></h3>
<p>- Перевернет задом наоборот буквы.</p>
<pre class="brush: html;">[+string:reverse+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">wordwrap</span></h3>
<p>- Устанавливает переносы в зависимости от кол-ва символов слова, аналогично функции php (По умолчанию: 70).</p>
<pre class="brush: html;">[*pagetitle:wordwrap=`10`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">limit</span></h3>
<p>- Возвратит первые X символов от текущего значения (По умолчанию: 100).</p>
<pre class="brush: html;">[*pagetitle:limit=`50`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">date</span></h3>
<p>- Преобразует метку времени unix timestamps в соответствии с заданным форматом.</p>
<pre class="brush: html;">[*createdon:date=`%d.%m.%Y`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">md5</span></h3>
<p>- Создает MD5-хэш текущего значения.</p>
<pre class="brush: html;">[*pagetitle:md5*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">userinfo</span></h3>
<p>- Возвращает запрошенные модификаторов данные о пользователе.</p>
<pre class="brush: html;">[+phx:userinfo=`username`+]</pre>
<ul>
	<li><span class="text-bold">cachepwd</span>&nbsp;: Cache password</li>
	<li><span class="text-bold">comment</span>&nbsp;: Comment</li>
	<li><span class="text-bold">country</span>&nbsp;: Страна</li>
	<li><span class="text-bold">dob</span>&nbsp;: Дата рождения в формате времени UNIX</li>
	<li><span class="text-bold">email</span>&nbsp;: Email</li>
	<li><span class="text-bold">fax</span>&nbsp;: Факс</li>
	<li><span class="text-bold">fullname</span>&nbsp;: Полное имя</li>
	<li><span class="text-bold">gender</span>&nbsp;: Пол</li>
	<li><span class="text-bold">internalKey</span>&nbsp;: User internal key</li>
	<li><span class="text-bold">lastlogin</span>&nbsp;: Last login, in UNIX time format</li>
	<li><span class="text-bold">logincount</span>&nbsp;: Number of logins</li>
	<li><span class="text-bold">mobilephone</span>&nbsp;: Мобильный телефон</li>
	<li><span class="text-bold">password</span>&nbsp;: Пароль</li>
	<li><span class="text-bold">phone</span>&nbsp;: Телефон</li>
	<li><span class="text-bold">photo</span>&nbsp;: Фотография</li>
	<li><span class="text-bold">role</span>&nbsp;: Роль</li>
	<li><span class="text-bold">state</span>&nbsp;: Статус</li>
	<li><span class="text-bold">thislogin</span>&nbsp;: This login, in UNIX time format</li>
	<li><span class="text-bold">username</span>&nbsp;: Логин</li>
	<li><span class="text-bold">zip</span>&nbsp;: Почтовый индекс</li>
</ul>

<h3 class="sub-header text-bold"><span class="text-bold">math</span></h3>
<p>- Использовать вычисления, такие, как - * + /.</p>
<p>"?" символ заменяется текущим значением расширения, но вы также можете использовать вложенные теги.</p>
<pre class="brush: html;">[+price:math=`?*[+curs+]`+] </pre>

<h3 class="sub-header text-bold"><span class="text-bold">ifempty</span></h3>
<p>- Использовать "другое значение" если значение placeholder или templatevar пустое.</p>
<pre class="brush: html;">[*longtitle:ifempty=`[*pagetitle*]`*]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">select</span></h3>
<p>- Принимает значение, в зависимости от значений placeholder или templatevar.</p>
<pre class="brush: html;">[+placeholder:select=`0=OFF&1=ON&2=UNKNOWN`+]</pre>

<h3 class="sub-header text-bold">Условные выражения</h3>
<h3 class="sub-header text-bold"><span class="text-bold">is - равно (==)</span></h3>
<p>- алиасы: eq</p>
<h3 class="sub-header text-bold"><span class="text-bold">ne - не равно (!=)</span></h3>
<p>- алиасы: isnot, isnt</p>
<h3 class="sub-header text-bold"><span class="text-bold">eg - больше или равно (>=)</span></h3>
<p>- алиасы: isgt</p>
<h3 class="sub-header text-bold"><span class="text-bold">el - меньше или равно (<=)</span></h3>
<p>- алиасы: islt</p>
<h3 class="sub-header text-bold"><span class="text-bold">gt - больше (>)</span></h3>
<p><span class="text-bold">lt - меньше (<)</span> </h3>

<h3 class="sub-header text-bold"><span class="text-bold">mo=`Webgroups`</span></h3>
<p>- алиасы: isinrole, ir, memberof</p>
<p>Принимает в качестве параметра разделенный запятыми список веб-групп и возвращает значение true/false в зависимости от того, принадлежит текущий пользователь к какой-либо из этих групп или нет (заменяет собой модификатор <b>"inrole"</b>, который необходимо было сочетать с условным оператором).</p>
<pre class="brush: html;">[+phx:mo=`Администраторы`:then=`Я админ`:else=`Я простой смертный`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">if=`value`</span></h3>
<p>- Принимает в качестве параметра переменную для сравнения. Также может быть использовано в сочетании с <code>:or</code> или <code>:and</code>.</p>
<pre class="brush: html;">[+phx:if=`[+price+]`:gt=`0`:then=`Цена: [+price+]`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">or</span></h3>
<p>- Логическое ИЛИ (проверяется, верно ли первое или второе условие).</p>
<pre class="brush: html;">[+phx:if=`[*id*]`:is=`2`:or:is=`3`:then=`{{Chunk}}`:else=`{{OtherChunk}}`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">and</span></h3>
<p>- Логическое И (проверяется, верны ли оба условия).</p>
<pre class="brush: html;">[+phx:if=`[!UltimateParent!]`:is=`1`:and:isnot=`[*id*]`:then=`{{ChildChunk}}`:else=`{{ParentChunk}}`+]</pre>

<h3 class="sub-header text-bold"><span class="text-bold">then =`template`</span></h3>
<p>- Значение <span class="text-bold">template</span> отображается, когда все условия верны. Здесь можно указать вызов <code>{{чанка}}</code>, <code>[[сниппета]]</code> или же чистый HTML.</p>
<h3 class="sub-header text-bold"><span class="text-bold">else =`template`</span></h3>
<p>- Значение <span class="text-bold">template</span> отображается, когда все условия не верны. Здесь можно указать вызов <code>{{чанка}}</code>, <code>[[сниппета]]</code> или же чистый HTML.</p>

<h3 class="sub-header text-bold"><span class="text-bold">show</span></h3>
<p>- Используется подобно then, но в качестве шаблона для вывода используется исходное значение. Выполняется, если условия верны.</p>
<pre class="brush: html;">[+myplaceholder:len:gt=`3`:show+]</pre>

<h2 class="page-header">Примеры</h2>
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