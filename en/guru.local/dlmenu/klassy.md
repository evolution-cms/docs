
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DLMenu: Классы</h2>

<p>Задаются для документов:</p>
<ul>
	<li><span class="text-bold">rowClass</span> - класс документа, задается значением параметра innerClass;</li>
	<li><span class="text-bold">firstClass</span> - класс первого документа в группе, задается значением параметра firstClass (по умолчанию - first);</li>
	<li><span class="text-bold">lastClass</span> - класс последнего документа в группе, задается значением параметра lastClass (по умолчанию - last);</li>
	<li><span class="text-bold">levelClass</span> - класс уровня меню, задается значением параметра lastClass, к которому добавляется номер уровня (по умолчанию - level);</li>
	<li><span class="text-bold">webLinkClass</span> - класс документа-ссылки, задается значением параметра webLinkClass;</li>
	<li><span class="text-bold">parentClass</span> - класс документа-родителя, задается значением параметра parentClass;</li>
	<li><span class="text-bold">hereClass</span> - класс текущего документа, задается значением параметра hereClass (по умолчанию - current);</li>
	<li><span class="text-bold">activeClass</span> - класс активного документа, задается значением параметра activeClass (по умолчанию - active);</li>
	<li><span class="text-bold">oddClass</span> - класс нечетного документа в группе, задается значением параметра oddClass (по умолчанию - odd);</li>
	<li><span class="text-bold">evenClass</span> - класс четного документа в группе, задается значением параметра evenClass (по умолчанию - even);</li>
	<li><span class="text-bold">stateClass</span> - задается значением плейсхолдера <span class="text-bold">[+state+]</span>.</li>
</ul>
<p>Можно также добавить свои классы в prepare-сниппете:</p>
<pre class="brush: php">$data['classes'] = array('myClass'=&gt;'my');</pre>
<p>Задаются для оберток:</p>
<ul>
	<li><span class="text-bold">innerClass</span> - класс обертки дочерних документов, задается значением параметра innerClass;</li>
	<li><span class="text-bold">outerClass</span> - класса обертки всего меню, задается значением параметра outerClass.</li>
</ul>