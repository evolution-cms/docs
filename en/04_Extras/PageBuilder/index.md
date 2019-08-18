Author: <a href="https://github.com/mnoskov/pagebuilder">mnoskov</a>

<img src="https://img.shields.io/badge/PHP-%3E=5.6-green.svg?php=5.6">

The plug-in allows the developer to define a set of blocks with a certain markup and a list of fields, so that the content manager uses those blocks that it considers necessary, with its content.

After installation, you must create the configuration files or rename the `*.php.sample` files to `*.php`. In the administration panel, the plugin adds a new tab to the edit-resource page. To show contents of the blocks use the snippet `[[PageBuilder]]`.

The configuration for the blocks is taken from the config folder. To create a new block, you need to create a `<block-name>.php` file in this folder, which should return an associative array. To create a container, you need to create a file `container.<container-name>.php`. The structure of the array is as follows:

<table>
<tr><th>Key</th><th>Value</th></tr>
<tr><td>title</td><td>Block name visible to the manager when filling in Value</td></tr>
<tr><td>container</td><td>Name of the container (or the array of names) in which the block will be displayed.</td></tr>
<tr>
<td>fields</td>
<td>
Associative array of used fields, in which the keys are field identifiers, and the values are the arrays of options for these fields.

The possible field types and options are listed below.
</td>
</tr>
<tr><td>show_in_templates</td><td>Array of template identifiers for which editing and output of blocks are available</td></tr>
<tr><td>hide_in_docs</td><td>Array of document identifiers for which editing and output are not available</td></tr>
<tr><td>show_in_docs</td><td>
  
An array of document identifiers for which editing and output of blocks are available.

If this parameter is specified, then `hide_in_docs` is not taken into account.

If none of the parameters restricting access is specified, the blocks will be available in all documents.

</td></tr>
<tr><td>order</td><td>
  
The sort order in the `add-block` section, or the sort order of the containers (tabs). This parameter does NOT affect the sorting of the blocks themselves!
  
</td></tr>
<tr>
<td>templates</td>
<td>
  
An associative array containing the template for the `owner` key, as well as templates for each field group.

For a description of template creation methods, see below.

</td>
</tr>
<tr><td>icon</td><td>
  
The icon class that will be displayed in the `add-block` section, if the plugin setting &addType is set to `icons`
  
For example, if you set the class `fa fa-cogs`, the output will be as following:
```html
<i class="fa fa-cogs"></i>
```

</td></tr>
<tr><td>image</td><td>
  
The image that will be displayed in the `add-block` section, if the plugin setting `&addType` is set to `images`.
  
The image will be processed with the `phpthumb` snippet with the parameter `w=80`

</td></tr>
<tr><td>prepare</td><td>The name of a snippet or function that will be called before displaying data. For example:

```php
'prepare' => function(&$options, &$values) {
  ...
},
```

The parameters for the function and the snippet is the same: `options` - container options, `values` - values of fields.</td></tr>
</table>
