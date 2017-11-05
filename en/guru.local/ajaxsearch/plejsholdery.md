
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>AjaxSearch: Плейсхолдеры</h2>

<p>Плэйсхолдеры используются в шаблонах. Форма поиска тоже доступна как плэйсхолдер <code>[+as.searchString +]</code>. Вставьте этот плэйсхолдер в шаблоне в том месте, где хотите видеть форму поиска.</p>
<p>Любой TV-параметр может превратиться в плэйсхолдер с помощью параметров <code>&withTvs</code> и <code>&tvPhx</code>. Эти плэйсхолдеры можно использовать, например, в шаблонах <code>tplResult</code> и <code>tplAjaxResult</code>:</p>
<pre class="brush: html;">[+as.****+]</pre>
<p>вместо **** укажите имя TV-параметра.</p>
<p>Для того, чтобы проверить, содержит или не содержит TV-параметр какое-нибудь значение, применяется такой плэйсхолдер:</p>
<pre class="brush: html;">[+as.****Show+]</pre>
<p>который принимает значения [0 | 1], и равен 0 когда **** = '', иначе принимает значение 1.</p>
<pre class="brush: html;">[+as.descriptionShow:is=`1`:then=`<span class="[+as.descriptionClass+]">[+as.description+]</span>`+]</pre>
<p>Т.е. если поле <span class="text-bold">description</span> не заполнено, то оно не выведется.</p>
<p>Для того, чтобы задать класс элементу, используется плэйсхолдер:</p>
<pre class="brush: html;">[+as.****Class+]</pre>
<p>название класса будет следующим:</p>
<p>1. ajaxSearch_result**** для результатов в не Ajax режиме (&tplResult)</p>
<p>2. AS_ajax_result**** для Ajax режима (&tplAjaxResult)</p>
<p>Например, при &whereSearch="content,tv" можно получить следующие плэйсхолдеры:</p>
<pre class="brush: html;">[+as.id+]
[+as.publishedon+]</pre>
<h3 class="sub-header text-bold">Плэйсхолдеры документа</h3>
<pre class="brush: html;">[+as.pagetitle+], [+as.pagetitleShow+], [+as.pagetitleClass+]
[+as.longtitle+], [+as.longtitleShow+], [+as.longtitleClass+]
[+as.description+], [+as.descriptionShow+], [+as.descriptionClass+]
[+as.alias+], [+as.aliasShow+], [+as.aliasClass+]
[+as.introtext+], [+as.introtextShow+], [+as.introtextClass+]
[+as.menutitle+], [+as.menutitleShow+], [+as.menutitleClass+]
[+as.content+], [+as.contentShow+], [+as.contentClass+]
[+as.breadcrumbs+],[+as.breadcrumbsShow+],[+as.breadcrumbsClass+]</pre>
<h3 class="sub-header text-bold">Переменные шаблона</h3>
<pre class="brush: html;">[+as.tv_value+], [+as.tv_valueShow+], [+as.tv_valueClass+]</pre>
<h3 class="sub-header text-bold">Breadcrumbs</h3>
<pre class="brush: html;">[+as.breadcrumbs+], [+as.breadcrumbsShow+], [+as.breadcrumbsClass+]</pre>
<h3 class="sub-header text-bold">Параметр &extract</h3>
<pre class="brush: html;">[+as.extract+], [+as.extractShow+], [+as.extractClass+]</pre>
<p>Имена классов:</p>
<p>AS_ajax_resultExtract (Ajax режим)<br>ajaxSearch_resultExtract (не Ajax режим)</p>
<h3 class="sub-header text-bold">&whereSearch=`content,tv,maxigallery,jot`</h3>
<pre class="brush: html;">[+as.jot_content], [+as.jot_contentShow], [+as.jot_contentClass]
[+as.gal_title], [+as.gal_titleShow], [+as.gal_titleClass]
[+as.gal_descr], [+as.gal_descrShow], [+as.gal_descrClass]</pre>