### Add entry

mixed insert($fields, $intotable [, $fromfields [, $fromtable [, $where [, $limit ]]]])

* **$fields** - associative array of added values, with field name as a key
* **$intotable** - table to add
* **$fromfields** - list of fields used for import from another table
* **$fromtable** - table used for import
* **$where** - condition for requesting data from a table for import
* **$limit** - limit on the number of entries to import

The INSERT method allows you to add new records to the database. Values are passed as an associative array $fields, the format of which is field => value. The key "field" indicates the name of the column, and "value" indicates the value to be added.

The $fromfields, $fromtable, $where, and $limit parameters are used to copy data from one table to another.

This method returns the AUTO_INCREMENT ID for the added entry.

***

#### Example
```
function insert_my_rows( $data = array() ) {  
	global $modx;  
	$table_name = $modx->getFullTableName( 'cars' );  
	$fields = array('name'	=> $data['name'],  
					'color'	=> $data['color'],  
					'make'	=> $data['make'],  
					'model'	=> $data['model'], 
					);   
	$modx->db->insert( $fields, $table_name);  
}
```
