### Количество записей в результате запроса

integer getRecordCount ($data_set)

**$data_set** - соединение с базой

Возвращает количество записей, которое было получено в результате запроса SELECT.

***

#### Пример
````
$output = '';  
$result = $modx->db->select('make, model, color, year', 'cars', 'year > 2001');  	
$total_rows = $modx->db->getRecordCount( $result );   
	
if( $total_rows >= 1 ) {  
	$output .= $total_rows . ' машин новее 2001 года:<br />';  
	while( $row = $modx->db->getRow( $result ) ) {  
		$output .= 'Производитель: ' . $row['make'] . ' | Модель: ' . $row['model'] .  ' | Цвет: ' . $row['color'] . ' | Год: ' . $row['year'] . '<br />';  
	}  
}else{  
	$output = 'Нет машин новее 2001 года!';  
}  
echo $output;
````
