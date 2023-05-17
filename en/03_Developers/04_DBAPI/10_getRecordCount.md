### Number of records in the query result

integer getRecordCount ($data_set)

* **$data_set** - connection to the database

Returns the number of records that were retrieved as a result of a SELECT query.

***

#### Example
````
$output = '';  
$result = $modx->db->select('make, model, color, year', 'cars', 'year > 2001');  	
$total_rows = $modx->db->getRecordCount( $result );   
	
if( $total_rows >= 1 ) {  
	$output .= $total_rows . ' cars newer than 2001:<br />';  
	while( $row = $modx->db->getRow( $result ) ) {  
		$output .= 'Manufacturer: ' . $row['make'] . ' | Model: ' . $row['model'] .  ' | Цвет: ' . $row['color'] . ' | Год: ' . $row['year'] . '<br />';  
	}  
}else{  
	$output = 'There are no cars newer than 2001!';  
}  
echo $output;
````
