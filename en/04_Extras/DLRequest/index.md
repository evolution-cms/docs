## DLRequest - run snippets with parameters from get/post
Snippet is designed to replace Ditto with a request extender at the request of Extremum and at its own expense, for which I thank you very much.

A snippet takes values from a post or get array and uses them as parameters to start another snippet. Initially, it was planned to work only with DocLister (hence the name), but in the end you can call any snippet. However, having DocLister installed is mandatory.

DLRequest is able not only to pass parameters, but also to build a form to control these very parameters, without crutches like:
```
<?php
//[!selected? &field=`ditto_id1_sortDir` &value=`DESC`!]
if ($_REQUEST[$field] == $value) {
	echo "selected"; 
}
```

An important point is that the possible parameter values are set by the developer, that is, if in the form for selecting the number of documents on the page it is indicated "10, 20, 50, 100", then it will not be possible to substitute url?display=100500 with your hands - such a parameter will simply be ignored.

It is also possible to save parameter values that are passed from the browser for other snippets, for example, for DocLister it will be the page parameter. That is, if in the list of documents you are on page 5, then after changing, for example, the direction of sorting, you will still remain on page 5.

Now I'll give you an example of a call that shows how it all works:
```
[+paramsForm+]
<div>
	[!DLRequest? 
	&runSnippet=`DocLister` 
	&parents=`2` 
	&tpl=`@CODE:
[+id+]. [+pagetitle+]

` 
	&paginate=`pages` 
	&display=`0` 
	&rqParams=`{
		"sortBy":{
			"id":"По id",
			"pagetitle":"По pagetitle"
		},
		"sortDir":{
			"asc":"По возрастанию",
			"desc":"По убыванию"
		},
		"display":{
			"1":"1 документ",
			"3":"3 документа",
			"5":"5 документов"
		}
	}`
	&rqParamsNames=`{
		"sortBy":"Сортировать по",
		"sortDir":"Порядок",
		"display":"Результатов на странице"
	}`
	&selectedClassName=`selected`
	& paramsForm=`paramsForm`
	&keepParams=`page`
	& paramsOwnerTPL=`@CODE:
		
			[+keepParams+]
			[+params+]
			Отправить
		
	`
	& param.ownerTPL=`@CODE:
		[+description+]
		
			[+values+]
		
	`
	& param.tpl=`@CODE:
		
			[+description+]
		
	`
	&sortBy.tpl=`@CODE:
		
			[+description+] dfdfdfh
		
	`
	&display.ownerTPL=`@CODE:
		[+description+]
		
			[+values+]
		
	`
	&keepTpl=`@CODE:
		
	`
	!]
</div>
[+pages+]
```
After & spaces stand, because otherwise the editor replaces the characters.

Author: Pathologic
