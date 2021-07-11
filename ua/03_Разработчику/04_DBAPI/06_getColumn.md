### Масив значень із заданої колонки

mixed getColumn (string $name, $dsq)

**$name** - назва колонки

**$dsq** - результат виконання запиту або SQL-запит

Цей метод повертає нумерований масив значень із заданої колонки в отриманих з бази даних. Набір даних може бути отриманий за допомогою запиту SELECT і містити кілька колонок, одну з яких можна отримати методом getColumn.

***

#### Приклад

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
