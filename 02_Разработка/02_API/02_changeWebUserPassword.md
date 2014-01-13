*Замечание: при возникновении ошибок метод возвращает информацию об ошибке на английском языке.*

mixed changeWebUserPassword(string $oldPwd, string $newPwd);

**$oldPwd** - старый пароль
**$newPwd** - новый пароль

***

####Пример:

````php
$txt = $modx->changeWebUserPassword('oldpassword','newpassword');
print_r($txt);
// полученный результат: true
````