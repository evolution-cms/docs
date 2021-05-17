###Отримання даних

resource select($fields , $from [, $where [, $orderby [, $limit]]])

**$fields** - список необхідних полей із запиту
**$from** - таблиця для вибірки
**$where** - умова вибірки
**$orderby** - поле за яким потрібно зробити сортування
**$limit** - обмеження кількості записів в результаті запиту

Метод "select" дозволяє зробити звичайний запит в базу для отримання даних, які відповідають заданим параметрам.

***

####Приклад

```php
function login($username, $password) {  
		global $modx;  
		// передбачається, що ці значення були отримані
		// за допомогою POST до виклику функції  
		$username = $modx->db->escape($username); 
		$password = $modx->db->escape($password); 
		
		$res = $modx->db->select("id", $modx->getFullTableName('web_users'),  "username='" . $username ."' AND password='".md5($password)."'");  
		
		if($modx->db->getRecordCount($res)) {  
			
			$id = $modx->db->getValue($res);  
			$_SESSION['userid'] = $id;  
			// інші дії ...  
			
		}else{  
		
			// відповідного запису не знайшлося 
		}  
	}
```
