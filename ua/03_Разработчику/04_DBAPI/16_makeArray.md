### Результат запроса в виде массива

mixed makeArray($rs, $index = false)

**$rs** - результат выполнения запроса

**$index** - имя поля для использования его значения в качестве ключа в массиве, если равно false - ключи в массиве будут числовые.

Этот метод возвращает многомерный ассоциативный массив с данными результата запроса в формате Key => Array( FieldName => Value ).

***

#### Пример

function show_members(){
	$modx = evolutionCMS();
	$output = '';
	$table = $modx->getFullTableName('members');
	
	$result = $modx->db->select('id, name, picture', $table, '', 'name ASC', '');
	$members = $modx->db->makeArray($result);
	
	foreach( $members as $p_val ) {  
		foreach( $p_val as $m_key => $m_val ) {  
			$output .= '<strong>' . $m_key . ':</strong> ' . $m_val . '<br />';  
		}  
	}  
}
