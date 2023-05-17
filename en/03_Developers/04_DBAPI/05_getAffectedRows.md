### Number of rows processed by the last request

integer getAffectedRows ([$conn])

* **$conn** - connection to the database

Returns the number of rows that were processed by the last INSERT, UPDATE, REPLACE, or DELETE request. If the last request failed, a value of -1 will be returned.

When using the UPDATE query, MySQL does not affect columns with values that have not been updated. As a result, the php function used mysql_affected_rows() can only return the number of records that have been changed.

The REPLACE query first deletes the old records and then inserts the new ones, causing the method to return the sum of the deleted and added records.

***

#### Example
````
function deleteid($id) {  
	$modx->db->query("DELETE FROM my_table WHERE userid=".$id);  
	if($modx->db->getAffectedRows()) {  
		return true;  
	}  		
	return false;  		
}
```
