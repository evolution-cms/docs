### Зміна пароля для WEB-користувача ###

*Примітка: при виникненні помилок метод повертає інформацію про помилку англійською мовою.*
```
mixed changeWebUserPassword(string $oldPwd, string $newPwd);
```
**$oldPwd** - старий пароль

**$newPwd** - новий пароль



### Приклаж:###

```php
$txt = $modx->changeWebUserPassword('oldpassword','newpassword');
print_r($txt);
// отриманий результат: true
````


### Початковий код функції ###
`Файл: /manager/includes/document.parser.class.inc.php`
```
/**
 * Change current web user's password
 *
 * @todo Make password length configurable, allow rules for passwords and translation of messages
 * @param string $oldPwd
 * @param string $newPwd
 * @return string|boolean Returns true if successful, oterhwise return error
 *                        message
 */
public function changeWebUserPassword($oldPwd, $newPwd)
{
	$rt = false;
	if ($_SESSION["webValidated"] == 1) {
		$tbl = $this->getFullTableName("web_users");
		$ds = $this->db->select('id, username, password', $tbl, "id='" . $this->getLoginUserID() . "'");
		if ($row = $this->db->getRow($ds)) {
			if ($row["password"] == md5($oldPwd)) {
				if (strlen($newPwd) < 6) {
					return "Password is too short!";
				} elseif ($newPwd == "") {
					return "You didn't specify a password for this user!";
				} else {
					$this->db->update(array(
						'password' => $this->db->escape($newPwd),
					), $tbl, "id='" . $this->getLoginUserID() . "'");
					// invoke OnWebChangePassword event
					$this->invokeEvent("OnWebChangePassword", array(
						"userid" => $row["id"],
						"username" => $row["username"],
						"userpassword" => $newPwd
					));
					return true;
				}
			} else {
				return "Incorrect password.";
			}
		}
	}
	return $rt;
}
```	