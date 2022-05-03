### Getting data

resource select($fields , $from [, $where [, $orderby [, $limit]]])

**$fields** - list of required fields from the request
**$from** - table to select
**$where** - selection condition
**$orderby** - field to sort by
**$limit** - limit on the number of records in the query result

The "select" method allows you to make a regular query to the database to get data that matches the given parameters.
***

#### Example
```
function login($username, $password) {  
	global $modx;  
	// assume these values have been received
	// using POST before calling the function
	$username = $modx->db->escape($username); 
	$password = $modx->db->escape($password); 

	$res = $modx->db->select("id", $modx->getFullTableName('web_users'),  "username='" . $username ."' AND password='".md5($password)."'");  

	if($modx->db->getRecordCount($res)) {  

		$id = $modx->db->getValue($res);  
		$_SESSION['userid'] = $id;  
		// Other Actions
	}else{  
		// no matching entry found
	}  
}
```
