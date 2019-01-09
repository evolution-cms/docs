Often there is a need for additional data processing before output. For this purpose, `prepare` and `prepareWrap` are available as settings in the configuration file or as snippet parameters.

The value can be a snippet name, a function name (also in the configuration file you can specify the *Closure*), or a comma-separated list, or an array of them.

The parameters of the function/snippet following:

Parameter | Description
--------- | -----------
`$data`     | Current values
`$modx`     | Instance of the DocumentParser class
`$_multiTV` | Instance of the multiTV class, to work with storage methods

The function/snippet should always return values, even if they have not changed.

Examples:

```php
// in configuration file:
function prepareRowsFunction($data, $modx, $_multiTV) {
   return $data;
}

$settings['prepare'] = 'prepareRowsSnippet';
// or
$settings['prepare'] = function($data, $modx, $_multiTV) {
   return $data;
};
// or
$settings['prepare'] = 'prepareRowsSnippet,prepareRowsFunction'; 
// or
$settings['prepare'] = ['prepareRowsSnippet', 'prepareRowsFunction']; 
// or
$settings['prepare'] = ['prepareRowsSnippet', function($data, $modx, $_multiTV) {
   return $data;
}]; 
```

```
// in tempalte
[[multiTV? &tvName=`test` &prepare=`prepareRowsSnippet,prepareRowsFunction`]]
```

Values of the `$data` parameter of the prepare function, in addition to the field values specified in the variable configuration, will be as follows:

Key | Description
--- | -----------
`docid` | Current document ID
`iteration` | Current iteration Number (starts with 1)
`row` | `row.number` - current iteration Number (starts with 1), `row.total` - total number of elements

Values of the `$data` parameter for `prepareWrap`:

Key | Description
--- | -----------
`docid` | Current document ID
`wrapper` | Array of rendered elements
`rows` | `rows.offset` - number of skipped items, `rows.total` - total number of elements

Examples:

```php
$settings['prepare'] = function($data, $modx, $_multiTV) {
   $store = $_multiTV->getStore('storekey');

   if (is_null($store)) {
      $store = $modx->runSnippet('HeavySnippet');
      $_multiTV->setStore('storekey', $store);
   }

   return $data;
};
```

```php
$settings['prepare'] = function($data, $modx, $_multiTV) {
   if (!empty($data['file'])) {
      $extension = pathinfo($data['file'], PATHINFO_EXTENSION);
      $data['icon'] = 'icon-document-' . $extension;
   }

   return $data;
};
```
