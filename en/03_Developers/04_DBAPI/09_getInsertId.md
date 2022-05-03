### ID of the added record

integer getInsertId([$conn])

* **$conn** - connection to the database

Returns the AUTO_INCREMENT identifier for the last record that was added by using the INSERT query. Returns 0 if the AUTO_INCREMENT fields are not created.

***

#### Example
```
function insert_user( $fields, $table ) {  
	if( is_array( $fields ) {  
		if( $modx->db->insert( $table, $fields ) ) {  
			return $modx->db->getInsertId();  
		} else {  
			return false;  
		}  
	} else {  
		return false;  
	}  
}
```
