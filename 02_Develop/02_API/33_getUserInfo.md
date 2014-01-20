Получение информации о менеджере по заданному идентификатору

mixed getUserInfo (int $uid);

$uid - идентификатор менеджера
Пример

$txt = $modx->getUserInfo(1); print_r($txt); // полученный результат: /* Array ( [username] => admin [password] => 21232f297a57a5a743894a0e4a801fc3 [id] => 1 [internalKey] => 1 [fullname] => Default admin account [role] => 1 [email] => admin@modxvanilla [phone] =>  [mobilephone] =>  [blocked] => 0 [blockeduntil] => 0 [blockedafter] => 0 [logincount] => 11 [lastlogin] => 1226838879 [thislogin] => 1229864673 [failedlogincount] => 0 [sessionid] => e1bbad97732fbfe42c22bb6d8bc4de9d [dob] => 0 [gender] => 0 [country] =>  [state] =>  [zip] =>  [fax] =>  [photo] =>  [comment] =>  [usertype] => manager ) */