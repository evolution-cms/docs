###Обновление данных

boolean update($fields, $table, $where)

**$fields** - массив обновляемых значений
**$table** - таблица для обновления
**$where** - условие для поиска обновляемых записей

Метод "update" позволяет обновить данные в базе, передав новые значения в массиве $fields. Формат массива обновляемых значений - field => new_value, где "field" - название обновляемого поля, а "new_value" - новое значение.

***

####Пример

	$table = $modx->getFullTableName( 'cars_table' );  
	
	$fields = array('make'	=> $new_make,  
					'model'	=> $new_model,  
					'color'	=> $new_color,  
					'year'	=> $new_year,  
					'updated'=> time()  
					);  
	
	$result = $modx->db->update( $fields, $table, 'id = "' . $id . '"' );  	
	if( $result ) {  
		echo 'Информация обновлена!';  
	} else {  
		echo 'Возникла проблема во время запроса...';  
	}