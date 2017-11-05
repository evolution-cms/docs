
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>UltimateParent: Примеры</h2>

<p>Получить id родителя документа 45, до документа с id = 6:</p>
<pre class="brush: html;">[[UltimateParent? &id=`45` &top=`6`]]</pre>
<p>Получить id третьего сверху родителя документа 45:</p>
<pre class="brush: html;">[[UltimateParent? &id=`45` &topLevel=`3`]]</pre>
<p>Из цепочки родительских документов, получить id второго родителя сверху. Само-собой вызов сниппета должен происходить из документа находящегося как минимум на третьем уровне вложенности. Иначе будет возвращаться id самого верхнего родительского документа.</p>
<pre class="brush: html;">[[UltimateParent? &topLevel=`2`]]</pre>