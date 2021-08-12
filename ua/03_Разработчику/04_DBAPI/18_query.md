###Прямий запит до бази даних
mixed query($sql)

**$sql** - рядок з SQL-запитом

Різні методи DBAPI роблять в кінцевому підсумку запит до бази за допомогою методу "query". Якщо не вистачає стандартних можливостей спеціальних методів, то можна зробити будь-який SQL-запит на пряму.
***

####Приклад

	$output = '';  
	$result = $modx->db->query( 'SELECT id, name, joined FROM `user_table` GROUP BY `member_type` ORDER BY name ASC' );   
	
	while( $row = $modx->db->getRow( $result ) ) {  
		$output .=  '<br /> Ідентифікатор: ' . $row['id'] . 
					'<br /> Ім'я: ' . $row['name'] . 
					'<br /> Участь: ' . $row['joined']  . 
					'<br />---------<br />';  
	}  
	
	echo $output;