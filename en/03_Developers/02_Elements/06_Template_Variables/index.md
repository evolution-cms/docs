TV parameter in MODx is an element (field) that contains certain information for the current page.

TV parameters allow you to add additional information to the document, which can then be used along with the main parameters. They have different types and depending on this, their behavior and appearance change. The parameter value can be displayed on the page or passed to a snippet for further processing.

#### What is the TV parameter for?
For orderly and logical storage of information on the site. Let's say there are 2 types of materials on the site - products and news. For a product, you can create parameters, in one of which the price will be stored, and in the other a photo. And for news, tags and a story.

Often, TV parameters are used to create SEO fields like meta description, keywords, etc. Parameters are tied to templates, and this allows you to set completely different fields depending on the type of material.

### Example parameter:
[\*pagetitle\*] - call a parameter in the template that will return the page title. It is most commonly used to output title:
```
<head>
<title>[*pagetitle*]</title>
</head>
```
All parameters can be divided into basic, system and user.

### Main parameters:
The list of basic parameters is predefined in the cms and contains basic information about the document. Most of them can be seen when creating and editing any document.

The most used are:
- **[\*pagetitle\*]** - document title
- **[\*longtitle\*]** - extended document title
- **[\*description\*]** - description of the document
- **[\*introtext\*]** - document annotation
- **[\*content\*]** - document content
- **[\*id\*]** - document identifier (number)
- **[\*parent\*]** - number (ID) of the parent document
- **[\*pub_date\*]** - date of publication of the documentary
- **[\*unpub_date\*]** - date of completion of publication
- **[\*createdby\*]** - Id of the user who created the document
- **[\*createdon\*]** - Document creation date
- **[\~identifier\~]** - URL of the document by the specified identifier
It is worth mentioning separately that the parameters can be combined. This is especially true for creating links to different documents using the **[\~identifier\~]** parameter. You can also set a parameter as an identifier.

**[\~[\*id\*]\~]** -Display a link to the current document.

**[\~[\*parent\*]\~]** - Display a link to the parent of the current document.

#### Additional
- **[\*alias\*]** - document alias
- **[\*editedby\*]** - id of the user who edited the document
- **[\*editedon\*]** - date of document editing
- **[\*type\*]** - resource type (document, folder or link)
- **[\*contentType\*]** - content type (e.g. text/html)
- **[\*published\*]** - is the document published (1|0)
- **[\*isfolder\*]** - whether the document is a folder (1|0)
- **[\*richtext\*]** - whether the visual editor is used when editing the document
- **[\*template\*]** - number (ID) of the template used for the document
- **[\*menuindex\*]** - serial number of the display in the menu
- **[\*searchable\*]** - is the document searchable (1|0)
- **[\*cacheable\*]** - Is the document cached? (1|0)
- **[\*deleted\*]** - document deleted (1|0)
- **[\*deletedby\*]** - id of the user who deleted the document
- **[\*menutitle\*]** - menu title.
- **[\*donthit\*]** - Tracking the number of visits is disabled (1|0)
- **[\*haskeywords\*]** - The document contains keywords (1|0)
- **[\*hasmetatags\*]** - The document has meta tags (1|0)
- **[\*privateweb\*]** - The document is part of a private group of user documents (1|0)
- **[\*privatemgr\*]** - The document is part of a private group of management documents (1|0)
- **[\*content_dispo\*]** - Content delivery option (1 - to display | 0 - to download)
- **[\*hidemenu\*]** - The document does not appear in the menu (1|0)
- **[\*alias_visible\*]** - Is the document involved in URL generation(1|0)

### System Parameters
Settings that display system data

- **[^qt^]** - time to query the database
- **[^q^]** - database queries
- **[^p^]** - time for PHP scripts to run
- **[^t^]** - total time to generate the page
- **[^s^]** - content source (database or cache)
- **[^m^]** - amount of memory consumed

#### Example:
```
Memory : [^m^], 
MySQL: [^qt^], [^q^] request(s), 
PHP: [^p^], 
Total time: [^t^], 
Document from [^s^]. 
```

### Custom TV Settings
Custom parameters are created manually by the programmer, based on the experience and structure of the site.

#### Create and edit a TV setting
To create a parameter, click on the link "Items - Settings (TV)" and select "New parameter (TV)".

(Picture should be here!)

#### Assign fields
- **Parameter name** - used to call the TV parameter. You can use both English and Russian, as well as a hyphen and an underscore. You can't use a space!
- **Title** - used to name the TV parameter in the document when editing.
- **Description** - used for more advanced information about the parameter in the document when editing, as well as in the general list of TV parameters.
- **Input type** - defines the type of information received. Depending on the selected type, the interface changes. For more information, see "Input Types".
- **Default value** - Specifies the default value of the TV parameter when editing a document.
- **Possible values** - used in some types of input (for example, Radio Options, Check Box) to provide choices. For more details, see Determining TV Parameter Values.
- **Visual component** - determines the option of displaying the TV-parameter on the page of the site. For more details, see TV Parameter View.
- **Order in the list** - determines the order of the TV parameter in the document.
- **"Lock" in the parameter name** - if you enable the checkbox, then no one except administrators will be able to edit this TV-parameter.

#### Input Types
-**Text** - input field. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**Raw Text, Raw Textarea** - outdated and not recommended for use. Instead, we recommend using Textarea and Textarea (Mini).

-**Textarea and Textarea (Mini)** - text field. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**RichText** - a field with a visual editor. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**DropDown List Menu** - drop-down list. The Possible Values field specifies a list of values and is defined in a special format. For more details, see Determining TV Parameter Values. The default value determines the selected item when you first edit it.

-**Listbox (Single-Select) and Listbox (Multi-Select)** - a list of multiple selections. Single-Select and Multi-Select differ only in that in the first option you can select one value, and in the second several (using Ctrl). The Possible Values field specifies the final list of values and is defined in a special format. For more details, see Determining TV Parameter Values. The default value determines the selected item when you first edit it.

-**Radio Options** - switches. The Possible Values field specifies a finite list of values and is defined in a special format. For more details, see Determining TV Parameter Values. The default value determines the selected item when you first edit it.

-**Check Box** - checkboxes. The Possible Values field specifies a finite list of values and is defined in a special format. For more details, see Determining TV Parameter Values. The default value determines the selected item when you first edit it.

-**Image** - image. When you click the "Insert" button, a file manager opens, which allows you to select the desired image and upload it. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**File** - file. When you click the "Insert" button, a file manager opens, which allows you to select the necessary file and download it. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**URL** - link. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**Email** - e-mail. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**Number** - number. The possible values are not used. The default value is automatically written to the field the first time you edit it.

-**Date** - date. The first button invokes a calendar that you can use to select a date. The second button erases the date. The possible values are not used. The default value is automatically written to the field the first time you edit it.

#### Determining TV Parameter Values
The Possible Values setting defines options for parameters such as DropDown List Menu, Listbox, Check Box, and Radio Options.

The format for determining the values is as follows:
```
parameter1==value1|| parameter2==value2|| parameter3==value3
```
The separator "==" is used to separate the displayed and actual value, and the separator "||" separates the values from each other.

If the actual and displayed values match, you can use a simplified version of the record:
```
value1|| value2|| value3
```
#### Example
Input Type: DropDown List Menu Possible values:
```
Red==#FF0000|| Green==#00FF00|| Blue==#0000FF
```
When the user edits the document, he will see a drop-down list with the values "Red, Green, Blue". When you select a value and save the document to the database, one of the values will be saved - #FF0000, #00FF00 or #0000FF.
