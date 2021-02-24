## Data output

Data are sanitized, arrays are converted to strings to be output in templates. Special placeholders are set for form controls. "Field name" below is the raw field name, without brackets for array fields.

Raw field value (or placeholder):
```
[+field name+]
[+placeholder.name+]
```

Sanitized field value (array fields are converted to strings): 
```
[+field name.value+]
```
Example:
```
[+comment.value+] //The value of a field named "comment". It may be a scalar value of the real input or textarea or any other form element, but it can be set with PHP as well. 
```

Setting checkbox: 
```
[+c.field name.field value+]
```
Example:
```
[+c.agree.Yes+] //It outputs "checked" if a single checkbox named "agree" contains "Yes" value.
[+c.district.West+] //Same but for one checkbox from an array of two checkboxes named "district[]"
[+c.district.East+] //Same but for one checkbox from an array of two checkboxes named "district[]"
```


Setting select or radio-button: 
```
[+s.field name.field value+]
```
Example:
```
[+s.country.Russia+] //It outputs "selected" if a single option of select named "country" is selected and its value is "Russia". See example for checkboxes if you need to use select with multiple options available to choose.
```

Class for empty required field:
```
[+field name.requiredСlass+]
```

Class for wrong filled field:
```
[+field name.errorClass+]
```

Alternative classes output:
```
[+field name.class+] outputs class="classname"
[+field name.classname+] outputs "classname"
```

Validation error message:
[+field name.error+]

Controller messages output:
[+form.messages+]

There are 3 possible types of messages in the [+form.messages+] placeholder: failed the "required" rule fields, wrong filled fields, any messages set by addMessage() method. The last ones are output by default, see the "messagesTpl" parameter description.

Lexicon entries:
[%lexicon keys%]

If any template engine (EvoTwig, EvoBlade) is used then template variables are available: 
* FormLister (controller object);
* errors (formData['errors'] array);
* messages (formData['messages'] array;
* data (formData['fields'] array);
* plh (placeholders set with setPlaceholder()) method as well as prerendered error messages if "prerenderErrors" parameter is on).

Post procession of MODX parser construction is disabled when template engine is used.
