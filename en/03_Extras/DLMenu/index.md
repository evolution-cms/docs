## Overview
DLMenu is DocLister based replacement of Wayfinder. Among perfomance and flexibility, the main features are:
* templates and classes are similar to Wayfinder;
* the amount of DB queries is equal to the number of menu levels (except the queries to append tv-paremeters and count children);
* the ability to count child resources (for their direct parents);
* almost all parameters are possible to apply to the particular menu level, as well as for all levels;
* prepare-snippets to post-process data and change templates on the fly; it's also possible to exclude documents from output using prepare-snippets, like in DocLister;
* menu can be built from several parents;
* it'possible to keep some menu branches always opened;
* ability to output menu in json format;

## General parameters
Use DocLister parameters to sort and to limit data selections (sortBy, sortDir, orderBy, addWhereList and so on). The results are sorted by menuindex field in ascending order by default, documents having hidemenu=1 are ignored.

Prepare parameter is impossible to set for particular menu level (for example, prepare2). But you can get level value from $data['level'] inside of snippet. tvList parameter is applied to all levels as well.

Level number should be decreased by 1 in template parameters (for example, rowTpl2 will be applied to  documents of the third level, and rowTpl0 - of the first one).

### parents
List of document ids to build menu from, comma separated. If these documents have different parents, then several menus will be built.  To keep parents order provided in this parameter, set the value of sortType1 parameter to "doclist".

Possible values - comma separated ids.

Default - id of the resource, where the snippet has been called.

### maxDepth
Maximum level of the menu.

Possible values - number starting from 1.

Default - 10.

### showParent
If the value is 1, then documents provided in parents parameter will be shown.

Possible values - 0 or 1.

Default - 0.

### api
Set to 1 to output results as json array.

Possible values - 0 or 1.

Default - 0.

### hideSubMenus
Set to 1 to hide inactive brances.

Possible values - 0 or 1.

Default - 0.

### openIds
When hideSubMenus parameter is set, it's possible to provide parent document ids to make their direct descendants always visible. 

Possible values - comma separated ids.

Default - not defined.

### countChildren
If the value is 1, then the amount of the direct children of all the resources in the menu will be counted.

Possible values - 0 or 1.

Default - 0.

### titleField 
Placeholder name to store document title.

Default - title.

### joinMenus
If several parents are provided showParent parameter if off, then snippet outputs several menus. This parameter allows to join them.

Possible values - 0 or 1.

Default - 0.

## Templates
### outerTpl
Wraps the whole menu.

Possible values - name of a template given according to the DocLister template setting rules.

Default:
```
@CODE:<ul[+classes+]>[+wrap+]</ul>
```

### rowTpl, rowHereTpl
Template to output a document of the first level without chilrden. rowHereTpl is applied to the current document.

Possible values - name of a template given according to the DocLister template setting rules.

Default:
```
@CODE:<li[+classes+]><a href="[+url+]">[+title+]</a></li>
```

### parentRowTpl, parentRowHereTpl, parentRowActiveTpl
Template to output a document having children. Use parentRowHereTpl for the current parent document or parentRowActiveTpl - for the active one.

Possible values - name of a template given according to the DocLister template setting rules.

Default:
```
@CODE:<li[+classes+]><a href="[+url+]">[+title+]</a>[+wrap+]</li>
```

### innerTpl
Wraps child elements.

Possible values - name of a template given according to the DocLister template setting rules.

Default - outerTpl value.

### innerRowTpl, innerRowHereTpl
Template to output a child document. innerRowHereTpl template can be set for the current document.

Possible values - name of a template given according to the DocLister template setting rules.

Default - rowTpl value.

### categoryFolderTpl
Template to output category (the document having isfolder=1 and \_blank template or if its link_attributes field value contains "category").

Possible values - name of a template given according to the DocLister template setting rules.

Default - parentRowTpl value.

## Классы
Document classes:
* __rowClass__ - document class, provided by innerClass parameter;
* __firstClass__ - first document class, provided by firstClass parameter (default - first);
* __lastClass__ - last document class, provided by lastClass parameter (default - last);
* __levelClass__ - menu level class, provided by levelClass parameter, with level number appended (default - level);
* __webLinkClass__ - web link class, provided by webLinkClass parameter;
* __parentClass__ - parent document class, provided by parentClass parameter;
* __hereClass__ - current document class, provided by hereClass parameter (default - current);
* __activeClass__ - active document class, provided by activeClass parameter (default - active);
* __oddClass__ - odd document class, provided by oddClass parameter(default - odd);
* __evenClass__ - even document class, provided by evenClass parameter (default - even);
* __stateClass__ - provided by __[+state+]__ placeholder value.

It's possible to define your own classes using prepare-snippet:
```
$data['classes'] = array('myClass'=>'my');
```

Wrapper classes:
* __innerClass__ - class of the children wrapper, provided by innerClass parameter;
* __outerClass__ - class of the whole menu wrapper, provided by outerClass parameter.

## Placeholders
* __[+wrap+]__ - child documents output (children in api mode); if the value of the placeholder is an array, then it's converted to a string with according templates applied, is it's string then it stays unchanged;
* __[+classNames+]__ - the list of classes available in template (only names); 
* __[+classes+]__ - the list of classes available in template (including class=" ");
* __[+level+]__ - document level;
* __[+maxLevel+]__ - if it's set, then the document is in the bottom of its branch;
* __[+iteration+]__ - index number of a document;
* __[+here+]__ - if it's set then the document is current;
* __[+active+]__ - if it's set then the document is active;
* __[+state+]__ - if hideSubMenus parameter is set, then its value is open for the opened branch or closed for the closed one;
* __[+title+]__ - document title, it's equal to menutitle, if menutitle is not empty, or pagetitle;
* __[+url+]__ - document url;
* __[+count+]__ - the amount of the direct document children;
* __[+\_renderRowTpl+]__ - set this placeholder if you need to change template for documents ouput;
* __[+\_renderOuterTpl+]__ - set this placeholder if you need to change template for wrapper output.

It's also possible to use placeholders set by e extender, and placeholders of particular classes: __[+oddClass+]__, __[+rowClass+]__ and so on.
