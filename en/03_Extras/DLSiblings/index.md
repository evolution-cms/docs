
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>DLSiblings: Вывод соседних ресурсов с шаблонизацией </h3>
Вывод соседних ресурсов с шаблонизацией (множественная кольцевая перелинковка).
<p>Вывод соседних ресурсов с шаблонизацией (множественная кольцевая перелинковка)</p>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/Aharito/DLSiblings" rel="nofollow" target="_blank">Aharito</a></p>
<h2 class="page-header">Параметры сниппета:</h2>
<h3 class="sub-header text-bold">&amp;idType, &amp;parents, &amp;documents, &amp;ignoreEmpty</h3>
<p>- как в ДокЛистере.</p>
<h3 class="sub-header text-bold">&amp;Qty</h3>
<p>(целое), кол-во предыдущих и следующих соседей. Имеет приоритете над &amp;prevQty и &amp;nextQty.</p>
<p>Если &amp;Qty=`3`, то общее кол-во будет 6 - то есть 3 перед и 3 после.
<p>Значение по умолчанию: 2.</p>
<h3 class="sub-header text-bold">&amp;prevQty</h3>
<p>Кол-во соседей-предшественников. Приоритет меньше $Qty</p>
<p>Значение по умолчанию:default 2</p>
<h3 class="sub-header text-bold">&amp;nextQty</h3>
<p>Кол-во соседей-последователей. Приоритет меньше $Qty</p>
<p>Значение по умолчанию: 2</p>

<p>Также можно использовать унаследованные от DocLister (такие же, как у него): условия выборки <span class="text-danger">&amp;addWhereList</span> и  <span class="text-danger">&amp;filters</span>, условия сортировки <span class="text-danger">&amp;orderBy</span>, глубина выборки <span class="text-danger">&amp;depth</span>, <span class="text-danger">prepare</span>, многие другие параметры.</p>
<p>Нужно лишь понимать, имеют ли смысл эти параметры в вызове. Например, если задать <span class="text-bold">&amp;idType=`documents`</span> и <span class="text-bold">&amp;documents=`1,2,3`</span> (всего 3 документа), а <span class="text-bold">&amp;Qty</span> задать как 6, то выводиться все равно будут всегда эти 3 документа - смысла в этом нет.</p>
<h3>Параметры-исключения:</h3>
<ul>
	<li>режим <span class="text-bold">api</span> принудительно устанавливается в 1 (нет смысла задавать в сниппете)</li>
	<li>режим <span class="text-bold">debug</span> устанавливается в 0 (также нет смысла задавать).</li>
	<li>параметр <span class="text-bold">&amp;display</span> принудительно устанавливается в &amp;display=`0`, так как за кол-во отвечают параметры <span class="text-bold">&amp;Qty</span>, <span class="text-bold">&amp;prevQty</span> и <span class="text-bold">&amp;nextQty</span>.</li>
</ul>
<h3>Шаблоны сниппета</h3>
<ul>
	<li><span class="text-bold">&amp;ownerTPL</span>, шаблон-обертка аналогично DocLister, но плейсхолдер НЕ [+dl.wrap+], а [+wrap+]. Значение по умолчанию null (вывод не оборачивается в ownerTPL).</li>
	<li><span class="text-bold">&amp;tpl</span>, <span class="text-bold">&amp;tplOdd</span> и <span class="text-bold">&amp;tplEven</span>, <span class="text-bold">&amp;tplIdN</span>, <span class="text-bold">&amp;tplFirst</span> и <span class="text-bold">&amp;tplLast</span> Шаблоны элемента как в DocLister в порядке <span class="text-bold">увеличения</span> приоритета.</li>
	<li><span class="text-bold">&amp;noneTPL</span> Шаблон с информацией, что ничего нет, как в DocLister. По умолчанию - пусто.</li>
	<li><span class="text-bold">&amp;noneWrapOuter</span> Как в DocLister, оборачивать ли шаблон noneTPL в обёртку ownerTPL. Параметр &amp;noneWrapOuter имеет смысл, только если ничего не нашлось и при этом задан ownerTPL.</li>
</ul>
<p>Другие шаблоны DL <span class="text-bold">не используются</span>.  </p>
<h3 class="text-danger">ВНИМАНИЕ:</h3>
<p>!!! В шаблонах сниппета <span class="text-bold">плейсхолдеры</span> ТВ-параметров записываются НЕ через точку, а через нижнее подчеркивание. То есть, будет <span class="text-bold">не</span> [+tv.h1+], а [+tv_h1+]. То же самое касается <span class="text-bold">экстендеров</span>, например экстендера e: вместо [+e.title+] пишем [+e_title+].</p>
<p>В общем, в плейсхолдерах шаблонов (только в них!) все точки <span class="text-bold">меняем</span> на нижнее подчеркивание (см. примеры вызова сниппета ниже).</p>
<h3>ПРИМЕРЫ</h3>
<p>Пример 1: Простой вызов сниппета.</p>
<pre class="brush: html;">
[[DLSiblings?
    &amp;idType=`parents`
    &amp;parents=`152`
    &amp;tpl=`@CODE: &lt;a href="[+url+]"&gt;[+tv_h1+]&lt;/a&gt;&lt;br&gt;`
    &amp;Qty=`2`
    &amp;tvList=`h1`
]]</pre>
<p>Пример 2: Более сложный пример с prepare и превьюшками FastImage</p>
<pre class="brush: html;">[[DLSiblings?
    &amp;idType=`parents`
    &amp;parents=`152`
    &amp;thumbSnippet=`sgThumb`
    &amp;thumbOptions=`{"tv.article_intro_img":{"small":"280x160","medium":"700x400"}}`   //Здесь НЕ надо менять точку на подчеркивание (это не шаблон)
    &amp;ownerTPL=`@CODE:&lt;div class="row latest-news inline-showcase"&gt;[+wrap+]&lt;/div&gt;&lt;hr&gt;`                                       
    &amp;tpl=`@CODE:
    &lt;div class="column col-1-1-2-4-4 margin-bottom-30"&gt;   //А здесь везде надо менять (это шаблон)              
        &lt;div class="article-announce-img"&gt;
            &lt;img class="img-responsive" src="[+tv_article_intro_img_medium+]" alt="[+e_title+] | [(cfg_company_brand_name)]"&gt;               
        &lt;/div&gt;
        &lt;div class="article-announce-content"&gt;
            &lt;div class="article-announce-header"&gt;
                &lt;a href="[+url+]"&gt;[+tv_h1+]&lt;/a&gt;
            &lt;/div&gt;
        &lt;/div&gt;
        &lt;a href="[+url+]" class="wrapper-link"&gt;&lt;/a&gt;
    &lt;/div&gt;`
    &amp;Qty=`2`
    &amp;tvList=`article_intro_img,h1`
    &amp;prepare=`FastImagePreviews`
]]</pre>
<p><span class="text-bold">Примечание:</span> Это только примеры. Для того, чтобы они заработали на вашем сайте, у вас должны быть такие же TV и такие же prepare-сниппеты.</p>
<h3>Результат работы примера 2</h3>
<p><img src="https://cloud.githubusercontent.com/assets/6253807/24569757/ea66affa-1691-11e7-8320-aa726ffd3dbc.png" alt="siblings_demo_1" /></p>
<h3>Скорость работы</h3>
<p>1) Кол-во запросов и т.д. при <span class="text-bold">кешированном</span> вызове сниппета на кешированном ресурсе на микро-сайте, выборка 4 из 8 статей с сортировкой</p>
<pre class="brush: html;">&amp;orderBy=`if(pub_date=0,createdon,pub_date) DESC`</pre>
<p><img src="https://cloud.githubusercontent.com/assets/6253807/24569985/4e7dedd6-1693-11e7-955c-95574150e8de.png" alt="siblings_requests" /></p>
<p>2) Кол-во запросов и т.д. при <span class="text-bold">некешированном</span> вызове сниппета на кешированном ресурсе на микро-сайте, выборка 4 из 8 статей с сортировкой</p>
<pre class="brush: html;">&amp;orderBy=`if(pub_date=0,createdon,pub_date) DESC`</pre>
<p><img src="https://cloud.githubusercontent.com/assets/6253807/24570665/e1272e60-1696-11e7-8b7d-832009a2be07.png" alt="siblings_requests_nocache" /></p>
<h3>Недостатки</h3>
<ul>
	<li>Длинная JSON-строка, содержащая все поля, в том числе контент (расход памяти)</li>
	<li>Формирование доп. индексного массива $ids (время)</li>
	<li>В результате сниппет подойдет для не очень больших выборок (навскидку до 1-2 тыс. ресурсов), для больших сайтов требуется другое решение</li>
</ul>