## SimpleGallery - Display gallery on page
SimpleGallery - Display the gallery on the Evolution CMS page.
Since such a question did arise, I will show you how to draw a conclusion. The input, I hope, is intuitive (:

## Display the gallery on the page
An important advantage of DocLister is that now you do not need to fence your bicycles to output data from any tables: you do not need to come up with the names of the parameters (so that you can then get confused in them), pagination, sorting, etc. All the tedious work was done by [Agel_Nash](http://modx.im/profile/Agel_Nash/), for which he is once again grateful.

To work with arbitrary tables, DocLister has a onetable controller. All you need to know is the name of the table, the names of its fields, the name of the key field. Everything else is [in the documentation](doclister/index.html).

Once again, I will give the names of the fields in the table sg_images:

* sg_id – image id, key field (idField);
* sg_index – position in the list;
* sg_image – link to the picture;
* sg_title – the name of the picture;
* sg_description – description of the picture;
* sg_properties - here in json format information about the width and height of the image, as well as the size of the file, you can store something else in this field;
* sg_add is an additional field, now i don't remember why i needed it;
* sg_isactive – checkbox to hide some pictures from the output;
* sg_rid – the id of the resource to which the image belongs (parentField);
* sg_createdon is the date the picture was added.
Knowing this, in order to display pictures from the gallery, it is enough to make such a call on the page with the gallery:
```
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
```
Result:
```
assets/galleries/2/kitty099h.jpg kitty099h
assets/galleries/2/kitty098p.jpg kitty098p
assets/galleries/2/kitty096j.jpg kitty096j
assets/galleries/2/kitty095s.jpg kitty095s
assets/galleries/2/kitty094c.jpg kitty094c
assets/galleries/2/kitty093p.jpg kitty093p
```
If you add [+pages+] to the page, and add &paginate='pages' &display='10' to the call, we get a pagination.

That is, the output from your table is not much different from the usual output of documents.

In order not to write &controller='onetable' &table='sg_images' &idField='sg_id' every time, I made a sgLister snippet wrapper. [Agel_Nash](http://modx.im/profile/Agel_Nash/) this snippet has been improved and now when it is called, additional processing of fields occurs, in chunk you can use such placeholders:

* [+thumb.sg_image+], [+thumb.width.sg_image+], [+thumb.height.sg_image+] – preview and its dimensions;
* [+e.sg_title+] and [+e.sg_description+]- the values of the fields sg_title and sg_description, which are converted into html-entities (so as not to accidentally break the layout with quotation marks or brackets);
* [+properties.property_name+] – properties of the picture from the sg_properties field.
You can use the [+thumb.sg_image+] field if you add parameters when calling:

* &thumbSnippet – the name of the snippet that will return a link to the preview, for example, phpthumb;
* &thumbOptions – parameters for creating previews, in the form in which they will be accepted by the specified snippet.
In practice, it looks like this:
```
[[sgLister? 
&thumbSnippet=`phpthumb`
&thumbOptions=`w=150&h=150&zc=1`
&tpl=`@CODE:
<a href="[+sg_image+]">
	<img src="[+thumb.sg_image+]" class="img-thumbnail" alt="[+e.sg_title+]" title="[+e.sg_description+]">
</a>`
]]
```
### Display a list of galleries
This task doesn't come up as often, but it does, so [I've expanded the controller](http://modx.im/blog/docs/2759.html) site_content to be able to add pictures from galleries when displaying a list:

The DocLister call looks like this:
```
[[DocLister? 
&controller=`sg_site_content`
&prepare=`prepareImages`
&sgOrderBy=`sg_id DESC`
&tpl=`@CODE:
<div class="page-header">
	<h1><a href="[+url+]">[+pagetitle+]</a></h1>
</div>
[+images+]
<div class="clearfix"></div>` 
&sgOuterTpl=`@CODE:[+wrapper+]`
&sgRowTpl=`@CODE:
<a href="[+sg_image+]">
	<img src="[+thumb.sg_image+]" class="img-thumbnail" alt="[+e.sg_title+]" title="[+e.sg_description+]">
</a>`
&sgDisplay=`5`
]]
```
That is, the same as a simple output of documents, but additional parameters have been added:

* &sgOuterTpl and &sgRowTpl – chunks for displaying pictures;
* &sgOrderBy – image sorting options;
* &sgDisplay – how many pictures to output, all – to output everything;
* &sgAddWhereList – here you can specify the conditions for selecting images.
In order to display these pictures in the document chunk (&tpl), you should use the placeholder [+images+]. However, if you just enter [+images+], the images will not be displayed (because images are an array). You need a prepare-snippet for additional processing (let's call it prepareImages):
```
<?php
if (isset($data['images'])) {
	$wrapper= '';
	foreach ($data['images'] as $image) {
		$ph = $image;
		$ph['thumb.sg_image'] = $modx->runSnippet(
			'phpthumb',
			array(
				'input' => $image['sg_image'],
				'options' => 'w=150&h=150&zc=1'
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
?>
```
Prepare-snippet can also be useful for displaying the properties of the picture. These are the width, height and size of the file – they are stored in the sg_properties field as json. It's simple:
```
<?php
if (isset($data['sg_properties'])) {
    $properties = json_decode($data['sg_properties'],true);
    $data['width'] = $properties['width'];
    $data['height'] = $properties['height'];
    $data['size'] = $properties['size'];
}
return $data;
?>
```
For some time now, the sgController snippet wrapper is included, which calls the DocLister with the necessary parameters and does not require a separate prepare-snippet:
```
[[sgController? 
&sgOrderBy=`sg_id DESC`
&thumbSnippet=`phpthumb`
&thumbOptions=`w=150&h=150&zc=1`
&tpl=`@CODE:
<div class="page-header">
	<h1><a href="[+url+]">[+pagetitle+]</a></h1>
</div>
[+images+]
<div class="clearfix"></div>` 
&sgOuterTpl=`@CODE:[+wrapper+]`
&sgRowTpl=`@CODE:
<a href="[+sg_image+]">
	<img src="[+thumb.sg_image+]" class="img-thumbnail" alt="[+e.sg_title+]" title="[+e.sg_description+]">
</a>`
&sgDisplay=`5`
]]
```
In sgRowTpl you can use all the placeholders provided by the sgLister snippet.

If there are problems, I advise you to first update DocLister [from the github](https://github.com/AgexNash).
