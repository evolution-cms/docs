## Filters

The following filters are included:

* content - to filter by the fields of the table, site_content can be replaced with the addWhereList parameter;
* tv - for filtering by TV-parameters;
* tvd - to filter by TV-parameters taking into account the default values;
* private - to filter documents taking into account access rights.
* 
# filter 
## Construction 
#### Example
```
OR(AND(filter:field:operator:value;filter2:field:operator:value);(...))
```
## Operators 

### =, eq, is
Equally.

### !=, no, isnot
Not equal.
NB: By design this creates a WHERE call which will include IS NULL.  This may produce undesired results when trying to filter for empty values.
#### Example: 
AND(tv:images:!=;)
Would show all records.  Please use isnull

### isnull
empty records

### isnotnull
records containing something

### >, gt
More than.

### <, lt
Less than.

### <=, elt
Less than or equal.

### >=, egt 
Greater than or equal to.

### %, like 
Contains a string.

### like-r 
Starts with a string.

### like-l
Ends with a string.

### regexp Fetch using REGEXP regular expressions.

### against Full-text search. 
#### Example

```
[[DocLister? &filters=`AND(content:pagetitle,description,content,introtext:against:search string)`]]
```
This example assumes that the database has a FULLTEXT index on the fields pagetitle,description,content,introtext

### containsOne 
Search for any word or part of it in text using LIKE. 

#### Example:
```
[[DocLister? &filters=`AND(content:content:containsOne:when,will come,peace)`]]
```
A SQL query of the form will be built

(content LIKE '%when%' OR content LIKE '%will come%' OR content LIKE '%peace%')
That is, in the end, documents will be selected from the database in the text of which the words "when" or "will come" or "peace" are used. From the sample call, you can see that the words are separated by a comma. You can override this behavior with the filter_delimiter parameter.

### in Included in the set.

### notin Not included in the set.

#### Example of a call with filtering at a price from 0 to 300:
```
[[DocLister? &filters=`AND(tv:price:gt:0;tv:price:lt:300)`]]
```
And now it's the same, only taking into account the default values
```
[[DocLister? &filters=`AND(tvd:price:gt:0;tvd:price:lt:300)`]]
```
