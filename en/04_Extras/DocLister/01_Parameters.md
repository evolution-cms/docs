## Parameters

### Parameters at a glance
| Parameter | Description | Default |
| --- | --- | --- |
| controller | Specifies the class to fetch the data | site_content |
| idType | Type of Documents | parents |
| parents | Selection of documents based on parental documents | (page_id) |
| documents | Selection of arbitrary documents | |
| ignoreEmpty | Allows you to select all the records from the table | 0 |
| display | Maximum number of documents per query | 0 | 
| queryLimit | Maximum number of documents per query | 0 |
| depth | The depth of the query using the parameter **parents** | 0 |
| offset | Number of documents to skip from the beginning | 0 |
| start | Number of documents to skipped from the beggining of the query | 0 |
| total | The maximum number of documents to display | 0 |
| addWhereList | Additional conditions for retrieving documents | |
| showParent | The exclusio of documents from which a query was made | 0 | 
| selectFields | The names of the fields to include in the selection | |
| groupBy | Group results by any field | |
| table | The name of the table query | site_content |
| idField | The name of the primary key field | id |
| parentField | The name of the field in which the idField values of the parent documents are stored | parent |
| debug | Provide debug log for snippet call | 0 |
| tvPrefix | Prefix for placeholders created from TV parameters | tv |
| tvList | List of TV parameter names that should be in the query | |
| renderTv | TV parameter names to render as per their widget settings | |
| sortType | Sort type | none |
| orderBy | A single sort string | id DESC |
| sortBy | Sorting criterion without sorting direction | |
| order | Sorting direction | DESC |
| sortDir | A synonym for **order** parameter | DESC |
| tvSortType | Rules for converting the types of TV parameter sorting | |
| tvSortWithDefault | | |
| showNoPublish | Show unpublished documents in the output | 0 |
| filters | Rules for filtering documents | |
| filer_delimiter | Filter separator for **containsOne** mode | |
| tagsData | The string that defines the source of the tags | |
| urlScheme | URL generating scheme | |
| dateSource | The document field in which the date is located. | |
| dateFormat | Formatting rules for PHP function strftime | %d.%b.%y %H:%M |
| summary | Text processing rules for the formation of a brief description | |
| introField | The name of the field for the short text source from the content Field | |
| contentField | The name of the field in which the main content of the document is stored | |
| e | Screening of field values | |
| jotcount | Adds JotX comments number to the section when using the jotcount extender | 0 |


### controller

Specifies the class to fetch the data. Base classes (located in the folder DocLister/core/controller/):

* site_content - working with EVO documents;
* shopkeeper - working with the Shopkeeper catalog;
* onetable - working with arbitrary tables;
* site_content_tags - outputs EVO documents with tag-filtering in conjunction with TagSaver plug-in.

Default value - site_content

### idType

Type of documents. Possible Values - parents, documents.

The list of documents inserted into the query will be selected from a parameter whose name coincides with the value of this parameter.

To avoid misunderstandings, it is recommended to always explicitly define this parameter. It is especially important when parents and documents parameters are used simultaneously.

Default value - parents

### parents

Selection of documents based on the list of parental documents. 

Possible values are the id values of the parent documents, separated by a comma.

The default value is the page id on which the snippet is called.

### documents

Selection of arbitrary documents.

If the parameter parents__ is used, then the documents listed in this parameter will be simply added to the result and subject to subsequent selection rules (filtering, sorting).

Possible values are document id values, separated by a comma.

### ignoreEmpty

Allows you to select all the records from the table if the documents parameter is not specified. The idType parameter in this case must be documents.

Possible values - 1 or 0.

Default - 0.

### display

Maximum number of documents per query.

Possible values are an integer that is greater than or equal to zero.

Can be overridden by parameter queryLimit value.

Default value - 0.

###queryLimit

Maximum number of documents per query.

Possible values are an integer that is greater than or equal to zero.

Default value - 0.

### depth

The depth of the query using the parameter parents.

Possible values are an integer that is greater than or equal to zero.

Default value - 0.

### offset

Number of documents to skip from the beginning of the list. Overridden when using pagination. If you want to always skip N documents, you must use the start parameter.

Possible values are an integer that is greater than or equal to zero.

Default value - 0.

### start

Number of documents skipped from the beginning of the query. Folds with an offset value that is automatically set when pagination occurs.

Possible values are an integer that is greater than or equal to zero.

Default value - 0.

### total

The maximum number of documents displayed on 1 page in the query.

Possible values are an integer that is greater than or equal to zero.

Default value - 0.

### addWhereList

Additional conditions for retrieving documents. Any string that meets the requirements of the string to be substituted in the WHERE clause of the SQL query.

Default value - empty.

### showParent

The exclusion of documents from which a query was made using the parameter parents.

Possible values:

* 0 - forced ignoring of parents in the query;
* 1 - forced parent included to the query;
* -1 - Only the parents specified in the parents parameter are ignored.

Default value - 0.

### selectFields

The names of the fields to include in the selection.

Default value - empty.

### groupBy

Group results by any field.

Default value - defined in the controller

## Query parameters for arbitrary tables (onetable controller)

### table

The name of the table for query. If the table PrimaryKey differs from id, then you must additionally specify the name of this field in the idField parameter.

Possible values - any table name without the EVO table prefix.

Default value - site_content

### idField

The name of the PrimaryKey field. The documents specified through the documents parameter will be selected by this field.

Possible values - any field name available in the table specified by the table parameter.

Default value - id

### parentField

The name of the field in which the idField values of the parent documents are stored. Used when fetching documents from the parents parameter.

Possible values - any name of the field available in the table specified by the table parameter.

Default value - parent.

## Query with TV-parameters

### tvPrefix

Prefix for placeholders created from the names of TV-parameters.

Default value - tv

### tvList

List of TV that should be in the query.

Possible values - names of TV, separated by a comma.

Default value - empty.

### renderTV 
TV-names, the value of which must be prepared for display in accordance with the installed widgets. TV parameters which are not present in the value of the tvList parameter will be ignored.

Possible values - * or a list of TV names, separated by a comma.

Default value - empty.

## Sorting

### sortType

The value "none" specifies automatic sorting by MySQL rules (usually by primary key).

Possible values:

** none - automatic sorting by MySQL rules (usually by primary key);
** doclist - output documents in the order in which they are added to the snippet via the documents parameter;
** other - sorting according to the criteria specified in the orderBy, order, and sortBy parameters.

Default value - none.

### orderBy

A single sort string (at least a collection of sortBy and sortDir parameters, but has a higher priority).

Possible values - any string that meets the rules for constructing the ORDER BY parameter in the SQL query. When sorting in the site_content controller, it is advisable to use the prefix c. for the fields of table site_content. The names of TV are indicated as is.

For sorting in random order, the value of the orderBy parameter will be "RAND()".

Default value - id DESC (or defined in the controller)

### sortBy

Sorting criterion without sorting direction.

Possible values - any string that meets the rules for constructing the ORDER BY parameter in the SQL query. The names of TV are indicated as is.

Default value - empty. The default value can be hard-coded in the controller.

### order

Sorting direction.

Possible values are ASC, DESC. The value of this parameter can be overridden by the value of the sortDir parameter.

Default value - DESC.

### sortDir

A synonym for the "order" parameter, but it has a higher priority. If "order" and "sortDir" parameters are set, the value of the sortDir parameter will be used.

Possible values - ASC, DESC. 

Default value - DESC (or defined in the controller).

## Sorting by TV

### tvSortType

Rules for converting the types of TV when sorting.

Possible values (are separated by commas in the order in which the TV names in the orderBy parameter are specified):

* DECIMAL - numbers with 2 decimal places;
* UNSIGNED - unsigned integers;
* SIGNED - integers greater than zero;
* BINARY - binary mode;
* DATETIME - date;
* TVDATETIME- outputs the string to the date according to the format used by the TV with the type of input "Date" (available only from the controllers based on site_content).

### tvSortWithDefault

Due to the engine features (TV whose values coincide with the default values are not saved in a separate table), sorting records may not be corrected if the Default value is different from the empty page.
Therefore, it is recommended to specify the TV parameters for which the Default value is forcibly specified.

## Filtering

### showNoPublish

Output of deleted or unpublished resources (used only in controllers based on site_content)

Possible values - 0/1.

Default value - 0

### filters 

Rules for filtering documents.

Possible values - The string is formed according to the rules described in DocLister::getFilters(). More details in the section "Filters".

Default value - empty.

#### Example string

```
OR(AND(filter:field:operator:value;filter2:field:operator:value);(...))
```

### filter_delimiter

The filter separator for mode containsOne.

Possible values - any string.

##Sort by tags

### tagsData

The string that defines the source of the tags.

Possible values - a line with rules separated by a colon.

Default value - empty.

To automatically substitute tags from a GET variable, you must specify the name of this variable by passing a value of type get:tag in this parameter. In this case, the tags should be substituted into $_GET['tag']. In case if static query is necessary, it is possible to replace get on static and after a colon to transfer value of the tag, for example, static:value_tag

## Additional information

### urlScheme

URL genereting scheme

Possible values are the schemes available in Evolution (relative, http, https, full).

Default value - empty (the relative)

### dateSource

The document field in which the date is located.

Possible values - name of the field in the table. If the value was a string other than createdon and the value of this field in the database is 0, then the value from createdon is taken. For example: You use a deferred publication for some documents and specify sorting by the field pub_date. So, c DocLister you will never get a situation that documents published without deferred publication will always be at the end of the list.

Default value - pub_date.

### dateFormat

Formatting rules for the PHP function strftime.

The date source is the dateSource parameter. In addition, the date offset on the server is taken into account (see the system parameter server_offset_time). Thus, you can use a personalized time substitution depending on the user's time zone.

Default value - %d.%b.%y %H:%M.

### summary

Text processing rules for the formation of a brief description. Loads the summary extender. The controller site_content has an additional rule for the processed text: by default, the content field is sent to the processing. But if the introtext field is not empty, then the text from this field will be passed in addition to the summary. Similarly, the onetable controller itself leads.

Possible values - string formed according to summary extender rules:

```
action1:parameter1,action2:parameter2A:parameter2B,action3
```

Default value - empty.

### introField

The name of the field for the short text source from the contentField. Used only if the summary extender is loaded.

Default value - empty.

### contentField    

The name of the field in which the main content of the document is stored. Used only if the summary extender is loaded.

Default value - empty.

### e

Screening of field values. Field names are available in templates via placeholders with the prefix e: [+e.pagetitle+], [+e.longtitle+].

Possible values - field names, separated by commas.

### jotcount

Adds JotX comments number to the selection when using the jotcount extender.

Possible values - 1 or 0.

Default value - 0.
