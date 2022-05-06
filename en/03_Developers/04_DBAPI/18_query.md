### Direct database query

mixed query($sql)

**$sql** - string with SQL query

Various DBAPI methods end up querying the database using the "query" method. If the standard features of special methods are not enough, then you can make any SQL query directly.

***

#### Example
```
$output = '';  
$result = $modx->db->query('SELECT id, name, joined FROM ' . $modx->getFullTableName('user_table') . ' GROUP BY `member_type` ORDER BY name ASC');   

while( $row = $modx->db->getRow( $result ) ) {  
	$output .=  '<br> ID: ' . $row['id'] . 
			'<br> Name: ' . $row['name'] . 
			'<br> Joined: ' . $row['joined']  . 
			'<br>---------<br>';  
}  

echo $output;
```
