###Закрывает текущее соединение с базой

void disconnect()

***

####Пример

	//Создание соединения  
	$modx->db->connect('123.45.6.7', 'mydb', 'user', 'password', true);  
	$res = $modx->db->select('*', 'this_table');  
	while($tmp = $modx->db->getRow($res, 'assoc')) {  
	// обработка полученных данных  
	}  
	
	// Отключение  
	$modx->db->disconnect()  
	
	// Повторное соединение  
	$modx->db->connect();