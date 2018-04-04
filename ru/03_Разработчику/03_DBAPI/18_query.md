###Прямой запрос в базу данных

mixed query($sql)

**$sql** - строка с SQL-запросом

Различные методы DBAPI делают в конечном итоге запрос в базу с помощью метода "query". Если не хватает стандартных возможностей специальных методов, то можно сделать любой SQL-запрос напрямую.

***

####Пример

	$output = '';  
	$result = $modx->db->query( 'SELECT id, name, joined FROM `user_table` GROUP BY `member_type` ORDER BY name ASC' );   
	
	while( $row = $modx->db->getRow( $result ) ) {  
		$output .=  '<br /> Идентификатор: ' . $row['id'] . 
					'<br /> Имя: ' . $row['name'] . 
					'<br /> Участие: ' . $row['joined']  . 
					'<br />---------<br />';  
	}  
	
	echo $output;