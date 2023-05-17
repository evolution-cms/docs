### Data update

boolean update($fields, $table, $where)

* **$fields** - array of updated values
* **$table** - table to update
* **$where** - condition for searching for updated records

The "update" method allows you to update the data in the database by passing new values ​​in the $fields array. The format of the updated values ​​array is field => new_value, where "field" is the name of the updated field, and "new_value" is the new value.

***

#### Example
```
$table = $modx->getFullTableName( 'cars_table' );  

$fields = array('make'	=> $new_make,  
				'model'	=> $new_model,  
				'color'	=> $new_color,  
				'year'	=> $new_year,  
				'updated'=> time()  
				);  

$result = $modx->db->update( $fields, $table, 'id = "' . $id . '"' );  	
if( $result ) {  
	echo 'Information updated!';  
} else {  
	echo 'There was a problem during the request...';  
}
```
