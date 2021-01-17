Возвращает идентификатор авторизованного пользователя или NULL, если пользователь неавторизован

*Замечание: метод учитывает соответствие типа пользователя. Поэтому для авторизованного менеджера на самом сайте идентификатор определяться не будет (вернется null).*

`mixed getLoginUserID();`

***

### Пример

```
echo 'Идентификатор пользователя: ' . $modx->getLoginUserID(); 
// полученный результат: 
// Идентификатор пользователя: 1
```

### Функция

```
/**
* Returns current user id.
*
* @param string $context . Default is an empty string which indicates the method should automatically pick 'web (frontend) or 'mgr' (backend)
* @return string
*/
public function getLoginUserID($context = '')
{
	$out = false;

	if (!empty($context)) {
		if (is_scalar($context) && isset($_SESSION[$context . 'Validated'])) {
			$out = $_SESSION[$context . 'InternalKey'];
		}
	} else {
		switch (true) {
			case ($this->isFrontend() && isset ($_SESSION['webValidated'])): {
				$out = $_SESSION['webInternalKey'];
				break;
			}
			case ($this->isBackend() && isset ($_SESSION['mgrValidated'])): {
				$out = $_SESSION['mgrInternalKey'];
				break;
			}
		}
	}
	return $out;
}
```
