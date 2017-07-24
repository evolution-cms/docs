###Идентификатор добавленной записи

integer getInsertId([$conn])

**$conn** - соединение с базой

Возвращает AUTO_INCREMENT-идентификатор для последней записи, которая была добавленна с помощью запроса INSERT. Возвращает 0, если поля AUTO_INCREMENT не создано.

***

####Пример

	function insert_user( $fields, $table ) {  
		if( is_array( $fields ) {  
			if( $modx->db->insert( $table, $fields ) ) {  
				return $modx->db->getInsertId();  
			} else {  
				return false;  
			}  
		} else {  
			return false;  
		}  
	}