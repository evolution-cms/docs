### Пример 1

В этом примере создается контентный блок с однострочным и многострочным текстовыми полями, который будет выводиться в шаблонах с идентификатором "2" под именем "Example 1":

```
<?php
    return [
        'title' => 'Example 1',
        'show_in_templates' => 2,
        'templates' => [
            'owner' => '
                <div>Text:<br> [+text+]</div>
                <div>Textarea:<br> [+textarea+]</div>
            ',
        ],
        'fields' => [
            'text' => [
                'caption' => 'Text',
                'type'    => 'text',
            ],
            'textarea' => [
                'caption' => 'Textarea',
                'type'    => 'textarea',
                'default' => 'Default content for textarea',
                'height'  => '80px',
            ],
        ],
    ];
```

### Пример 2

В следующем примере контентный блок будет содержать однострочное поле для заголовка, дату и список изображений. 
Основной шаблон вывода будет загружен из чанка с именем "example2".

Блок будет выводиться только в документах с идентификаторами "37" и "41" под именем "Example 2":

```
<?php
    return [
        'title' => 'Example 2',
        'show_in_docs' => [ 37, 41 ],
        'templates' => [
            'owner'  => '@CHUNK example2',
            'images' => '<img src="[+image+]">',
        ],
        'fields' => [
            'text' => [
                'caption' => 'Text',
                'type'    => 'text',
            ],
            'date' => [
                'caption' => 'Date',
                'type'    => 'date',
            ],
            'images' => [
                'caption' => 'Images',
                'type'    => 'group',
                'fields'  => [
                    'image' => [
                        'caption' => 'Image',
                        'type'    => 'image',
                    ],
                ],
            ],
        ],
    ];
```
