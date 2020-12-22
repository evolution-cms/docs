### Отримання плейсхолдера

*Зауваження: багато сніпетів мають власні плейсхолдери, які вони обробляють самостійно. Метод getPlaceholder може про них нічого не знати.*

string getPlaceholder(string $name);

**$name** - назва плейсхолдера. Здається без синтаксичної конструкції.

***

####Приклад
```php
$txt = $modx->getPlaceholder('MyPlaceholder');
//поверне  значення плейсхолдера MyPlaceholder.
```
***

####Вихідний код
```php
/**
* Повертає значення плейсхолдера
*
* @param string $name Placeholder name
* @return string Placeholder value
*/
function getPlaceholder($name) {
    return isset($this->placeholders[$name]) ? $this->placeholders[$name] : null;
}
```
