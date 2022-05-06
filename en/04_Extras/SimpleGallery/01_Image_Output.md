## Image output
To display the gallery, use a DocLister with a onetable controller. For greater convenience, the DocLister is called through the sgLister snippet wrapper; accordingly, you can use any DocLister parameters when calling. sgLister also performs additional processing of the output data, which is implemented using the prepare parameter when docLister is called.

## sgLister snippet parameters
#### imageField
The name of the field with the image.

The default value is sg_image.

#### parents
To output images from specified resources.

The possible values are resource ids separated by a comma.

The default value is the id of the resource in which the snippet is called.

#### documents
To display individual images from all galleries.

The possible values are the id of the records in the sg_images table, separated by a comma.

The default value is empty.

#### BeforePrepare, AfterPrepare
Data processing before it is processed by the sgLister snippet, and after.

The possible values are snippet names, separated by commas.

The default value is empty.

#### thumbSnippet
The name of the snippet for generating previews at output.

The possible values are the name of the snippet, for example, phpthumb.

The default value is empty.

#### thumbOptions
Parameters passed to the snippet specified in the thumbSnippet parameter. To generate a single preview, a string with parameters is indicated:
```
&thumbSnippet=`phpthumb`
&thumbOptions = `w=400&h=400&zc=1`
```
The path to the picture will be available in the template through the placeholder [+thumb.sg_image+]

To generate multiple previews, parameters can be specified in json-format:
```
&thumbSnippet=`phpthumb`
&thumbOptions = `{
    "default":"w=400&h=400&zc=1",
    "small":"w=50&h=50&zc=1",
    "medium":"w=200&h=200&zc=1"
}`
```
Paths to the pictures will be available in the template through placeholders:

* [+thumb.sg_image+]
* [+thumb_small.sg_image+]
* [+thumb_medium.sg_image+]
The default value is empty.

#### tpl
The template for the output.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

### Placeholders
Table data sg_images:

* [+sg_id+] — image id;
* [+sg_index+] — position in the gallery;
* [+sg_image+] — link to the picture;
* [+sg_title+] — the name of the picture;
* [+sg_description+] — description of the picture;
* [+sg_properties+] - information about the image in json format;
* [+sg_add+] — additional field;
* [+sg_isactive+] — checkbox to hide some pictures from the output;
* [+sg_rid+] — id of the resource to which the picture belongs (parentField);
* [+sg_createdon+] — the date the picture was added.
To output shielded data (parameter e in DocLister):

* [+e.field_name+]
Image information (when using the sgLister snippet):

* [+properties.width+] - width in pixels;
* [+properties.height+] - height in pixels;
* [+properties.size+] - file size.
Preview (when using the sgLister snippet and the specified parameters thumbSnippet and thumbOptions):

* [+thumb.sg_image+] - link to the main preview file;
* [+thumb_name.sg_image+] - link to an additional preview file;
* [+thumb.width.sg_image+], [+thumb_name.width.sg_image+] - preview width;
* [+thumb.height.sg_image+], [+thumb_name.height.sg_image+] - the height of the preview.
Placeholders installed by the DocLister snippet are also available.

### Example
```
[+pages+]
[!sgLister?
&ownerTPL=`@CODE: <div class="row">[+dl.wrap+]</div>`
&thumbSnippet=`sgThumb`
&thumbOptions=`400x300`
&display=`16`
&paginate=`pages`
&PrevNextAlwaysShow=`1`
&tpl=`@CODE:
<div class="col-lg-3 col-md-4 col-xs-6 thumb">
    <a class="thumbnail" href="[+sg_image+]" target="_blank">
        <img class="img-responsive" src="[+thumb.sg_image+]" alt="[+e.sg_title+]">
    </a>
</div>
`
&TplWrapPaginate=`@CODE:<nav class="text-center"><ul class="pagination">[+wrap+]</ul></nav>`
&TplCurrentPage=`@CODE:<li class="active"><span>[+num+]</span></li>`
&TplPage=`@CODE:<li><a href="[+link+]"><span>[+num+]</span></a></li>`
&TplNextP=`@CODE:<li><a href="[+link+]"><span class="glyphicon glyphicon-forward"></span></a></li>`
&TplLastP=`@CODE:<li><a href="[+link+]"><span class="glyphicon glyphicon-fast-forward"></span></a></li>`
&TplFirstP=`@CODE:<li><a href="[+link+]"><span class="glyphicon glyphicon-fast-backward"></span></a></li>`
&TplPrevP=`@CODE:<li><a href="[+link+]"><span class="glyphicon glyphicon-backward"></span></a></li>`
&TplNextI=`@CODE:<li class="disabled"><span class="glyphicon glyphicon-forward"></span></li>`
&TplLastI=`@CODE:<li class="disabled"><span class="glyphicon glyphicon-fast-forward"></span></li>`
&TplFirstI=`@CODE:<li class="disabled"><span class="glyphicon glyphicon-fast-backward"></span></li>`
&TplPrevI=`@CODE:<li class="disabled"><span class="glyphicon glyphicon-backward"></span></li>`
!]
[+pages+]
```
