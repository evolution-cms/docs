###Удаление данных из базы

bool delete(string $from [, string $where [, string $fields]])

**$from** - таблица, в которой необходимо удалить данные
**$where** - условие, по которому необходимо удалить данные
**$fields** - список полей, которые требуется удалить. Если не указан, то удаляется весь ряд

***

####Пример

	//Удаление пользователя из базы по идентификатору  
	global $modx, $table_prefix;  
	$id = $modx->db->escape($id);  
	$modx->db->delete($table_prefix.".modx_web_users", "id = $id");