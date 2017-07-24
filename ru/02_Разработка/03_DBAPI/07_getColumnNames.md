###Массив названий колонок

array getColumnNames($dsq)

**$dsq** - результат выполнения запроса или SQL-запрос

Этот метод возвращает нумерованный массив названий колонок в полученных из базы данных. Набор данных может быть получен с помощью запроса SELECT и содержать несколько колонок, список названий которых можно получить методом getColumnNames.

***

####Пример

	$result = $modx->db->select( 'id, name, age', 'people_table' );  
	
	// Получить список названий колонок  
	$cols = $modx->db->getColumnNames( $result );
	
	for( $i = 0; $i < count( $cols ); $i++ ) {
		// Список названий колонок для простого заголовка  
		$output .= $cols[$i] . ' | ';	 	
	}   
	
	while( $row = $modx->db->getRow( $result ) ) {		// Получить данные из результата запроса  
		$output .= '<br />' . $row['ItemID'] . ' | ' . $row['Name'] . ' | ' . $row['Image'];  
	}   
	
	return $output;