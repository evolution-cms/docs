## General parameters

These parameters are processed by FormLister core class. Controllers can change parameters purposes.

## Settings
### controller
Sets the class extending \FormLister\Core to process data. 

Possible values - class name. If it has no namespace, then namespace is assumed to be \FormLister. So Form means \FormLister\Form.
Default value - Form.

### dir
Folder where controller class is located.

Default value - assets/snippets/FormLister/core/controller/

### formid
The name of the form, required parameter.

Form needs to have a hidden field named "formid" and its value has to be the same as parameter value. The form means to be sent, if there is a key named "formid" in the $_REQUEST array and its value is equal to the parameter value.

### formMethod
Determines the source of request data:
* post - $_POST array;
* get - $_GET array;
* request - $_REQUEST array;
* anonymous function or class method name - the result of its call.

Possible values - post, get, request, anonymous function or class method name. 

Default value - post.

### disableSubmit
Disables form submission, if the parameter value is set to 1.

Possible value - 1, 0.

Default value - 0.

### config
Loads parameters from json file.

Possible values - filename:folder, several values are separated by the semicolon.

#### Example
myparams:core - loads parameters from assets/snippets/FormLister/config/core/myparams.json file;
myparams - loads parameters from assets/snippets/FormLister/config/custom/myparams.json file; myparams:/assets/myfolder - loads parameters from assets/myfolder/myparams.json file.

Default value - none.

### api
The way of output.

Possible values:

- 0: html only (default);
- 1: array with form data;
- 2: array with form data and html.
- 3: pure FormLister object;

### apiFormat
Output format for mode 1 or mode 2.

Possible value - json or array.

Defaut value - json.

### debug
Enables debug mode. Debug data is sent to MODX events log.

Possible values - 0, 1.

Default value - 0.

### saveObject
Saves FormLister object to placeholder, so other snippets can use it. The object is saved only if form processing is finished successfully.

Possible values - placeholder name.

Default value - none.

### removeGpc
Restores data sanitized by MODX as it contains {{, [[ and so on. MODX tags will be sanitized in output.

Default value - 0, 1 or field names comma separated.

Default value - 0.

## Data sources
### defaultsSources
Allows to load data from external sources, to pre-fill form fields, for example. External data are loaded only before initial form output and ignored after form is sent. This behaviour can be changed with "keepDefaults" parameter.

Possible values: sources, semicolon separated. The order of loading data matches the sources order in parameter.

The source can be set as "name:key:prefix". A prefix with a dot is added to field name, if set - for example, config.site_name. If a prefix is ended with an underscore (_), then an underscore will be used instead of a dot - that allows to avoid dot to underscore conversion made by PHP (https://www.php.net/manual/en/language.variables.external.php).

Possible sources:

- array: json or php array, its values are defined by the parameter named "defaults";
- param:parameter name:prefix - the same as the "array" source but you can specify any snippet parameter, not only "defaults";
- session:array keys, comma separated:prefix - loads data from $_SESSION according to the given keys, the values can be arrays;
- plh:keys, comma separated:prefix - loads data from $modx->placeholders property according to the given keys, the values can be arrays;
- cookie:keys, comma separated:префикс - loads data from the $_COOKIE array according to the given keys, the values can be json-arrays;
- config:prefix- loads data from MODX configuration;
- MODxAPI class name:key:prefix - a key is the argument of edit() method, the class has to be loaded before snippet call;
- document:prefix - loads current document data from modResource model. It needs no key;
- user:key:prefix - load authorized user data from modUsers model. User type is provided by key value (web or mgr).

Default value - array.

### defaults
Data for the "array" source.

Possible values: json or php array.

### keepDefaults
Allows to load external data after the form is sent. If fields list is specified, then only these fields will be loaded.

Possible values: 1, 0; field names, comma separated.

Default value - 0.

### allowEmptyFields
Allows to set fields with empty values.

Possible values - 0 or 1.

Default value - 1.

## Form Controls
### formControls
The list of fields hold by form controls (selects, checkboxes, radio buttons). It needs to determine their state.

Possible values - field names, comma separated.

Default value - none.

### emptyFormControls
This parameter allows to solve the problem of unchecked checkboxes, as they are excluded from fields array during form submission: if there's no needed element in the $_REQUEST array, then it's set according to this parameter. The problem is actual mostly for MODxAPI classes usage, because MODxAPI requires to list changed fields in fromArray() method. But it's possible to use it in common forms to set the value of unchecked checkbox in templates. 

Possible values - an array:
```
&emptyFormControls=`{
    "mycheckbox" : "No",
    "published" : 0
}`
```

### fieldAliases
Allows to set field aliases. For exemplae, "foo" field has "bar" alias:
```
$FormLister->setField("foo", 10);
$FormLister->getField("bar"); //10
$FormLister->setField("bar", 20);
$FormLister->getField("foo"); //20
$FormLister->unsetField("foo");
$FormLister->getField("foo"); //Nothig
$FormLister->getField("bar"); //Nothing (but "bar" field stays untouched when function call is unsetField("foo", false)); 
```

Possible values - an array:
```
&fieldAliases=`{
    "field name":"alias",
    "field name":"alias"
}
```
Default value - none. 

## Data Processing
### prepare, prepareProcess, prepareAfterProcess
It's similar to the "prepare" parameter of DocLister. 

Snippets defined in the "prepare" parameter are run after form data loaded, "prepareProcess" - after validation is passed successfully, "prepareAfterProcess" - after form processing is finished. Controller object is available in prepare-snippets via $FormLister variable, while $data array contains the values of form fields. Additional $name variable allows to determine the parameter initiated snippet call; so you can use one snippet for all cases. Use controller methods (setField, setFields etc.) to change form data in prepare-snippets, or return data to change as an array. 

Possible values - snippet names, anonymous functions, static methods of loaded classes.

Default value - none.

## Filtering
### filterer
Class name to filter data. Is has to be loaded before snippet call.

Default value - \FormLister\Filters.

### filters
Filtering rules array.

Default value - none.

## Validation
### validator
Class name to validate data. Is has to be loaded before snippet call.

Default value - \FormLister\Validator.

### rules
Validation rules array.

Default value - none.

### fileValidator
Class name to validate files. This class has to be loaded before snippet call.

Default value - \FormLister\FileValidator

### fileRules
Files validation rules array.

Default value - none.

## Templates
### formTpl
Form template. It needs to have the required field named "formid" with the same value as "formid" parameter's one.

Possible values - template name, according to DocLister templating rules.

Default value - none.

### arraySplitter

The separator to convert arrays to strings. 

Default value - semicolon.

### {field}.arraySplitter
The separator to convert arrays to strings, but for particular {field}. Example: groups.arraySplitter - the separator for the field named "groups".

If not set, then the "arraySplitter" parameter is used.

### errorTpl
Template for validation messages.

Possible values - template name, according to DocLister templating rules.

Default value:
```
@CODE:<div class="error">[+message+]</div>
```

### requiredClass, errorClass
Class name for empty required fields and wrong filled fields.

Default value - required and error accordingly.

### {field}.requiredClass, {field}.errorClass
Allows to set classes mentioned above for particular fields.

If not set, then "requiredClass", "errorClass" parameters are used.

### messagesTpl
Template for controller messages. It outputs message groups (messages, required, error).

Possible values - template name, according to DocLister templating rules.

Default value:
```
@CODE:<div class="form-messages">[+messages+]</div>
```

### messagesOuterTpl
Wrapper template for controller message groups.

Possible values - template name, according to DocLister templating rules.

Default value -
```
@CODE: [+messages+]
```

### messagesRequiredOuterTpl
Wrapper template for the "required" message group.

Possible values - template name, according to DocLister templating rules.

Default value:
```
@CODE: [+messages+]
```

### messagesErrorOuterTpl
Wrapper template for the "error" message group.

Possible values - template name, according to DocLister templating rules.

Default value:
```
@CODE: [+messages+]
```

### messagesSplitter, messagesRequiredSplitter, messagesErrorSplitter
Messages separator in groups.

Possible values - string.

Default value:
```
<br>
```

### removeEmptyPlaceholders
Removes placeholders without values from templates.

Possible values - 0 or 1.

Default value - 1.

### parseDocumentSource
Enables MODX-parser for output post-processing.

Possible values - 0 or 1.

Default value - 0.

### rewriteUrls
Allows to parse links in templates if the "parseDocumentSource" parameter is off.

Possible values - 0 or 1.

Default value - 0.

### skipPrerender
Allows to skip some form fields processing (sanitizing values, converting arrays to strings, error messages rendering). Set to 1, if you do not use MODX templates. 

Possible values - 0 or 1.

Default value - 0.

### prerenderErrors
Allows to process form errors if "skipPrerender" parameter is on. The results are saved to placeholders.

Possible values - 0 or 1.

Default value - 0.

### templatePath, templateExtension
Sets template files folder and template files extension. These parameters are needed to use with EvoTwig plugin.

Default value - none.

## Redirect after finish
### redirectTo
Target page id to redirect if form is processed successfully. There's no redirect in api-mode, but absolute url for target page is saved in form data as "redirectTo" field.

Instead of target page id, you can specify an array with additional options:
```
&redirectTo=`{
    "page":10,
    "query":{
        "foo":"bar"
    },
    "header":"HTTP/1.1 307 Temporary Redirect"
}`
```
The "page" key is the target page id, the "query" array contains get-parameters to pass, the "header" key can be used to set redirect header.

Possible values - number or array.

Default value - none.
