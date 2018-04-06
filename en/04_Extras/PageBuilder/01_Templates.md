The main template of the block must be defined for the `owner` key. In addition to this, the array must contain templates for each group of fields, and can contain templates for fields that have the `elements` property defined (`dropdown`, `checkbox`, `radio` fields). In these templates, the selected values for the `elements` property are available.

For example, if the `images` group is used in the field array, then an element with the `images` key must be defined in the templates which will contain either the template string:

```php
'images' => '<img src="[+image+]" alt="[+title+]" class="slide">'
```

Or an associative pattern array:

```php
'images' => [
  'item'  => '<img src="[+image+]" alt="[+title+]" class="slide">',
  'thumb' => '<div class="thumb" style="background-image: url([+image+])"></div>',
],
```

In the second case, the output of these elements in the parent template can be used as `[+images.item+]` and `[+images.thumb+]`.

#### Placeholders

You can use field names (eg `[+title+]`) and group field names (eg `[+images+]`, `[+images.thumb+]`) as a placeholders.

Also in templates for fields `dropdown`, `checkbox` and `radio`, the placeholders `[+value+]` and `[+title+]` are available.

Also the placeholders `[+index+]` and `[+iteration+]` are available in the `owner` template, and `[+{field_name}_index+]` and `[+{field_name}_iteration+]` are available in the group fields and selection fields.

#### Templates sources

Markup can be specified in the configuration directly, as shown in examples above.

Also can be specified name of the chunk with th template markup. To do this, use the `@CHUNK` binding, for example:

```php
'checkbox' => '@CHUNK all_fields_checkboxes',
```

It is also possible to load a template from a file:

```php
'owner' => '@FILE pagebuilder/all_fields.tpl',
```

In this example, the template file will be loaded from `MODX_BASE_PATH . "assets/templates/pagebuilder/all_fields.tpl"`. In general, the file is searched in the following directories:

```
assets/tvs/
assets/chunks/
assets/templates/
```

Alternatively, you can specify the full path from the site root. The first slash is not specified.

#### Templates groups

Templates can be grouped to use different groups of templates with the parameter `&templates` when outputting. For example, if you specify the following configuration for a block:

```php
'templates' => [
  'owner'  => '@CHUNK full_owner',
  'images' => '@CHUNK full_images'

  'anchors' => [
    'owner' => '@CHUNK link_owner',
  ],
],
```

then next snippet call will use the templates that are defined in the `anchors` group to output:

```
[[PageBuilder? &templates=`anchors`]]
```
