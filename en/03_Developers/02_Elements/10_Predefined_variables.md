PHP provides all scripts with a large number of predefined variables. These variables contain everything from external data to environment variables, from the text of error messages to the most recently received headers.

Evolution supports calling in templates and chunks to call some of them.

## Example ###
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
