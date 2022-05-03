### Connection with the database

void connect(string $host, string $dbase, string $uid, string $pwd, boolean $persist)

* **$host** - server to connect 
* **$dbase** - select the working base of the 
* **$uid** - login 
* **$pwd** - password 
* **$persist** - keep the connection active 

This function also tracks the time spent on the connection and adds it to the total time of requests.

If the connection fails, it reports an error and crashes.

***

#### Example

```
//Connection to a third-party database
$modx->db->connect('123.45.6.7', 'mydb', 'user', 'password', true);  
$res = $modx->db->select('*', 'this_table');  
while($tmp = $modx->db->getRow($res, 'assoc')) {  
	// processing of received data  
}  
// Shut down  
$modx->db->disconnect()   

// Reconnect  
$modx->db->connect();
```
If necessary, you can create a separate instance of the object and organize a connection to a separate database without binding to the $modx.
