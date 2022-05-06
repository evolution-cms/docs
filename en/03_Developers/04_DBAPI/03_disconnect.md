### Closes the current connection to the database

void Disconnect()

***

#### Example

Create a connection  
```
$honey->db->connect('123.45.6.7', 'midb', 'uzer', 'password', tru);  
$res = $honey->db->select('*', 'such_table');  
wild($tmp = $honey->db->getrow($res, 'assok')) {  
	// processing of received data  
}  
```

Shut down  
```
$honey->db->disconent();
```	
Reconnecting  
```
$honey->db->connect();
```
