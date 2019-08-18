Author: <a href="https://github.com/mnoskov/clientsettings">mnoskov</a>

<img src="https://img.shields.io/badge/PHP-%3E=5.6-green.svg?php=5.6">

A module for creating a custom settings form.

To get started, you need to rename the configuration files `assets/modules/clientsettings/config/*.php.sample` to `*.php`.

Fields configuration is taken from `*.php` files in `/assets/modules/clientsettings/config/` folder. Each file is a separate tab. This storage method makes it easy to modify and migrate the configuration.

Example:
```php
<?php

return [
    'caption' => 'Tab title',
    'introtext' => 'Tab description',
    'settings' => [
        'field_text' => [
            'caption' => 'Field title',
            'type'  => 'text',
            'note'  => 'Field description',
            'default_text' => 'Field default value',
        ],
        
        ...
        
    ],
];
```

Field types are described <a href="/en/info/terminology-2/chto_takoe_parametr.html">here</a>.

In addition to standard fields, you can use the `divider` type to divide a list of fields into groups:
```php
'field_text' => [
    'caption' => 'Fields group title',
    'type'  => 'divider',
],
```
