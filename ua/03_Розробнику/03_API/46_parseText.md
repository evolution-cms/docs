###Функція для заміни плейсхолдерів на значення

string parseText(string $chunkName, array $chunkArr[, string $prefix[, string $suffix]]);

**$chunkName** - рядок містить текст з плейсхолдерами

**$chunkArr** - масив зі значеннями плейсхолдерів

**$prefix** - значення початку плейсхолдера. Зазвичай використовується '[+'
за замовчуванням: [+

**$suffix** - значення завершення плейсхолдера. Зазвичай використовується '+]'
за замовчуванням: +]

***

####Формат визначення значень плейсхолдерів:

	Array ( [name] => modx.im 
			[type] => site 
			[url] => http://modx.im )
Це буде відповідати плейсхолдерам name, type та url, які при обробці замінюватися відповідними значеннями.

***

####Приклад:
	$text = 'Приклад текста з тегами, [+name+] , [+type+], [+url+]';
	$txt = $modx->parseText($text, array( 'name' => 'modx.im', 'type' => 'site', 'url' => 'http://modx.im' ), '[+', '+]' );
	//поверне: 
	Приклад текста з тегами, modx.im , site, http://modx.im
	
	
####Вихідний код функції
	/**
     * parseText
     * @version 1.0 (2013-10-17)
     * 
     * @desc Replaces placeholders in text with required values.
     * 
     * @param $chunk {string} - String to parse. @required
     * @param $chunkArr {array} - Array of values. Key — placeholder name, value — value. @required
     * @param $prefix {string} - Placeholders prefix. Default: '[+'.
     * @param $suffix {string} - Placeholders suffix. Default: '+]'.
     * 
     * @return {string} - Parsed text.
     */
	function parseText($chunk, $chunkArr, $prefix = '[+', $suffix = '+]'){
		if (!is_array($chunkArr)){
			return $chunk;
		}
		
		foreach ($chunkArr as $key => $value){
			$chunk = str_replace($prefix.$key.$suffix, $value, $chunk);
		}
		
		return $chunk;
	}	
