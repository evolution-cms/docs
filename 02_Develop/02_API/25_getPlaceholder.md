### Получение плейсхолдера

*Замечание: многие сниппеты имеют собственные плейсхолдеры, которые они обрабатывают самостоятельно. Метод getPlaceholder может о них ничего не знать.*

string getPlaceholder(string $name);

**$name** - название плейсхолдера. Задается без синтаксической конструкции.

***

####Пример
```php
$txt = $modx->getPlaceholder('MyPlaceholder');
//вернет значение плейсхолдера MyPlaceholder.
```
***

####Исходный код
```php
/**
* Returns the placeholder value
*
* @param string $name Placeholder name
* @return string Placeholder value
*/
function getPlaceholder($name) {
    return isset($this->placeholders[$name]) ? $this->placeholders[$name] : null;
}
```