### Value of the first column from the query result

mixed getValue($dsq)

* **$dsq** - query result or SQL query

This function returns the first value from the first column of the query result. This allows you to quickly retrieve a single expected value (for example, the result of a SELECT COUNT(*) query).

***

#### Example
```
function display_rows() {  
	global $modx;  
	$count = $modx->db->getValue( $modx->db->select( 'count(*)', 'people' ) );   		
	if( $count < 1 ) {  
		return 'No records found';  
	}else{  
		return 'Найдено ' . $count . ' записей в базе.';  
	}  
}
```
