###Результат запроса в виде массива

mixed makeArray( $rs )

**$rs** - результат выполнения запроса

Этот метод возвращает многомерный ассоциативный массив с данными результата запроса в формате Key => Array( FieldName => Value ).

***

####Пример

	function show_members() {  
		global $modx;  
		$output = '';  
		$table = $modx->getFullTableName( 'members' );   
		
		$result = $modx->db->select( 'id, name, picture', $table, '', 'name ASC', '' );  		$members = $modx->db->makeArray( $result );   
		foreach( $members as $p_val ) {  
			foreach( $p_val as $m_key => $m_val ) {  
				$output .= '<strong>' . $m_key . ':</strong> ' . $m_val . '<br />';  
			}  
		}  
	}