##A simple example without pagination

```
[!DocLister? 
&display=`20` 
&summary=`notags,len` 
&dateSource=`pub_date` 
&parents=`5` 
&tvList=`img,tag` 
&id=`lastnews` 
&tpl=`dl-post-item`
!]
```

The selection of the last 20 documents from the parent with ID=5. 

The text of each document will be subject to additional processing by the parameter summary with the preliminary removal of html tags and truncating the length of the text to 200 +/- 50 characters. In this case in the chunk placeholders tv.img and tv.tag will be available with the value of TV img and tag.

For clarity, dl-list-item chunk:

```
<div class="c-post">
  <h3 class="c-post__title"><a href="[~[+id+]~]">[+pagetitle+]</a></h3>
  <p class="c-post__date">[+createdon+]</p>
  <p class="c-post__tag">Tags: [+tv.tag+]</p>
  <div class="c-post__content">
    <a href="[~[+id+]~]" title="[+pagetitle+]"><img src="[+tv.img+]"></a>
    <p>[+summary+]...</p>
    <a href="[~[+id+]~]" title="Read more">Read more</a> 
  </div>
</div>
```

##Using configs

```
[!DocLister? 
&config=`test`
!]
```

Then create the JSON file test.json in the /config/custom/ snippet subfolder with the following content:

```
{
  "display" : "20",
  "summary" : "notags,len", 
  "dateSource" : "pub_date",
  "parents" : "5",
  "tvList" : "img,tag",
  "id" : "lastnews",
  "tpl" : "dl-list-item"
}
```

The result of this call will be identical to the previous example.

##Using lexicon

```
[!DocLister?
&tpl=`example` 
&customLang=`news`
!]
```

Then create the php file news.php with the $_lang array in the snippet subfolder /lang/

```
<?php if (!defined('MODX_BASE_PATH')) {
  die('What are you doing? Get out of here!');
}
$_lang = array();
$_lang['newsTitle'] = 'Latest News';
return $_lang;
```

Now in the example chunk you can use the tag [%newsTitle%] and it will automatically be replaced with the "Latest News" message.

##A complex example with pagination

```
[!DocLister? 
&id=`list` 
&parents=`2` 
&display=`4` 
&depth=`2` 
&addWhereList=`c.template IN (6,7)` 
&tpl=`dl-list-item` 
&summary=`notags,len:500` 
&dateFormat=`%d.%m.%Y в %H:%M` 
&dateSource=`pub_date` 
&tvList=`img,tag` 
&renderTV=`img` 
&showParent=`0` 
&sortBy=`menuindex` 
&paginate=`pages` 
&TplNextP=`` 
&TplPrevP=`` 
&TplPage=`@CODE: <li><a href="[+link+]">[+num+]</a></li>` 
&TplCurrentPage=`@CODE: <li class="active"><a href="[+link+]">[+num+]</a></li>` 
&TplWrapPaginate=`@CODE: <div class="pagination"><ul>[+wrap+]</ul></div>`
!]

[+list.pages+]
```

In this case, all documents from the parent with ID=2 with depth 2 and templates 6 or 7 are fetched, after which the documents will be filtered (namely the document with ID=2 and all its children that are containers). At the output, a pagination of the page will be prepared and the templates for the pagination elements will be defined with those specified in the parameters TplWrapPaginate, TplCurrentPage and TplPage. Templates for links the next and previous will be empty (the text in these elements will not be displayed). To all placeholders of the DocLister snippet, the prefix "list" will be added, and to each document involved in the issuance, the values of the TV parameters img and tag will be added to the placeholders tv.img and tv.tag. TV parameter img will be rendered in accordance with the widget specified when creating this TV parameter. A total of 4 documents will be displayed on the page. The sorting will be done not by the date of creation, but by menuindex (menu items). The date of publication of the document will be taken as the source of the date.

For clarity, dl-list-item chunk

```
<div class="c-post">
  <p class="c-post__date">[+createdon+]</p>
  <h3 class="c-post__title"><a href="[~[+id+]~]">[+pagetitle+]</a></h3>
  <p class="c-post__tag">Tags: [+tv.tag+]</p>
  <div class="c-post__content">
    <a href="[~[+id+]~]" title="[+pagetitle+]">[+tv.img+]</a>
    <p>[+summary+]...</p>
    <a href="[~[+id+]~]" title="Read more">Read more</a> 
  </div>
</div>
```

##Example of displaying information from a table other than site_content

```
[!DocLister? 
&controller=`onetable` 
&table=`site_snippets` 
&idField=`id` 
&contentField=`snippet` 
&sortBy=`name` 
&sortDir=`ASC` 
&display=`10` 
&tpl=`dl-onetable-item` 
&id=`snip` 
&showParent=`0` 
&paginate=`pages`
!]
```

dl-onetable-item chunk

```
<div class="c-onetable-row">
  <h3>[+name+]</h3>
  <code>[+snippet+]</code>
  <table class="table table-striped table-bordered">
    <thead>
      <tr>
        <td><strong>field</strong></td>
        <td><strong>value</strong></td>
      </tr>
    </thead>
    <tbody>
      <tr><td>id</td><td>[+id+]</td></tr>
      <tr><td>name</td><td>[+name+]</td></tr>
      <tr><td>description</td><td>[+description+]</td></tr>
      <tr><td>editor_type</td><td>[+editor_type+]</td></tr>
      <tr><td>category</td><td>[+category+]</td></tr>
      <tr><td>cache_type</td><td>[+cache_type+]</td></tr>
      <tr><td>locked</td><td>[+locked+]</td></tr>
      <tr><td>properties</td><td>[+properties+]</td></tr>
      <tr><td>moduleguid</td><td>[+moduleguid+]</td></tr>
    </tbody>
  </table>
</div>
```

In this example, the output will be content from the table site_snippets. The id field is used as the PrimaryKey column. Sorting occurs ascending values in the column name.