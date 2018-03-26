#### The structure of the array for describing the field

<table>
<tr><th>Key</th><th>Value</th></tr>
<tr><td>caption</td><td>The name of the field that the manager sees</td></tr>
<tr><td>type</td><td>Type of field, see <a href="#field-types">below</a></td></tr>
<tr><td>theme</td><td>

The editor's topic for the `richtext` field, the available values can be viewed in the Evolution CMS configuration, on the "Interface" tab

</td></tr>
<tr><td>options</td><td>

Additional options for the `richtext` field, values can be viewed <a href="https://www.tinymce.com/docs/configure/" target="_blank">here</a>

</td></tr>
<tr><td>fields</td><td>

Nested fields, for type `group`

</td></tr>
<tr><td>height</td><td>

The height of the field, with units (for example `150px`). Available for field type `textarea`.

For `richtext` field type this option must be specified in the key `options`

</td></tr>
<tr><td>elements</td><td>

Possible values for the selection field. Available for the fields `dropdown`, `radio` and `checkbox`. Can be represented as an array of pairs `key => value`, or as a string in an cms format (`@SELECT` and others).

</td></tr>
<tr><td>layout</td><td>

Layout for the fields `radio`, `checkbox` and `group`. Possible values are `vertical` (default) and `horizontal`. Also, for `group` you can use `gallery`.

</td></tr>
<tr><td>default</td><td>

Default value. For the field type `checkbox` can be an array of values. Can be in a cms format.

</td></tr>
</table>

#### Field types

<table>
<tr><th>Value</th><th>Description</th></tr>
<tr><td>text</td><td>Text single line field</td></tr>
<tr><td>image</td><td>Text field with thumbnail and button for image selection</td></tr>
<tr><td>richtext</td><td>Text editor TinyMCE 4</td></tr>
<tr><td>textarea</td><td>Multiline text field</td></tr>
<tr><td>date</td><td>Text field with dropdown calendar</td></tr>
<tr><td>dropdown</td><td>Dropdown list</td></tr>
<tr><td>checkbox</td><td>Checkboxes, allows to multiselect</td></tr>
<tr><td>radio</td><td>Radio buttons</td></tr>
<tr><td>group</td><td>

Fields group, it is necessary to specify nested fields in the key `fields`

</td></tr>
</table>
