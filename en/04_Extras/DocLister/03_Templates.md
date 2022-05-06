## Templates

By prayer, it is assumed that the name of the chunk is passed in the parameters of the template. However, if the chunk name begins with the @ symbol, the initial word in the template name is checked against the pre-reserved template loading rules. All subsequent words are used as a parameter to the selected rule.

__@FILE__ Loading a template from an html file located in the assets/templates/ folder or subfolders

__@CHUNK__ Normal template loading from chunk

__@TPL__ __@CODE__ parameter value is used in the inline role of the template

__@DOCUMENT__ __@DOC__ Template is taken from the content field of the specified document

__@PLH__ __@PLACEHOLDER__ Template is downloaded from the MODX Global Placeholder

__@CFG__, __@CONFIG__, __@OPTIONS__ Template is taken from the global settings of the current MODX Evolution installation

It is worth noting that even if the initial character was @ and after processing all the rules the template was still empty, then an attempt is made to detect the chunk by the full name of the template

## Placeholders

DocLister Placeholders:

* table placeholder, the name of such a placeholder coincides with the name of the column in the table;
* virtual placeholder, which became available after starting the extender or some calculations inside the controller;
* a global placeholder that is accessible from outside the templates passed to the snippet (usually prefixed with dl and can be overridden using the sysKey or id parameters).

> The extender in DocLister is a helper class for any processing, has nothing to do with Ditto extenders.

### Table Placeholders

If you specify a site_content controller or any other controller that extends it, the default site_content table is used. In the case of the onetable controller, the table name is determined by the table parameter. Thus, you can get a complete list of placeholders by opening the mysql table, for example, through phpmyadmin and looking at what fields are in this table.

### Virtual Placeholder

#### Placeholders installed by the paginate extender

__[+parameter_id.pages+]__ Pagination

__[+parameter_id.totalPages+]__ Total number of pages

__[+parameter_id.isstop+]__ 1 if the current page is the last page

__[+parameter_idisstart+]__ 1 if the current page is the first

#### Placeholder installed by the jotcount extender

The extender loads if the &jotcount parameter is specified when the snippet is invoked.

__[+jotcount+]__ Number of comments from jot snippet

#### Placeholder installed by the tv extender

__[+tv.nameTIntro+]__ Tv parameter value

By default, the tv prefix is added to all TV settings, but you can get rid of it or override it with the tvPrefix parameter.

#### Placeholder installed by extender e

The extender loads if the parameter &e=comma-separated field names are specified when the snippet is invoked

__[+e.namefield+]__ The escaped value of the field.

#### Placeholder set by the extender summary

__[+summary+]__ Annotation to the page

#### Placeholder set by the user extender

The extender must be loaded manually by specifying its name in the &extender parameter. The following parameters must also be specified:

* usertype - possible values: manager, mgr, web. Determines which tables to take user data from;
* userFields - comma-separated column names in which the user id is specified, for example, createdby, publishedby.

__[+user.id.ColumnName+]__ User ID

__[+user.username.NameColumn+]__ User login

__[+user.fullname.Columnname+]__ Full username

__[+user.role.NameColumn+]__ User Role ID

__[+user.email.NameColumn+]__ e-mail

__[+user.phone.NameColumn+]__ Phone

__[+user.mobilephone.NameColumns+]__ Mobile phone

__[+user.blocked.ColumnName+]__ Lock Status

__[+user.blockeduntil.Columnname+]__ Until what UNIX-time the user will be locked

__[+user.blockedafter.NameColumn+]__ After which UNIX-time the user will be blocked

__[+user.logincount.Columnname+]__ Total number of authorizations

__[+user.lastlogin.ColumnName+]__ UNIX last authorization time

__[+user.thislogin.ColumnName+]__ UNIX time of current authorization

__[+user.failedlogincount.NameColumn+]__ Number of failed login attempts

__[+user.lastlogin.ColumnName+]__ UNIX last authorization time

__[+user.dob.NameColumn+]__ Date of birth

__[+user.gender.NameColumn+]__ Gender

__[+user.country.NameColumn+]__ Country

__[+user.state.Columnname+]__ Region

__[+user.zip.NameColumn+]__ Postal code

__[+user.fax.NameColumn+]__ Fax

__[+user.photo.NameColumn+]__ Photo

__[+user.comment.NameColumn+]__

#### Placeholder installed in site_content controllers

__[+title+]__ The name of the document for the lists. if menutitle is empty pagetitle is used

__[+iteration+]__, __[+Parameter Value sysKey.full_iteration+]__ The sequence number of an item in the list; serial number in the list taking into account pagination.

Note: for the site_content controller and for the shopkeeper controller, the placeholder __[+iteration+]__ looks like the above - __[+iteration+]__ without prefix, and for the onetable controller - as __[+ValueSysKey.iteration+]__ with a prefix. The default value of the SysKey parameter is dl, which means that for onetable this default placeholder is __[+dl.iteration+]__.

__[+url+]__ Link to the document

__[+date+]__ the date of publication of the document is formed according to the rules specified in the dateFormat parameter (by default%, %d.%b.%y %H:%M). In addition, the server_offset_time in the engine settings is taken into account.

__[+ValueThe parametersysKey.active+]__ Flag indicating that the processed document coincides and the document on which the snippet was called is the same thing (1 - if true, 0 if not)

__[+ValueSYsKey parameter.class+]__ Classes that can be automatically assigned to a document (first, last, current, odd, even)

__[+ValueThe ParametersysKey.wrap+]__ HTML code of the list prepared for display to the user (used only for the ownerTPL template)

## Options for setting placeholders

### sysKey

The prefix for system placeholders.

The possible values are any string. The output is a placeholder named __[+sysKey.placeholder+]__, where sysKey is the value of this parameter

The default value is dl

### id

The prefix for local placeholders.

The possible values are any string. If id is specified, the output is __[+id.placeholder+]__. Where id is the value passed. If the id is not specified, then a period is not put before the name of the placeholder.

The default value is empty.

## Options output to templates

### ownerTPL

A template in which the list of results is wrapped. If no matching results are found, then by default the result with the noneTPL template is also wrapped in that template. For details, refer to the description of the noneWrapOuter parameter.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

#### Example:
```
&ownerTPL=`@CODE:
<ul class="pages-list">
    [+dl.wrap+]
</ul>
`
```
### tpl

Template.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister. The value of the parameter can be changed from the prepare snippet using the $_DocLister->renderTPL property.

The default value is defined in the controller.

#### Example:
```
&tpl=`@CODE:
<li>
    <img src="[+tv.image+]" alt="[+e.pagetitle+]">
    <a href="[+url+]">[+title+] ([+id+])</a>
</li>
`
```
### tplId1, tplId2, ..., tplIdN

A template for issuing a document under the number 1, 2, etc., where the number is the iteration number starting from 1.

The default value is taken from the value of the tpl parameter.

Note: Please note, the Id in the template names should not mislead you, in fact the number is not the Id of the document, but its number in order in the output (iteration number).

### tplOdd, tplEven

Template for even/odd document formatting.

The default value is taken from the value of the tpl parameter.

### tplFirst

Template for the design of the first document in the list. The parameter is synonymous with tplId1, but takes precedence.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister. If not specified, it matches the tpl pattern.

The default value is empty.

### tplLast

Template for the last document in the list.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister. If not specified, it matches the tpl pattern.

The default value is empty.

### tplСurrent

A template for formatting the current document in the list of documents.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister. If not specified, it matches the tpl pattern.

The default value is empty.

### noneTPL

A template with a notification that nothing was detected according to the specified criteria.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

### noneWrapOuter

Wrap the noneTPL response into the ownerTPL template. The parameter is relevant only if there are no documents to build the list and the ownerTPL is set.

The possible values are 1 or 0.

The default value is 1.

## Pagination

### paginate

Data output with pagination. See placeholders set by the paginate extender.

Possible values are:

offset - pagination in the style of Ditto;
pages - pagination with shoots.
The default value is pages.

### TplFirstP

Template for inserting a "first page" link.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

### TplLastP

A template for inserting a "last page" link.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

### TplNextP

Template for inserting a "next page" link. Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: <a href="[+link+]">' . $this->DocLister->getMsg('paginate.next', 'Next') . ' ></a>
```
There are no placeholders to substitute data from the language pack yet.

### TplPrevP

Template for inserting a previous page link.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: <a href="[+link+]">< ' . $this->DocLister->getMsg('paginate.prev', 'Prev') . '</a>
```
There are no placeholders to substitute data from the language pack yet.

### TplPage

A template for inserting a page number into a paginator.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: <a href="[+link+]" class="page">[+num+]</a>
```

### TplCurrentPage

Current page design template in paginator

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: <b class="current">[+num+]</b>
```

### TplWrapPaginate

Template container for wrapping pages pagination.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: <div class="[+class+]">[+wrap+]</div>
```

### pageLimit

The number of pages displayed in the paginator.

The possible values are an integer greater than zero.

The default value is 1.

### pageAdjacents

The maximum number of pages on the left and right relative to the current page.

The possible values are an integer greater than zero.

The default value is 4.

### PaginateClass

The class for the container in which the pagination pages will be nested.

Possible values - any string generated according to the rules for substitution in HTML attributes of class tags.

The default value is paginate.

### PrevNextAlwaysShow

Always show "next page" and "previous page".

The possible values are 1 or 0.

The default value is 0.

### TplFirstI

A template for inserting a "first page" link is used in conjunction with PrevNextAlwaysShow.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

### TplLastI

A template for inserting a "last page" link is used in conjunction with PrevNextAlwaysShow.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is empty.

### TplNextI

A template for inserting an inactive "next page" link is used in conjunction with PrevNextAlwaysShow.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: [%paginate.next%] >
```

### TplPrevI

A template for inserting an inactive "previous page" link is used in conjunction with PrevNextAlwaysShow.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: < [%paginate.prev%]
```
### TplDotsPage

Shooting template.

Possible values are the name of the template specified according to the rules for specifying templates in the DocLister.

The default value is:
```
@CODE: ...
```

### noRedirect

Prevents redirects when a page that does not exist is requested.

The possible values are 0 or 1.

The default value is 0.

## Inference to placeholders

### contentPlaceholder

Set document values in personalized placeholders.

The possible values are 0, 1. If the parameter value is 1, DocLister creates placeholders of the form [+id.item[x]+]. Where x is the sequence number of the document in the list and id is the value of the id parameter (see the id parameter description).

The default value is 0

## API Mode

### api

Used to generate output in JSON format.

The possible values are 0, 1 or the list of selectable document fields.

The default value is 0.

### JSONformat

On what principle to form a JSON-response.

The possible values are old, new. In the old format, the response looks like a regular array. In the new format, the answer is wrapped in a rows section + an admixture total is added in which the total number of participants in the sample is indicated

The default value is old.
