When you install PageBuilder generates the following events that can be used for customization:

#### OnPBContainerRender

This event is called after rendering the edit form of the container, the result is simply added to the output.

The parameters of the event:
<table>
  <tr><td>name</td><td>The name of the container</td></tr>
  <tr><td>container</td><td>Container options</td></tr>
  <tr><td>configs</td><td>Options of the available blocks of the container</td></tr>
  <tr><td>blocks</td><td>Blocks with values</td></tr>
</table>

#### OnPBFieldRender

This event is called after rendering each field, the result is added to the output.

The parameters of the event:
<table>
  <tr><td>name</td><td>Name of the field</td></tr>
  <tr><td>field</td><td>Field options</td></tr>
  <tr><td>value</td><td>Field value</td></tr>
</table>
