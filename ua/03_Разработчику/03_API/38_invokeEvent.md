###Викликати задану подію

array invokeEvent(string $evtName, array $extParams);

**$evtName** - найменування події
**$extParams** - параметри події у вигляді набору значень name => value

***

####Приклад

	$modx->invokeEvent("OnWebChangePassword", array( "userid" => $id, "username" => $username, "userpassword" => $newpwd ));
