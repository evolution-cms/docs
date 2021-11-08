###Ідентифікатор доданої записи

integer getInsertId([$conn])

**$conn** - з'єднання з базою

Повертає AUTO_INCREMENT-ідентифікатор для останнього запису, яка була додана за допомогою запиту INSERT. Повертає 0, якщо поля AUTO_INCREMENT не створено.

***

####Приклад

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