PHP предоставляет всем скриптам большое количество предопределённых переменных. Эти переменные содержат всё, от внешних данных до переменных среды окружения, от текста сообщений об ошибках до последних полученных заголовков.

Evolution поддерживает вызов в шаблонах и чанках вызов некоторых из них.

## Примеры ###
```
[!$_GET['username'] !]
[!$_GET['username']:ifempty=<form><input name="username"></form>!]
[!$_SERVER['REQUEST_TIME']:dateFormat='d.m.Y'!]
[!$_SERVER['HTTP_USER_AGENT']:find='Chrome':then='Chrome':else='Other'!]
<h2>$_SERVER:</h2>
<pre>
	[!$_SERVER!]
</pre>
<hr>
<h2>$_POST:</h2>
<pre>
	[!$_POST!]
</pre>
<hr>
<h2>$_GET:</h2>
<pre>
	[!$_GET!]
</pre>
<h2>$_COOKIE:</h2>
<pre>
	[!$_COOKIE!]
</pre>
<hr>
<h2>$_REQUEST:</h2>
<pre>
	[!$_REQUEST!]
</pre>

<h2>$_SESSION:</h2>
<pre>
	[!$_SESSION!]
</pre>
```