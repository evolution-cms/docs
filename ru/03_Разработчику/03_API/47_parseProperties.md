###Разбирает строку конфигурации плагина или сниппета и возвращает текущие значения в виде массива

array parseProperties(string $propertyString);

**$propertyString** - строка конфигурации

***

####Пример

	$propertys = "&tinyFormats=Block Formats;text;p,h1,h2,h3,h4,h5,h6,div,blockquote,code,pre,address &entity_encoding=Entity Encoding;list;named,numeric,raw;named"; 
	
	$txt = $modx->parseProperties($propertys); 
	print_r($txt); // полученный результат: 
	/* Array ( [tinyFormats] => p,h1,h2,h3,h4,h5,h6,div,blockquote,code,pre,address 			   [entity_encoding] => named 
		 	 ) 
	*/