Автор: <a href="https://github.com/mnoskov/clientsettings">mnoskov</a>

<img src="https://img.shields.io/badge/PHP-%3E=5.6-green.svg?php=5.6">

Модуль для создания формы пользовательских настроек.

Для начала работы нужно переименовать файлы конфигурации `assets/modules/clientsettings/config/*.php.sample` в `*.php`.

Конфигурация полей берется из файлов `*.php` из папки `/assets/modules/clientsettings/config/`. Каждый файл - это отдельная вкладка. Такой способ хранения позволяет легко изменять и переносить конфигурацию.

Пример файла конфигурации:
```php
<?php

return [
    'caption' => 'Заголовок таба',
    'introtext' => 'Описание таба',
    'settings' => [
        'field_text' => [
            'caption' => 'Текст',
            'type'  => 'text',
            'note'  => 'Это просто текст',
            'default_text' => 'Значение по умолчанию',
        ],
        
        ...
        
    ],
];
```

Типы полей описаны <a href="/info/terminology-2/chto_takoe_parametr.html">здесь</a>.

Помимо стандартных полей можно использовать тип `divider` для разделения списка полей на группы:
```php
'field_text' => [
    'caption' => 'Заголовок группы полей',
    'type'  => 'divider',
],
```
