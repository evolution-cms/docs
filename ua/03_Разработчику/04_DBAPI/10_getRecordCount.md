### Кількість записів в результаті запиту

integer getRecordCount ($data_set)

**$data_set** - з'єднання з базою

Повертає кількість записів, яке було отримано в результаті запиту SELECT.

***

#### Приклад

	$output = '';  
	$result = $modx->db->select('make, model, color, year', 'cars', 'year > 2001');  	$total_rows = $modx->db->getRecordCount( $result );   
	
	if( $total_rows >= 1 ) {  
		$output .= $total_rows . ' машин новіше 2001 року:<br />';  
		while( $row = $modx->db->getRow( $result ) ) {  
			$output .= 'Виробник: ' . $row['make'] . ' | Модель: ' . $row['model'] .  ' | Колір: ' . $row['color'] . ' | Рік: ' . $row['year'] . '<br />';  
		}  
	}else{  
		$output = 'Немає машин новіше 2001 року!';  
	}  
	echo $output;