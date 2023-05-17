### Table Structure Information

array getTableMetaData($table)

**$table** - table name

This function returns a multidimensional array with detailed information about the structure of the specified MySQL table.

The array has the form *TableField => Array( Info => Value )*, where 

+ TableField - column name, 
+ Info - one of the 6 information parameters, 
+ Value - the value of a specific parameter.

***

#### Information parameters:

* **Field** - table field name
* **Type** - field type and size (e.g. int(5), varchar(40) or text)
* **Null** - can contain a null value
* **Key** - contains a key for a value of type "UNI" (UNIQUE) or "PRI" (PRIMARY)
* **Default** - default value
* **Extra** - additional information, such as the use of auto_increment

***

#### Example
```
$table = 'my_table';  
$data = $modx->db->getTableMetaData( $table );  
$output = '';   

// Loop through all columns  
foreach( $data as $field => $arr ) {	 
	// Column name 
	$output .= '<b>' . $field . '</b><br />';

	// Cycle for all information parameters
	foreach( $arr as $info => $value )
		$output .= $info . ': ' . $value . '<br />'; // Output value  
	}  
}
return $output;
```
