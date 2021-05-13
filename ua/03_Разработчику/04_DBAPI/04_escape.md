### Екранування потенційно-небезпечних символів

string escape(string $s)

**$s** - рядок для обробки

При роботі цієї використовується стандартна функція **mysql_real_escape_string**, а при її відсутності **mysql_escape_string**.

Рекомендується завжди використовувати цей метод для даних, перед тим як робити запит до бази. Це дозволить захистити базу від SQL-ін'єкцій.

***

#### Приклад

	function login($username, $password) {  
		global $modx, $table_prefix;  
		
		$username = $modx->db->escape($username);  
		$password = $modx->db->escape($password);   
		
		$res = $modx->db->select("id", $table_prefix.".modx_web_users",  "username='$username' AND password='".md5($password)."'");  
		
		if($modx->db->getRecordCount($res)) {  
			$_SESSION['userid'] = $id;  
			
			// інші дії ...  
		} else {  
			// відповідного запису не знайшлося 
		}  
	}