###Функция для вызова чанка с обработкой для замены плейсхолдеров на значения

*Замечание: при использовании метода обязательно уделяйте внимание параметрам $prefix и $sufix, так как их значения по умолчанию являются нестандартными.*

*Замечание: Этот метод не работает при вызове из подключенного файла (include, include_once, require, require_once).*

string parseChunk(string $chunkName, array $chunkArr[, string $prefix[, string $suffix]]);

**$chunkName** - название чанка (чувствительно к регистру!)

**$chunkArr** - массив со значениями плейсхолдеров

**$prefix** - значение начала плейсхолдера. Обычно используется '[+'
по умолчанию: {

**$suffix** - значение завершения плейсхолдера. Обычно используется '+]'
по умолчанию: }

***

####Формат определения значений плейсхолдеров:

	Array ( [name] => Spros66.ru 
			[type] => site 
			[url] => http://spros66.ru )
Это будет соответствовать плейсхолдерам name, type и url, которые при обработке заменяться соответствующими значениями.

***

####Пример:

	$txt = $modx->parseChunk('ditto_blog', array( 'name' => 'Spros66.ru', 'type' => 'site', 'url' => 'http://spros66.ru' ), '[+', '+]' );
	//вернет содержимое чанка ditto_blog, в котором будут заменены плейсхолдеры [+name+], [+type+] и [+url+] на значения.
	
####Исходный код функции
	/**
	 * parseChunk
	 * @version 1.1 (2013-10-17)
	 * 
	 * @desc Replaces placeholders in a chunk with required values.
	 * 
	 * @param $chunkName {string} - Name of chunk to parse. @required
	 * @param $chunkArr {array} - Array of values. Key — placeholder name, value — value. @required
	 * @param $prefix {string} - Placeholders prefix. Default: '{'.
	 * @param $suffix {string} - Placeholders suffix. Default: '}'.
	 * 
	 * @return {string; false} - Parsed chunk or false if $chunkArr is not array.
	 */
	function parseChunk($chunkName, $chunkArr, $prefix = '{', $suffix = '}'){
		//TODO: Wouldn't it be more practical to return the contents of a chunk instead of false?
		if (!is_array($chunkArr)){
			return false;
		}
		
		return $this->parseText($this->getChunk($chunkName), $chunkArr, $prefix, $suffix);
	}	