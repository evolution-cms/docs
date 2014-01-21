###Возвращает информацию о клиентском системном окружении (браузер, операционная система и т.д.)

array getUserData();

***

####Формат данных результата:

	Array ( [ip] => 127.0.0.1 
			[ua] => mozilla/5.0 (windows; u; windows nt 5.1; ru; rv:1.9.0.3) gecko/2008092417 firefox/3.0.3 
			[browser] => mz 
			[long_name] => mozilla 
			[version] => 1.9.0.3 
			[maj_ver] => 1 
			[min_ver] => .9.0.3 
			[letter_ver] =>  
			[javascript] => 1.5 
			[platform] => win 
			[os] => xp 
			[language] => ru,en-us,en 
			[gecko] => 2008092417 
			[gecko_ver] => 1.9.0.3 
			[html] => true 
			[images] => true 
			[frames] => true 
			[tables] => true 
			[java] => true 
			[plugins] => true 
			[css2] => true 
			[css1] => true 
			[iframes] => true 
			[xml] => true 
			[dom] => true 
			[hdml] => false 
			[wml] => false 
			[must_cache_forms] => true 
			[avoid_popup_windows] => false 
			[cache_ssl_downloads] => false 
			[break_disposition_header] => false 
			[empty_file_input_value] => false 
			[scrollbar_in_way] => false 
		)

***

####Пример

	$txt = $modx->getUserData();
	//даст информацию о системном окружении пользователя.