
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ddTypograph: Примеры</h2>

<h4>Типографирование аннотации перед выводом</h4>
<pre class="brush: html;">[[ddTypograph? &text=`Snippet for text typography.`]]</pre>
<h4>Типографирование аннотации с автоматической расстановкой абзацев, ссылок и адресов email</h4>
<pre class="brush: html;">
[[ddTypograph?
&text=`Snippet for text typography.`
&text_paragraphs=`1`
&text_autoLinks=`1`
]]
</pre>
<h4>Типографирование аннотации с автоматическим оптическим выравниванием (висячие кавычки и пр.)</h4>
<pre class="brush: html;">
[[ddTypograph?
&text=`Snippet for text typography.`
&optAlign=`1`
]]
</pre>