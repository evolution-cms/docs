### Column Name Array

array getColumnNames($dsq)

* **$dsq** - query result or SQL query

This method returns a numbered array of column names in the retrieved from the database. A dataset can be retrieved by using a SELECT query and contain multiple columns, a list of which can be retrieved by the getColumnNames method.

***

#### Example
```
$result = $modx->db->select( 'id, name, age', 'people_table' );  

// Get a list of column names  
$cols = $modx->db->getColumnNames( $result );

for( $i = 0; $i < count( $cols ); $i++ ) {
	// Column name list for a simple header  
	$output .= $cols[$i] . ' | ';	 	
}   

while( $row = $modx->db->getRow( $result ) ) {		// Get data from query result  
	$output .= '<br />' . $row['ItemID'] . ' | ' . $row['Name'] . ' | ' . $row['Image'];  
}   

return $output;
```
