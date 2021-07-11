### Формує HTML-таблицю з даними запиту

string getHTMLGrid($dsq, $params)

**$dsq** - результат виконання запиту або SQL-запит

**$params** - масив налаштувань виведення HTML-таблиці

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

Метод формує HTML-таблицю на основі даних запиту з урахуванням великого списку можливих налаштувань виведення.

***

#### Приклад

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