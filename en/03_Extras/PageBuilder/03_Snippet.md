To display the blocks, use the PageBuilder snippet with the following parameters:
<table>
<tr><th>Parameter</th><th>Default value</th><th>Possible values</th></tr>
<tr><td>docid</td><td>Current document</td><td>Identifier of any existing document, an integer</td></tr>
<tr><td>container</td><td>default</td><td>Name of the container</td></tr>
<tr><td>blocks</td><td>*</td><td>

The list of blocks is separated by commas, without spaces. The name of the configuration file is taken without the extension (For example, `all_fields, groups`). If you specify `*`, the filter by name will not be applied

</td></tr>
<tr><td>wrapTpl</td><td>[+wrap+]</td><td>The name of the chunk containing the wrapper template for the list of blocks of the output container</td></tr>
<tr><td>templates</td><td></td><td>The identifier of the template group to be used for output. It must be defined in the configuration of each output block</td></tr>
<tr><td>offset</td><td>0</td><td>Number of skipped blocks from the beginning of the output</td></tr>
<tr><td>limit</td><td>0</td><td>The number of blocks for output, or 0 for all</td></tr>
<tr><td>renderTo</td><td>templates</td><td>
  
Output type: `templates` - through templates, `array` - as array, `json` - as json.

</td></tr>
<tr><td>giveTo</td><td></td><td>If the parameter is set, the result data will be transferred to the snippet specified in this parameter, and then the result of this snippet will be showed</td></tr>
</table>
