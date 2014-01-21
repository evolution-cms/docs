###Получение информации о пользователе сайта по заданному идентификатору

mixed getWebUserInfo (int $uid);

**$uid** - идентификатор пользователя сайта

***

####Пример

	$txt = $modx->getWebUserInfo(1); 
	print_r($txt); 
	
	 /* полученный результат: 
	
	Array ( [username] => siteadmin 
			[password] => 6f3cac6213ffceee27cc85414f458caa 
			[id] => 1 
			[internalKey] => 1 
			[fullname] => Site Admin 
			[role] => 0 
			[email] => you@yourdomain.com 
			[phone] =>  
			[mobilephone] =>  
			[blocked] => 0 
			[blockeduntil] => 0 
			[blockedafter] => 0 
			[logincount] => 29 
			[lastlogin] => 1229874475 
			[thislogin] => 1229874526 
			[failedlogincount] => 0 
			[sessionid] => e1bbad97732fbfe42c22bb6d8bc4de9d 
			[dob] => 0 
			[gender] => 0 
			[country] =>  
			[state] =>  
			[zip] =>  
			[fax] =>  
			[photo] =>  
			[comment] =>  
			[usertype] => web
		) 
	*/