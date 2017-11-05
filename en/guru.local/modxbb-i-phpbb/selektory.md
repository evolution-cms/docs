
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>MODxBB и phpBB: Селекторы</h2>

<h2 class="page-header">MODxBB сниппеты: CSS селекторы</h2>
<p>На этой странице представлены CSS-селекторы для настройки отображения сниппетов MODxBB. <br>Большинство из них говорят сами за себя. Я добавил комментарии, чтобы объяснить некоторые моменты. Значения и примеры идентичны тем, которые используются в файле CSS на сайте MODxBB</p>
<p>По возможности, HTML теги используются вместо создания новых классов или идентификаторов, чтобы свести их число к минимуму </p>
<p>Названия разделов описывают сниппеты, к которым они принадлежат. Они сортируются по порядку, в котором они появляются на сайте.</p>
<p>=============[ ПАНЕЛЬ ПОЛЬЗОВАТЕЛЯ ]=============</p>
<pre class="brush: css;">.loginbb {
	position:relative; 
	float:left;
	margin:0;
	padding:0 0 33px 0; 
}

.loginbb table {
	float:left;
	margin:0 0 0 21px;
	padding:0px;
}

.loginbb tr {
	float:left;
	width:243px;
	padding:3px;
}

.loginbb button {
	width:59px;
	height:23px;
	margin:3px 0 0 -3px;
	vertical-align:bottom !important;
}

.loginbb input:focus {
	outline:#7F91A1 dotted 2px;
}

.loginbb .leftbb {
	float:left;
	padding-top:5px;
}

.loginbb .buttonpanel {
	height:27px;
	margin-left:21px;
	padding-right:9px;
}

.buttonpanel .leftbb {
	padding:5px 18px 0px 0px;
}

.leftbb label {
	vertical-align:1px;
}

.loginbb .rightbb {
	float:right;
}

.loginbb .inputbb {
	border-right:2px white solid;
	border-bottom:2px white solid;
	border-left:1px Gray solid;
	border-top:1px Gray solid;
}</pre>
<p>/* Класс privmsg используется для отображения в профиле пользователя информации о непрочитанных сообщениях в их почтовом ящике */</p>
<pre class="brush: css;">.privmsg {
	margin:3px 0;
	padding:2px 0 3px 0;
	border-top:2px #E6DBD8 solid;
	border-bottom:2px #E6DBD8 solid;
	background:#AF2525;
	font:normal small-caps 900 12px Arial, sans-serif;
}

.privmsg a:link, .privmsg a:visited {
	color:white;
	text-decoration:underline;
}

.privmsg a:hover {
	color:white;
	text-decoration:none;
}

.privmsg a:active {
	color:white;
	text-decoration:overline underline;
}

.privmsg span {
	font-variant:normal;
	letter-spacing:normal;
}

.userpanel {
	position:relative;
	float:left;
	margin:0;
	padding:0 0 33px 0; 
}

.userpanel table {
	float:left;
	margin-left:15px;
	padding:0px;
}

.userpanel tr {
	float:left;
	width:270px;
	padding:3px;
	vertical-align:middle;
}

.userpanel td {
	float:left;
	width:270px;
	border:1px #D3D3D3 solid;
	letter-spacing:normal;
}

.userpanel img {
	float:left;
	width:90px;
	height:90px;
}

.userpanel .userstats {
	position:relative;
	float:left;
	margin:0;
	padding:15px 0 0 3px;
	text-align:left;
	font:12px/110% Arial, sans-serif;
	letter-spacing:normal;
}

.userpanel .userstats .userlinks {
	line-height:15px;
}

.userpanel .username {
	color:#63463A;
	font:bold 16px/120% Arial, sans-serif;
}</pre>
<p>============[ ИСТОРИЯ ОПРОСОВ ]============</p>
<p>/ * Они используются для нумерации страниц PrevPollsBB. Все остальные объекты этого сниппета используют селекторы Опроса Сайта * /</p>
<pre class="brush: css;">.pagination {
	text-align:center;
}

.pagination a, .pagination strong {
	margin:0 3px;
}</pre>
<p>==============[ ОПРОС САЙТА ]==============</p>
<pre class="brush: css;">.sitepoll {
	display:block;
	position:relative;
	float:left;
	width:100%;
	margin:0;
	padding:33px 0 83px;
}

.sitepoll h2 {
	margin-bottom:-9px;
}

.sitepoll table {
	width:100%;
}

.polloptions {
	letter-spacing:normal;
	width:auto;
	padding-right:0;
	padding-left:1px;
	margin-right:0;
	text-align:center;
}</pre>
<p>/*. polloptions0 и.pollcount0 используются прежде, чем голосование сделано, .polloptions и.pollcount после того, как голосование было сделано */</p>
<pre class="brush: css;">.polloptions0 {
	letter-spacing:1px;
	padding-left:9px;
	text-align:center;
}

.pollrow:hover {
	background:#A9CBD6;
}

.pollshare {
	margin:0;
	padding-right:0;
	width:auto;
	min-width:120px;
	letter-spacing:normal;
}

.pollshare div {
	margin:2px 0;
	padding:0;
	background:#A52A2A;
	text-align:center;
}

.pollcount {
	position:relative;
	float:right;
	margin-right:0;
	margin-left:-3px;
	width:21px;
}

.pollcount0 {
	position:relative;
	float:right;
	margin-right:5px;
	margin-left:-3px;
	width:21px;
}

.voted {
	position:relative;
	float:right;
	width:5px;
	color:#696969;
}

.maxvotes {
	line-height:21px;
	letter-spacing:normal;
	color:#696969;
}

.maxvotes strong {
	color:#635757;
	letter-spacing:1px;
}

.pollmsg {
	position:relative;
	float:left;
	width:210px;
	margin:7px 0 3px 9px;
	letter-spacing:normal;
}

.pollmsg0 {
	position:relative;
	float:none;
	width:210px;
	padding:3px 0 9px;
	letter-spacing:normal;
}

.errormsg {
	position:relative;
	float:left;
	width:210px;
	margin:7px 0 3px 9px;
	color:red;
	text-align:center;
	letter-spacing:normal;
	font-size:18px;
	font-weight:bold;
}

.submitvote {
	position:relative;
	float:right;
	width:auto;
	height:auto;
	margin:-1px 9px 3px 3px;
}

.submitvote button {
	width:59px;
	height:23px;
	margin-top:9px;
	vertical-align:bottom !important;
}</pre>
<p>============[ ПОСЛЕДНИЕ ТЕМЫ ]============</p>
<p>/* Есть только один класс для этого сниппета. Для дальнейшей настройки используйте html селекторы, как сделано ниже. */</p>
<pre class="brush: css;">.latestposts {
	width:295px;
	margin:0 0 0 7px;
	padding:33px 0 0px;
	text-align:left;
}

.latestposts h4 {
	text-align:center;
	padding-bottom:3px;
}

.latestposts div {
	margin-bottom:12px;
	padding:3px 0 3px 2px;
	border:1px #A1A1A1 dashed;
	overflow:hidden;
}

.latestposts p {
	display:block;
	position:relative;
	min-height:54px;
	margin:0;
	padding:0 1px 0 43px;
	color:#696969;
	font:italic normal normal 12px/normal Arial, sans-serif; 
	letter-spacing:normal;
}

.latestposts img {
	display:block;
	position:relative;
	float:left;
	height:33px;
	width:33px;
	border:1px #939393 solid;
	border-right:1px #4B4B4B solid;
	border-bottom:1px #4B4B4B solid;
}</pre>
<p>============[ КТО СЕЙЧАС НА САЙТЕ ]============</p>
<pre class="brush: css;">#onlinebox {
	margin:-7px 0 0;
	padding:0 0 39px;
}

.onlineheader {
	font:12px/normal Calibri, Arial, sans-serif;
}

#onlinelist {
	position:relative;
	width:100%;
	height:0px;
	margin:0;
	padding:0;
	background:#CFBFB1;
	color:#fff;
	text-align:left;
	font-size:14px;
	overflow:hidden;
}

#onlinelist p {
	padding:5px;
}</pre>
<p>/* span используется для легенды */</p>
<pre class="brush: css;">#onlinelist p span {
	font:italic normal normal 12px/normal Arial, sans-serif;
}

#onlinelist a:link, #onlinelist a:visited {
	color:#63463A;
	text-decoration:none;
}

#onlinelist a:hover {
	color:#7B91A5;
	text-decoration:underline;
}

#onlinelist a:active {
	color:#FFFFED;
	text-decoration:none;
}</pre>