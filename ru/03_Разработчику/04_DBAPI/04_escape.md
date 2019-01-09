###Экранирование потенциально-опасных символов

string escape(string $s)

**$s** - строка для обработки

При работе этой используется стандартная функция **mysql_real_escape_string**, а при ее отсутствии **mysql_escape_string**.

Рекомендуется всегда использовать этот метод для данных, перед тем как делать запрос в базу. Это позволит защитить базу от SQL-инъекций.

***

####Пример

	function login($username, $password) {  
		global $modx, $table_prefix;  
		
		$username = $modx->db->escape($username);  
		$password = $modx->db->escape($password);   
		
		$res = $modx->db->select("id", $table_prefix.".modx_web_users",  "username='$username' AND password='".md5($password)."'");  
		
		if($modx->db->getRecordCount($res)) {  
			$_SESSION['userid'] = $id;  
			
			// прочие действия...  
		} else {  
			// подходящей записи не нашлось  
		}  
	}