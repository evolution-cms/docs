### Display a list of galleries
Implemented using the sg_site_content controller for the DocLister snippet. The controller adds the corresponding records from the sg_images table to the documents selected from the site_content table. For convenience, DocLister is called with the necessary settings from the sgController wrapper snippet.

### SgController snippet parameters
#### sgOuterTpl
Image block template. Images in the block are displayed through the placeholder [+wrapper+], and the block itself is displayed in the document template through the placeholder [+images+].

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

#### sgRowTpl
The image template in the sgOuterTpl block. See the "Image Output" section.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

#### sgOrderBy
The conditions for sorting pictures in a SQL query to select from the sg_images table.

The default value is the ASC sg_index.

#### sgDisplay
Specifies the maximum number of images displayed in the sgOuterTpl block.

The possible values are number or all to display all images.

The default value is all.

#### sgAddWhereList
Additional conditions for the SQL query. Similar to the addWhereList parameter in the DocLister.

The default value is empty.

#### count
Allows you to display the number of images in the gallery in the document template through the [+count+] placeholder. Makes an additional request, so it is disabled by default.

The possible values are 0 or 1.

The default value is 0.

### Example
```
[[sgController? 
&count=`1` 
&depth=`1` 
&ownerTPL=`@CODE:[+dl.wrap+]` 
&tpl=`@CODE:<h2>[+pagetitle+] <span class="badge">[+count+]</span></h2>[+images+]` 
&sgDisplay=`4`
&sgOuterTpl=`@CODE:<div class="row">[+wrapper+]</div>`
&sgRowTpl=`@CODE:
<div class="col-lg-3 col-md-4 col-xs-6 thumb">
    <a class="thumbnail" href="[+url+]">
        <img class="img-responsive" src="[+thumb.sg_image+]" alt="[+e.sg_title+]">
    </a>
</div>
`
&thumbSnippet=`sgThumb`
&thumbOptions=`400x300`
&orderBy=`menuindex ASC` 
&sgOrderBy=`sg_index DESC`
]]
```
