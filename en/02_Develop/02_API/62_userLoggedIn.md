###Определяет, авторизован ли пользователь через систему администрирования Evolution CMS (как менеджер) или на сайте (как пользователь) и возвращает информацию о нем

string userLoggedIn();

***

####Формат данных результата:

	Array ( [loggedIn] => 1 
			[id] => 1 
			[username] => siteadmin 
			[usertype] => web 
		)

***

####Пример:

	$txt = $modx->userLoggedIn();
