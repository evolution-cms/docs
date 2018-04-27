Функция для вызова чанка с заменой плейсхолдеров на значения

**Важно:** при использовании метода обязательно уделяйте внимание параметрам $prefix и $sufix, так как их значения по умолчанию являются нестандартными.

**Важно:** этот метод не работает при вызове из подключенного файла (include, include_once, require, require_once)

```
string parseChunk(string $chunkName, array $chunkArr[, string $prefix[, string $suffix]]);
```

**$chunkName** - название чанка (чувствительно к регистру!)

**$chunkArr** - массив со значениями плейсхолдеров

**$prefix** - значение начала плейсхолдера. Обычно используется '[+', по умолчанию: {

**$suffix** - значение завершения плейсхолдера. Обычно используется '+]', по умолчанию: }

## Пример:

**Вызов:**
```
echo $modx->parseChunk(
	'test_chunk',
	array(
		'uname'=>'Иван',
		'balance'=>'0.23'
	),
	$prefix = '[+',
	$suffix = '+]'
);
```
**Чанк test_chunk:**
```
Привет, [+uname+]!<BR>
У вас на счету [+balance+] руб.
```
**Результат:**
```
Привет, Иван!
У вас на счету 0.23 руб.
```
	
## Исходный код функции
```
    /**
     * parseChunk
     * @version 1.1 (2013-10-17)
     *
     * @desc Replaces placeholders in a chunk with required values.
     *
     * @param $chunkName {string} - Name of chunk to parse. @required
     * @param $chunkArr {array} - Array of values. Key — placeholder name, value — value. @required
     * @param string $prefix {string}
     * - Placeholders prefix. Default: '{'.
     * @param string $suffix {string}
     * - Placeholders suffix. Default: '}'.
     * @return bool|mixed|string {string; false} - Parsed chunk or false if $chunkArr is not array.
     * - Parsed chunk or false if $chunkArr is not array.
     */
    public function parseChunk($chunkName, $chunkArr, $prefix = '{', $suffix = '}')
    {
        //TODO: Wouldn't it be more practical to return the contents of a chunk instead of false?
        if (!is_array($chunkArr)) {
            return false;
        }

        return $this->parseText($this->getChunk($chunkName), $chunkArr, $prefix, $suffix);
    }	
```