### Array of values from a given column

mixed getColumn (string $name, $dsq)

* **$name** - column name

* **$dsq** - query result or SQL query

This method returns a numbered array of values from the specified column in retrieved from the database. A dataset can be retrieved by using a SELECT query and contain multiple columns, one of which can be retrieved by the getColumn method.

***

#### Example
```
function myColumn() {  
	global $modx;  
	$output = '';   

	$result = $modx->db->select( 'id, name', 'colors', 'favorite_color = "blue"' ); 
	$col = $modx->db->getColumn( 'name', $result );   

	for( $i = 0; $i < count( $col ); $i++ ) {  
		$output .= $col[$i] . "'s favorite color is blue.<br />";  
	}  

	return $output;  
}
```
