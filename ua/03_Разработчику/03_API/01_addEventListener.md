### Додати обробник події для плагіна ###

**Примітка:** використовується тільки для поточного циклу виконання.
```
string addEventListener(string $evtName, string $pluginName);
```
**$evtName** - ім'я події

**$pluginName** - назва плагіну


### Початковий код функції ###

`Файл: /manager/includes/document.parser.class.inc.php`

```
/**
 * Add an event listener to a plugin - only for use within the current execution cycle
 *
 * @param string $evtName
 * @param string $pluginName
 * @return boolean|int
 */
public function addEventListener($evtName, $pluginName)
{
	if (!$evtName || !$pluginName) {
		return false;
	}
	if (!array_key_exists($evtName, $this->pluginEvent)) {
		$this->pluginEvent[$evtName] = array();
	}
	return array_push($this->pluginEvent[$evtName], $pluginName); // return array count
}
```