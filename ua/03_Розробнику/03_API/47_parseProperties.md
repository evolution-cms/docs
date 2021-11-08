###Розбирає рядок конфігурації плагіна або сніппета і повертає поточні значення в вигляді масиву

array parseProperties(string $propertyString);

**$propertyString** - рядок конфігурації

***

####Приклад

	$propertys = "&tinyFormats=Block Formats;text;p,h1,h2,h3,h4,h5,h6,div,blockquote,code,pre,address &entity_encoding=Entity Encoding;list;named,numeric,raw;named"; 
	
	$txt = $modx->parseProperties($propertys); 
	print_r($txt); // отриманий результат: 
	/* Array ( [tinyFormats] => p,h1,h2,h3,h4,h5,h6,div,blockquote,code,pre,address 			   [entity_encoding] => named 
		 	 ) 
	*/
