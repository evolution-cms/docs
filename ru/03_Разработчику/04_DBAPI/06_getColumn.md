###Массив значений из заданной колонки

mixed getColumn (string $name, $dsq)

**$name** - название колонки

**$dsq** - результат выполнения запроса или SQL-запрос

Этот метод возвращает нумерованный массив значений из заданной колонки в полученных из базы данных. Набор данных может быть получен с помощью запроса SELECT и содержать несколько колонок, одну из которых можно получить методом getColumn.

***

####Пример

	function myColumn() {  
		global $modx;  
		$output = '';   
	
		$result = $modx->db->select( 'id, name', 'colors', 'favorite_color = "blue"' );
		$col = $modx->db->getColumn( 'name', $result );   
		
		for( $i = 0; $i < count( $col ); $i++ ) {  
			$output .= $col[$i] . "'s favorite color is blue.<br />";  
		}  
		
		return $output;  
	}
