### Функція виклику чанка із заміною плейсхолдерів на значення

**Важливо:** при використанні методу необхідно приділити увагу параметрам $prefix и $sufix, оскільки за замовчуванням їхні значення вважаються нестандартними.

**Важливо:** метод не працює при виклику з підключеного файла (include, include_once, require, require_once)

```
string parseChunk(string $chunkName, array $chunkArr[, string $prefix[, string $suffix]]);
```

**$chunkName** - назва чанка (чутливість до регістру).

**$chunkArr** - масив зі значеннями плейсхолдерів.

**$prefix** - значення початку плейсхолдера. Зазвичай використовується '[+', за замовчуванням: {

**$suffix** - значення завершення плейсхолдера. Зазвичай використовується '+]', за замовчуванням: }

## Приклад:

**Виклик**
```
echo $modx->parseChunk(
	'test_chunk',
	array(
		'uname'=>'Евеліно',
		'balance'=>'1000000'
	),
	$prefix = '[+',
	$suffix = '+]'
);
```
**Чанк test_chunk:**
```
Привіт, [+uname+]!<BR>
На Вашому рахунку [+balance+] грн.
```
**Результат:**
```
Привіт, Евеліно!
На Вашому рахунку 1000000 грн.
```
	
## Початковий код функції:
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