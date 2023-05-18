### Результат запиту у вигляді масиву

mixed makeArray($rs, $index = false)

**$rs** - результат виконання запиту

**$index** - ім'я поля для використання його значення як ключ в масиві, якщо рівне false - ключі в масиві будуть числові.

Цей метод повертає багатовимірний асоціативний масив з даними результату запиту в форматі Key => Array(FieldName => Value).

***

#### Приклад
```
function show_members(){
	$modx = evolutionCMS();
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