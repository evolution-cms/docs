## Data validation

Validator applies validation rules to field values one by one, if error occures then the record is added to form errors array and further form procession is interrupted.

Validation is passed successfully if there are no records in form errors array. 

### Validation rules
Validation rules are described as an array. Field name is the array key, and array value contains the rules array. 

Validation rule is the method of validator class. The key of rules array is the rule name (the name of validation method), its value is either error message string, or an array with rule description. 

This array contains needed values in the key named "params" and an error message in the key named "message".
Values can be taken from form fields, you should use "@params" insteadof "@params" and the value should be set as "@field":
```
"field":{
    "equals": {
        "@params" : "@foobar",
        "message": "'field' should be equal to 'foobar' field value"
    }
}
```

If several values are needed for the rule, then pass them as an array:
```
&rules=`{
    "field" : {
        "lengthBetween" : {
            "params" : [10, 20],
            "message" : "The length should be from 10 to 20"
        }
    }
}`
```

If the rule requires an array (the "in" rule and other), then you should specify this array in the following way:
```
&rules=`{
    "field" : {
        "in" : {
            "params" : [ [10,20,30] ],
            "message" : "field value should be equal to 10, 20 or 30"
        }
    }
}`
```

It needs to pass an array to validator method as single argument.

Use exclamation mark for rule denial: "!numeric" - the field passes validation if its value is not numeric.

If you need to validate only not empty fields, then set exclamation mark before field name to ignore rules if the field is empty.

```
{
    "field 1": {
        "rule 1" : "error message",
        "rule 2" : "error message"
    },
    "field 2": {
        "rule 1" : "error message",
        "rule 2" : {
            "params" : value,
            "message" : "error message"
        }
    },
    "!field 3":{
        "rule 1" : "error message"
    }
}
```
\FormLister\Validator base class has the following rules:

- required: field value is not empty;
- date: field value is a date in defined format;
- min: field value length is greater or equal to defined;
- max: field value length is less or equal to defined;
- greater: field value is greater than defined;
- less: field value is less than defined;
- between: field value is in the range (strict or loose comparison possible, loose is default);
```
"field":{
    "less": {
        "params" : [10, 20],
        "message": "'field' value should be greater or equal to 10 and less or equal to 20"
    }
},
"another_field":{
    "less": {
        "params" : [10, 20, true],
        "message": "'another_field' value should be strictly greater than 10 and strictly less than 20"
    }
}
```
- equals: field value is equals to defined;
- in: field value is in defined array;
- alpha: field value contains only letters;
- numeric: field value contains only digits;
- alphaNumeric: field value contains only letters and digits;
- slug: field value is an url slug;
- decimal: field value is a decimal number;
- phone: field value is a phone number;
- matches: field value matches regular expression;
- url: field value is an url;
- email: field value is an e-mail address;
- length: field value length is equal to defined;
- minLength: field value length is greater than defined (strict or loose comparison possible, loose is default);
- maxLength: field value length is less than defined (strict or loose comparison possible, loose is default);
- lengthBetween: field value length is in the range (strict or loose comparison possible, loose is default);
- minCount: array size is greater than defined (strict or loose comparison possible, loose is default);
- maxCount: array size is less than defined (strict or loose comparison possible, loose is default);
- countBetween: array size is in the range (strict or loose comparison possible, loose is default).

Add one more parameter having "true" value to set strict comparison in rules with the choice of strict or loose comparision available (see "between" rule example above).

It's possible to use anonymous functions or static methods of loaded classes:
```
&rules=`{
    "myfield":{
        "required":"Required field",
        "custom":{
            "function":"\\Namespace\\Classname::myCustomRule",
            "params":[10,20,30],
            "message":"Custom check failed"
        }
    }
}`
```

Validation method should accept controller object as the first argument, field value as the second argument, parameters from the "params" key of the rule description as other arguments:
```
public static function myCustomRule($fl, $value, $a, $b, $c) {
    $result = $fl->getField('field1') == $a && $fl->getField('field2') == $b && $value == $c;
    return $result;
}
```
The rule above will be passed if the field1 value is 10, the field2 value is 20, and the value of the the field which the rule is applied to is equal to 30.

Validator method returns true if the rule is passed, false or error message if not (so it's possible not to use the "message" key for custom rules).

Example contains the "сustom" rule name, but it can be any if it's not in validator class. So you can use several custom rules.

### Files validation
### fileRules
Default validator file validator (\FormLister\FileValidator) has the following rules:

- required: files are loaded successfully;
- allowed: file extension is in defined array;
- images: file extension is jpg, jpeg, gif, png, bmp;
- minSize: file size in kilobytes is greater than defined (strict or loose comparison possible, loose is default);
- maxSize: file size in kilobytes is less than defined (strict or loose comparison possible, loose is default);
- sizeBetween: file size in kilobytes is in the range (strict or loose comparison possible, loose is default);
- minCount: files count is greater than defined (strict or loose comparison possible, loose is default);
- maxCount: files count is less than defined (strict or loose comparison possible, loose is default);
- countBetween: files count is in the range (strict or loose comparison possible, loose is default);

### Validation results
Error data are stored as an array and can be obtained with getFormData('errors') method call:
```
{
    "field 1": {
        "failed rule" : "error message"
    },
    "field 2": {
        "failed rule" : "error message"
    }
}
```
This array is filled with addError(field name, rule name, error message) method. So, it's possible to affect final result adding records to this array manually. You can also call setValid(false) method to decline failed validation. 

Each field validation result can be output in template with [+field name.error+] placeholder. Total results can be output with [+form.messages+] placholder set by messagesTpl parameter. You can use the following placeholders on its part: 

- [+required+] - messages about empty required fields;
- [+errors+] - messages about wrong filled fields.

Use getErrorMessage(field name) method to get validation error messages for any field.
