In the context to Template Variables, a Data Source is the location of the information to be displayed. A Data source can come from any of the following sources:

*an externally generated file that is sent via FTP to the server
*a Database table accessible to Evo
*a Document in the document tree
*a Chunk in the Admin Interface
*the result of an evaluated PHP script

These Data Sources can be tied (or "bound") to a Template Variable for formatting and displaying in document. In addition, the bound data in the TVs can be almost effortlessly formatted via the Display Controls within the TV system for some truly stunning results. The format for using the five types of data source bindings available to all template variables follows:
```
@FILE file_path
@DOCUMENT document_id
@CHUNK chunk_name
@SELECT sql_query
@EVAL php_code
@DIRECTORY _path_to_folder

```
These five "@" commands or bindings will allow you to quickly and easily attach your template variables to virtually any database system available.

The value returned from the data source can either be a string value (including numbers, dates, etc), an array or a recordset. The value returned is dependent on the type of binding used. Some display controls will attempt to either convert the returned value into a string or an array.

For example, controls that accept string values such as a radio button group or select list will attempt to convert a record set (rows and columns) into the following format:

```
col1row1Value==col2row1Value||col1row2Value==col2row2Value,…
```
Please note that @ bindings will work only when used inside "Input Option Values" or "Default Value" fields (indicated by the database icon next to them).



When placing @ bindings inside the "Input Option Values" field, they are used to format input options only when editing document within the Admin Interface, for example to create a drop-down list of Cities or Countries.

When placing @ bindings inside the "Default Value" field the returned value is used to render to the final web page. This makes it simple to build complex forms for data input on the web very quickly.