###Получение данных

resource select($fields , $from [, $where [, $orderby [, $limit]]])

**$fields** - список необходимых полей из запроса
**$from** - таблица для выборки
**$where** - условие выборки
**$orderby** - поле по которому нужно сделать сортировку
**$limit** - ограничение количества записей в результате запроса

Метод "select" позволяет сделать обычный запрос в базу для получения данных, которые соответствуют заданным параметрам.

***

####Пример

```php
function login($username, $password) {  
		global $modx;  
		// предполагается, что эти значения были получены
		// с помощью POST до вызова функции   
		$username = $modx->db->escape($username); 
		$password = $modx->db->escape($password); 
		
		$res = $modx->db->select("id", $modx->getFullTableName('web_users'),  "username='" . $username ."' AND password='".md5($password)."'");  
		
		if($modx->db->getRecordCount($res)) {  
			
			$id = $modx->db->getValue($res);  
			$_SESSION['userid'] = $id;  
			// прочие действия...  
			
		}else{  
		
			// подходящей записи не нашлось  
		}  
	}
```
