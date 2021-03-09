Anyone who starts to understand Evolution will come across new terms.
Here we will note small points that you can periodically spy on.

## Terminology ##

**Template** - Contains the general layout of the page with structure and design. It also defines where to display dynamic content. You can choose your own template for each document.

**Parameters (TV)** - Additional parameters that are connected to the template. Parameters can be of different types (text, link, file, date, number, etc.). For more details on types, see the following articles.

**Chunk** - Chunk is a small template that can be used both simply for displaying some content (phone on all pages), and for processing (template of the sent eForm letter, template of the directory displayed by Ditto, etc.). Thus, the kind (presentation) of information is separated from the place of processing and is easily controlled.

**Snippet** - Snippet is a code for processing information. The received information is analyzed (for example, the user's message) and the result is provided (for example, the message is sent by mail, and the user is shown a message about the result). Snippets form menus (Wayfinder), output lists of articles with pagination (Ditto), build forms (eForm). Chunks are used for withdrawal.

**Plugin** - A plugin is a code that runs when an event occurs. For example, it highlights search words (Search Highlighting) when navigating from a search page. There are many events and their consideration is worth a separate article.

## Special tags ##

Special tags are used to display dynamic data.

### Systemic ###

- [(site_name)] - site name
- [(base_url)] or [(site_url)] - site address (https://evo.im)
- [(modx_charset)] - used encoding
- [(lang_code)] - the code of the language used on the site
- [^m^] - the amount of used memory
- [^qt^] - time for database queries
- [^q^] - the number of requests to the database
- [^p^] - time spent for PHP scripts
- [^t^] - total time to generate the page
- [^s^] - content source (database or cache) 

### Standard ###

- [\*pagetitle\*] - document title
- [\*longtitle\*] - расширенный заголовок документа
- [\*description\*] - описание документа
- [\*introtext\*] - аннотация документа
- [\*content\*] - содержимое документа
- [\*alias\*] - псевдоним документа
- [\*id\*] - идентификатор (номер) документа
- [\*pub_date\*] - дата публикации дкоумента
- [\*unpub_date\*] - дата завершения публикации
- [\*createdby\*] - Идентификатор пользователя создавшего документ
- [\*createdon\*] - Дата создания документа
- [\*editedby\*] - Идентификатор пользователя редактировавшего документ
- [\*editedon\*] - Дата редактирования документа
- [~идентификатор~] - URL указанного документа

### Additional ###

- [\*type\*] - variant (document, folder or link)
- [\*contentType\*] - content type (for example, text / html)
- [\*published\*] - whether the document has been published (1 | 0)
- [\*parent\*] - number (ID) of the parent document
- [\*isfolder\*] - is the document a folder (1 | 0)
- [\*richtext\*] - whether a visual editor is used when editing a document
- [\*template\*] - number (ID) of the used template for the document
- [\*menuindex\*] - ordernumber of the display in the menu
- [\*searchable\*] - is the document searchable (1 | 0)
- [\*cacheable\*] - Whether the document is cached (1 | 0)
- [\*deleted\*] - Document deleted (1 | 0)
- [\*deletedby\*] - ID of the user who deleted the document
- [\*menutitle\*] - Menu title. If not used, then the title of the document
- [\*donthit\*] - Tracking the number of visits is disabled (1 | 0)
- [\*haskeywords\*] - The document contains keywords (1 | 0)
- [\*hasmetatags\*] - Document has metatags (1 | 0)
- [\*privateweb\*] - The document belongs to the private group of user documents (1 | 0)
- [\*privatemgr\*] - The document is included in the private group of managerial documents (1 | 0)
- [\*content_dispo\*] - Option for serving content (1 - for display | 0 - for download)
- [\*hidemenu\*] - The document is not displayed in the menu (1 | 0)

## TV parameters, snippets and chunks ##
```
[\*TVname\*] - prints the value of the parameter in the document. 
```
```
{{ChunkName}} - returns the contents of the chunk. 
```
```
[[SnippetName]] - returns the result of the snippet. 
```
You can pass additional parameters to the snippet, listing them when called. Suppose, if we want to get the id of the current document and process it in a snippet, then the call may look like this: 
```
[[snippetname?docId=`[+id+]`]]
```
[+VariableName+] - placeholder - found in chunks that are used to process the results of snippets. After processing, values are inserted instead. In the example above, you can see how we have substituted the system placeholder [+id+] in the docId parameter for the snippet, in which the id of the current document will be. You can create placeholders yourself. 

** Nuances **

There are actually two options for calling a snippet:
1. [[SnippetName]] - cached snippet call
2. [!SnippetName!] - noncacheable snippet call

**Where to use**

Everything is very harmoniously used with each other. In templates, you can use TV parameters, snippets and chunks. In chunks, you can call snippets, TV parameters and other chunks. In snippets, you can call anything at all, but through PHP. Ultimately, you will receive the final result of processing all snippets/chunks/TV parameters.

### Пример шаблона ###
```html
<!DOCTYPE html>
<html lang="[(lang_code)]">
{{head_tags}}
<body>
	[*content*]
</body>
</html>
```
where head_tags is a chunk with the following content:

```html
<head>	
	<base href="[(site_url)]" />
	<meta charset="[(modx_charset)]" />
	<title>[*pagetitle*] / [(site_name)]</title>
</head>
```
And in the field [\*content\*] will be displayed the content of the page, set from the admin panel. Everything else is based on this information.
