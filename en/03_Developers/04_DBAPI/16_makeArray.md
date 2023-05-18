### Query result as an array

mixed makeArray($rs, $index = false)

**$rs** - результат виконання запиту

**$index** - ім'я поля для використання його значення як ключ в масиві, якщо рівне false - ключі в масиві будуть числові.

This method returns a multidimensional associative array with query result data in the format Key => Array(FieldName => Value).

***

#### Example
```
function show_members() {  
	global $modx;  
	$output = '';  
	$table = $modx->getFullTableName('members');   

	$result = $modx->db->select('id, name, picture', $table, '', 'name ASC', '');
	$members = $modx->db->makeArray($result, 'id');   
	foreach ($members as $p_val) {  
		foreach ($p_val as $m_key => $m_val) {  
			$output .= '<strong>' . $m_key . ':</strong> ' . $m_val . '<br />';  
		}  
	}  
}
```
