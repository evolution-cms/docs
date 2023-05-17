### Changing the password for the WEB-user
Note: If errors occur, the method returns error information in English.

mixed changeWebUserPassword(string $oldPwd, string $newPwd);

**$oldPwd** - old password
**$newPwd** - new password

#### Example:

````php
$txt = $modx->changeWebUserPassword('oldpassword','newpassword');
print_r($txt);
// result: true
````


