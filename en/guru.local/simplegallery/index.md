
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>SimpleGallery</h2>

<p>Раз такой вопрос все же возник, то покажу, как делать вывод. Ввод, я надеюсь, понятен интуитивно (:</p>
<h3 class="sub-header">Вывод галереи на странице</h3>
<p>Важное достоинство DocLister заключается в том, что теперь не нужно городить свои велосипеды для вывода данных из любых таблиц: не нужно придумывать названия параметров (чтобы потом в них путаться), пагинации, сортировки и т.п. Всю нудную работу сделал <a href="http://modx.im/profile/Agel_Nash/" rel="nofollow" target="_blank">Agel_Nash</a> , за что ему в очередной раз спасибо.</p>
<p>Для работы с произвольными таблицами в DocLister есть контроллер onetable. Все что нужно знать – это название таблицы, названия ее полей, название ключевого поля. Все остальное есть <a href="doclister/index.html" target="_blank">в документации</a>.</p>
<p>Еще раз приведу названия полей в таблице <span class="text-bold">sg_images</span>:</p>
<ul>
	<li><span class="text-bold">sg_id</span> – id картинки, <span class="text-bold">ключевое поле (idField)</span>;</li>
	<li><span class="text-bold">sg_index</span> – позиция в списке;</li>
	<li><span class="text-bold">sg_image</span> – ссылка на картинку;</li>
	<li><span class="text-bold">sg_title</span> – название картинки;</li>
	<li><span class="text-bold">sg_description</span> – описание картинки;</li>
	<li><span class="text-bold">sg_properties</span> – здесь в формате json хранится информация о ширине и высоте картинки, а также размере файла, можно еще что-нибудь хранить в этом поле;</li>
	<li><span class="text-bold">sg_add</span> – дополнительное поле, сейчас уже не помню, зачем оно мне было нужно;</li>
	<li><span class="text-bold">sg_isactive</span> – флажок, чтобы скрыть какие-то картинки из вывода;</li>
	<li><span class="text-bold">sg_rid</span> – id ресурса, которому принадлежит картинка (parentField);</li>
	<li><span class="text-bold">sg_createdon</span> – дата добавления картинки.</li>
</ul>

<p>Зная это, чтобы вывести картинки из галереи, достаточно сделать такой вызов на странице с галереей:</p>
<pre class="brush: html;">
[[DocLister?
&controller=`onetable`
&table=`sg_images`
&idField=`sg_id`
&parentField=`sg_rid`
&idType=`parents`
&addWhereList=`sg_isactive=1`
&tpl=`@CODE:[+sg_image+] [+sg_title+]`
&showParent=`-1`
]]
</pre>

<p>Результат:</p>
<pre class="brush: html;">
assets/galleries/2/kitty099h.jpg kitty099h
assets/galleries/2/kitty098p.jpg kitty098p
assets/galleries/2/kitty096j.jpg kitty096j
assets/galleries/2/kitty095s.jpg kitty095s
assets/galleries/2/kitty094c.jpg kitty094c
assets/galleries/2/kitty093p.jpg kitty093p
</pre>
<p>Если на страницу добавить [+pages+], а к вызову добавить &paginate=`pages` &display=`10` – получим пагинацию. </p>
<p>То есть вывод из своей таблицы не сильно отличается от обычного вывода документов.</p>
<p>Чтобы не писать каждый раз &controller=`onetable` &table=`sg_images` &idField=`sg_id`, я сделал сниппет-обертку sgLister. <a href="http://modx.im/profile/Agel_Nash/" rel="nofollow" target="_blank">Agel_Nash</a> этот сниппет доработал и теперь при его вызове происходит дополнительная обработка полей, в чанке можно использовать такие плейсхолдеры:</p>
<ul>
	<li>[+thumb.sg_image+], [+thumb.width.sg_image+], [+thumb.height.sg_image+] – превьюшка и ее размеры;</li>
	<li>[+e.sg_title+] и [+e.sg_description+]- значения полей sg_title и sg_description, которые преобразованы в html-сущности (чтобы не поломать случайно верстку кавычками или скобками);</li>
	<li>[+properties.имя_свойства+] – свойства картинки из поля sg_properties.</li>
</ul>
<p>Использовать поле [+thumb.sg_image+] можно, если при вызове добавить параметры:</p>
<ul>
	<li><span class="text-bold">&thumbSnippet</span> – имя сниппета, который вернет ссылку на превью, например, phpthumb;</li>
	<li><span class="text-bold">&thumbOptions</span> – параметры для создания превью, в том виде, в каком их примет указанный сниппет.</li>
</ul>
<p>На практике это выглядит так:</p>
<pre class="brush: html;">
[[sgLister? 
&thumbSnippet=`phpthumb`
&thumbOptions=`w=150&h=150&zc=1`
&tpl=`@CODE:
&lt;a href="[+sg_image+]"&gt;
	&lt;img src="[+thumb.sg_image+]" class="img-thumbnail" alt="[+e.sg_title+]" title="[+e.sg_description+]"&gt;
&lt;/a&gt;`
]]
</pre>

<h3 class="sub-header">Вывод списка галерей</h3>
<p>Такая задача возникает не так часто, но все же возникает, поэтому я <a href="http://modx.im/blog/docs/2759.html" rel="nofollow" target="_blank">расширил контроллер</a> site_content, чтобы получить возможность добавить картинки из галерей при выводе списка:
</p>
<p>Вызов DocLister выглядит так:</p>
<pre class="brush: html;">
[[DocLister? 
&controller=`sg_site_content`
&prepare=`prepareImages`
&sgOrderBy=`sg_id DESC`
&tpl=`@CODE:
&lt;div class="page-header"&gt;
	&lt;h1&gt;&lt;a href="[+url+]"&gt;[+pagetitle+]&lt;/a&gt;&lt;/h1&gt;
&lt;/div&gt;
[+images+]
&lt;div class="clearfix"&gt;&lt;/div&gt;` 
&sgOuterTpl=`@CODE:[+wrapper+]`
&sgRowTpl=`@CODE:
&lt;a href="[+sg_image+]"&gt;
	&lt;img src="[+thumb.sg_image+]" class="img-thumbnail" alt="[+e.sg_title+]" title="[+e.sg_description+]"&gt;
&lt;/a&gt;`
&sgDisplay=`5`
]]
</pre>

<p>То есть то же самое, что простой вывод документов, но добавлены дополнительные параметры:</p>
<ul>
	<li><span class="text-bold">&sgOuterTpl и &sgRowTpl</span> – чанки для вывода картинок;</li>
	<li><span class="text-bold">&sgOrderBy</span> – параметры сортировки картинок;</li>
	<li><span class="text-bold">&sgDisplay</span> – сколько картинок выводить, all – чтобы вывести все;</li>
	<li><span class="text-bold">&sgAddWhereList</span> – здесь можно указать условия для выборки картинок.</li>
</ul>

<p>Для того, чтобы вывести в чанке документа (&tpl) эти картинки, следует использовать плейсхолдер [+images+]. Однако если просто вписать [+images+], то картинки не выведутся (потому что images – это массив). Нужен prepare-сниппет для дополнительной обработки (назовем его prepareImages):</p>
<pre class="brush: php;">
&lt;?php
if (isset($data['images'])) {
	$wrapper= '';
	foreach ($data['images'] as $image) {
		$ph = $image;
		$ph['thumb.sg_image'] = $modx-&gt;runSnippet(
			'phpthumb',
			array(
				'input' =&gt; $image['sg_image'],
				'options' =&gt; 'w=150&h=150&zc=1'
			)
		);
		//сделали превьюшку

		$ph['e.sg_title'] = htmlentities($image['sg_title'], ENT_COMPAT, 'UTF-8', false);
		$ph['e.sg_description'] = htmlentities($image['sg_description'], ENT_COMPAT, 'UTF-8', false);
		//добавили поля e.sg_title и e.sg_description

		$wrapper .= $_DocLister-&gt;parseChunk($_DocLister-&gt;getCFGDef('sgRowTpl'), $ph);
		//обработали чанк sgRowTpl - для каждой картинки
	}
	$data['images'] = $_DocLister-&gt;parseChunk($_DocLister-&gt;getCFGDef('sgOuterTpl'),array('wrapper'=&gt;$wrapper));
	//обработали чанк sgOuterTpl
}
return $data;
?&gt;
</pre>

<p>Prepare-сниппет может пригодиться также для вывода свойств картинки. Это ширина, высота и размер файла – они хранятся в поле sg_properties в виде json. Тут все просто:</p>
<pre class="brush: php;">
&lt;?php
if (isset($data['sg_properties'])) {
    $properties = json_decode($data['sg_properties'],true);
    $data['width'] = $properties['width'];
    $data['height'] = $properties['height'];
    $data['size'] = $properties['size'];
}
return $data;
?&gt;
</pre>

<p>С некоторых пор в комплекте имеется сниппет-обертка sgController, который вызывает DocLister с нужными параметрами и не требует отдельного prepare-сниппета:</p>
<pre class="brush: html;">
[[sgController? 
&sgOrderBy=`sg_id DESC`
&thumbSnippet=`phpthumb`
&thumbOptions=`w=150&h=150&zc=1`
&tpl=`@CODE:
&lt;div class="page-header"&gt;
	&lt;h1&gt;&lt;a href="[+url+]"&gt;[+pagetitle+]&lt;/a&gt;&lt;/h1&gt;
&lt;/div&gt;
[+images+]
&lt;div class="clearfix"&gt;&lt;/div&gt;` 
&sgOuterTpl=`@CODE:[+wrapper+]`
&sgRowTpl=`@CODE:
&lt;a href="[+sg_image+]"&gt;
	&lt;img src="[+thumb.sg_image+]" class="img-thumbnail" alt="[+e.sg_title+]" title="[+e.sg_description+]"&gt;
&lt;/a&gt;`
&sgDisplay=`5`
]]
</pre>
<p>В sgRowTpl можно использовать все плейсхолдеры, предусмотренные сниппетом sgLister.</p>
<p class="text-bold">Если возникают проблемы, то советую первым делом обновить DocLister <a href="https://github.com/AgexNash" rel="nofollow" target="_blank">с гитхаба</a>.</p>