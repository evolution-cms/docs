### Масив назв колонок

array getColumnNames($dsq)

**$dsq** - результат виконання запиту або SQL-запит

Цей метод повертає нумерований масив назв колонок в отриманих з бази даних. Набір даних може бути отриманий за допомогою запиту SELECT і містити кілька колонок, список назв яких можна отримати методом getColumnNames.

***

#### Приклад

	$result = $modx->db->select( 'id, name, age', 'people_table' );  
	
	// Отримати список назв колонок 
	$cols = $modx->db->getColumnNames( $result );
	
	for( $i = 0; $i < count( $cols ); $i++ ) {
		// Список назв колонок для простого заголовка
		$output .= $cols[$i] . ' | ';	 	
	}   
	
	while( $row = $modx->db->getRow( $result ) ) {		// Отримати дані з результату запиту
		$output .= '<br />' . $row['ItemID'] . ' | ' . $row['Name'] . ' | ' . $row['Image'];  
	}   
	
	return $output;