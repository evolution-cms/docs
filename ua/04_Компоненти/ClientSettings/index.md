Автор: <a href="https://github.com/mnoskov/clientsettings">mnoskov</a>

<img src="https://img.shields.io/badge/PHP-%3E=5.6-green.svg?php=5.6">
Модуль для створення форми користувацьких налаштувань.

Для початку роботи необхідно перейменувати файли конфігурації assets/modules/clientsettings/config/*.php.sample у *.php.

Конфігурація полів береться з файлів *.php у папці /assets/modules/clientsettings/config/. Кожен файл — це окрема вкладка. Такий спосіб зберігання дозволяє легко змінювати та переносити конфігурацію.

Приклад файлу конфігурації:

```php
<?php

return [
    'caption' => 'Заголовок вкладки',
    'introtext' => 'Опис вкладки',
    'settings' => [
        'field_text' => [
            'caption' => 'Текст',
            'type'  => 'text',
            'note'  => 'Це просто текст',
            'default_text' => 'Значення за замовчуванням',
        ],
        
        ...
        
    ],
];
```
Типи полів описані <a href="/info/terminology-2/chto_takoe_parametr.html">тут</a>.

Окрім стандартних полів можна використовувати тип divider для розділення списку полів на групи:

```php
'field_text' => [
    'caption' => 'Заголовок групи полів',
    'type'  => 'divider',
],
```
