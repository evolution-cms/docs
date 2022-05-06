### Generates an HTML table with query data

string getHTMLGrid($dsq, $params)

* **$dsq** - query result or SQL query
* **$params** - an array of HTML table output settings

+ columnHeaderClass
+ cssClass
+ itemClass
+ altItemClass
+ columnHeaderStyle
+ tableStyle
+ itemStyle
+ altItemStyle
+ columns
+ fields
+ colWidths
+ colAligns
+ colColors
+ colTypes
+ cellPadding
+ cellSpacing
+ header
+ footer
+ pageSize
+ pagerLocation
+ pagerClass
+ pagerStyle

The method generates an HTML table based on the query data, taking into account an extensive list of possible output settings.

***

#### Example
```
$resource = $modx->db->query('SELECT id,name FROM modx_site_tmplvars order by name');   
$result = $modx->db->getHTMLGrid(
	$resource,
	array('fields'=>'id,name',
		'columns'=>'Number,Name',  
		'cssClass'=>'sortable resizable editable',  
		'columnHeaderClass'=>'noedit',  
		'columnHeaderStyle'=>'color: black; background-color: silver;'  
		);
	);  
return $result; 
```
