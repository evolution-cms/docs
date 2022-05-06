Allows you to display only those documents whose specific field begins with the desired letter. Let's say that from the documents with ID 2,4,23,3 we will show only those whose longtitle (the extended title begins with the letter "H" regardless of the case)

### Options
* fromget – Whether to take data from GET
* frompost – Whether to take data from POST
* char – Which character should the text begin with?
* field – Default field to filter by:c.pagetitle
* setActive - Activate character sets, default:0
* regexpSep - Separator in regular sets, default:||
* regexp - Sets of supported regulars, default:a-z|| 0-9|| a-z
* loadfilter - Which filter to load, default:empty
* register – Case sensitivity, default:0

### Example of a call
```
[[DLglossary? 
&documents=`2,4,23,3` 
&idType=`documents`  
&field=`c.longtitle`
&char=`н`
&register=`1`
]]
```
