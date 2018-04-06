###Формирует HTML-таблицу с данными запроса

string getHTMLGrid($dsq, $params)

**$dsq** - результат выполнения запроса или SQL-запрос

**$params** - массив настроек вывода HTML-таблицы

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

Метод формирует HTML-таблицу на основе данных запроса с учетом обширного списка возможных настроек вывода.

***

####Пример

	$resource = $modx->db->query('SELECT id,name FROM modx_site_tmplvars order by name');   
	$result = $modx->db->getHTMLGrid(
			  $resource,
			  array('fields'=>'id,name',
			  		'columns'=>'Number,Name',  
					'cssClass'=>'sortable resizable editable',  
					'columnHeaderClass'=>'noedit',  
					'columnHeaderStyle'=>'color: black; background-color: silver;'  
			  )
			);  
	return $result; 