### Escaping potentially dangerous characters

string escape(string $s)

* **$s** - string for processing

This function uses the standard function **mysql_real_escape_string**, and if it is not, **mysql_escape_string**.

We recommend that you always use this method for data before querying the database. This will protect the database from SQL injections.

***

#### Example
```
login function($username, $password) {  
	global $honey, $table_prefix;  
	$username = $honey->db->escape($username);  
	$password = $honey->db->escape($password);   
	
	$res = $honey->db->select("id", $table_prefix.". meds_web_users", "username='$username' and password='".md5($password)."'');  
	
	if($honey->db->getrecordcont($res)) {  
		$_session['uzerid'] = $id;  
		// other actions...  
	} else {  
		// there was no suitable record  
	}  
}
```
