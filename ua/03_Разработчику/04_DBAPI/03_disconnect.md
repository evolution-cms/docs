### Закриває поточне з'єднання з базою

void disconnect()

***

#### Приклад

	//Створення з'єднання 
	$modx->db->connect('123.45.6.7', 'mydb', 'user', 'password', true);  
	$res = $modx->db->select('*', 'this_table');  
	while($tmp = $modx->db->getRow($res, 'assoc')) {  
	// обробка отриманих даних  
	}  
	
	// Відключення  
	$modx->db->disconnect()  
	
	// Повторне підключення 
	$modx->db->connect();