###Функция для замены плейсхолдеров на значения 

string parseText(string $chunkName, array $chunkArr[, string $prefix[, string $suffix]]);

**$chunkName** - строка содержащая текст с плейсхолдерами

**$chunkArr** - массив со значениями плейсхолдеров

**$prefix** - значение начала плейсхолдера. Обычно используется '[+'
по умолчанию: [+

**$suffix** - значение завершения плейсхолдера. Обычно используется '+]'
по умолчанию: +]

***

####Формат определения значений плейсхолдеров:

	Array ( [name] => modx.im 
			[type] => site 
			[url] => http://modx.im )
Это будет соответствовать плейсхолдерам name, type и url, которые при обработке заменяться соответствующими значениями.

***

####Пример:
	$text = 'Пример текста с тегами, [+name+] , [+type+], [+url+]';
	$txt = $modx->parseText($text, array( 'name' => 'modx.im', 'type' => 'site', 'url' => 'http://modx.im' ), '[+', '+]' );
	//вернет: 
	Пример текста с тегами, modx.im , site, http://modx.im
	
	
####Исходный код функции
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