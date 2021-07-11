###оновлення даних

boolean update($fields, $table, $where)

**$fields** - масив оновлюваних значень
**$table** - таблиця для оновлення
**$where** - умова для пошуку оновлюваних записів

Метод "update" дозволяє оновити дані в базі, передавши нові значення в масиві $fields. Формат масиву оновлюваних значень - field => new_value, де "field" - назва оновлюваного поля, а "new_value" - нове значення.

***

####Приклад

	$table = $modx->getFullTableName( 'cars_table' );  
	
	$fields = array('make'	=> $new_make,  
					'model'	=> $new_model,  
					'color'	=> $new_color,  
					'year'	=> $new_year,  
					'updated'=> time()  
					);  
	
	$result = $modx->db->update( $fields, $table, 'id = "' . $id . '"' );  	
	if( $result ) {  
		echo 'Інформація оновлена!';  
	} else {  
		echo 'Виникла проблема під час запиту...';  
	}