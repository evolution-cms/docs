Snippet use
=======

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

YAMS Snippet Call
-----------------

The YAMS snippet call is used for obtaining and outputting multilingual content stored in document variables, template variables, chunks, snippets or whatever in the correct language. It is also used for repeating content in multiple languages based on templates.

By selecting the list, select or selectform options the same approach is used together with a default (but overridable) set of templates to create a hyperlinked list of language versions or a drop down select box of languages to enable switching the current language.

The YAMS snippet is in fact a macro for creating special hidden language constructs that are embedded in the document template and removed before the document is served. See the YAMS [Technical Details](extras/yams/yams-technical-details) page. These allow all possible language versions of the content to be embedded in a single document.

The blocks are reorganised and optimised as much as possible before a document is cached. This helps to ensure that as little parsing as possible is required to select the correct language content once it has been retrieved from the cache.

Note that language selection occurs after a document is retrieved from the cache, so it is not possible to end up caching the wrong language content. **It is important that the YAMS snippet is run as a cacheable at all times, since this will allow pre-cache optimisation to be undertaken.**

See the [How To](extras/yams/yams-how-to/) ? page tab for examples of its use.

YAMS Snippet Parameters
-----------------------

#### 1. Parameter : &get

**Values :**
*   chunk
*   csnippet
*   usnippet
*   tv
*   placeholder

**Description :** These parameters choose from multiple language versions of a `chunk`, \[\[cacheable snippet\]\], \[!uncacheable snippet!\], \[\*template variable\*\] or \[+placeholder+\] and display the correct one depending on the current language.

Use the `&from` parameter to specify the names of the resources to choose from. The multiple language versions are assumed to have the name basename\_langId where langId is the language group id unless otherwise specified.

-----

**Values :**  text

**Description :** In this case, the `&from parameter` will accept plain text in multiple languages rather than the name of a resource. Example:

    [!YAMS? &get=`text` &from=`de::german stuff||en::english stuff`!]

-----

**Values :**  data

**Description :** This parameter is used to extract multilingual content from the document or template variables of specific documents. In this case, the &from parameter specifies the the names of the document or template variables from which the content will be extracted and `&docidspecifies` the document identifier.

This is primarily for use in the templates of snippets which don't understand multilingual variables. See the YAMS "How To" for more information. **This parameter used to be called content**. The content syntax still works, but is depracated and may be removed in a future version. So, please switch to using data.\*

-----

**Values :**  repeat

**Description :** Repeats multiple language versions of content on a page. This option works using the templates specified by the "&beforetpl", "&repeattpl", "¤ttpl" and "&aftertpl" parameters.

If a "¤ttpl" template is specified, then it is used in place of "&repeattpl" for the current document language. Otherwise, the "&repeattpl" template is repeated for all languages.

-----

**Values :**  list

**Description :** This functions in the same way as ``&get=`repeat` `` except that by default it uses the templates in "assets/modules/yams/tpl/yams/list/" to create a list of hyperlinks to the different language versions of the page.

These default templates can be overridden using the "&beforetpl", "&repeattpl", "¤ttpl" and "&aftertpl" parameters.

-----

**Values :**  selectform

**Description :** This functions in the same way as ``&get=`repeat` `` except that by default it uses the templates in "assets/modules/yams/tpl/yams/selectform/" to create a select box and form allowing users to change language.

These default templates can be overridden using the "&beforetpl", "&repeattpl", "¤ttpl" and "&aftertpl" parameters.

-----

**Values :**  select

**Description :** This functions in the same way as ``&get=`selectform` `` except that it only outputs the select box, not the form.

### 2. Parameter : &from

**Values :**  resource\_name

**Description :** This parameter enables the names of the chunks/snippets etc. in which the information lies to be specified. It has two forms: In the first, simpler form, the basename of a resource, say, resource\_name is specified.

On multilingual pages this will be replaced by a construct that includes one language variant for each active language group.

The language variants are assumed to have the name resource\_name\_id, where id is the language group id. These language variants are subject to normal Evo caching. When a request is made for the document in a given language, all incorrect language variants are stripped out, allowing the user to see only the correct language content.

    id1::resource_name1||id2::resource_name1||...

In the second, more complex form, the languages group ids and full resource names for each language are specified. Here _id1_, _id2_, …, are the language group ids, and _resource\_name1_, … are the full corresponding resource names.

When using ``&get=`text` ``, the resource name can be replaced by text to be output instead, but this text cannot itself contain a double pipe ||.

### 3. Parameter : &docid

**Values :**  A document identifier

**Description :** The document identifier of the document from which to obtain the data. This is for use with the ``&get=`data` `` parameter.

### 4. Parameter : &beforetpl

**Values :**
_a chunk name_  
@CODE:template code  
@FILE:path to template file

**Description :** Specifies a template to be placed before a repeat block.

### 5. &repeattpl

**Values :**
_a chunk name_  
@CODE:template code  
@FILE:path to template file

**Description :** Specifies a template to be repeated once for each active language. Can be overridden by the "¤ttpl" param.

### 6. Parameter : &ttpl

**Values :**
_a chunk name_  
@CODE:template code  
@FILE:path to template file

**Description :** Specifies a template to be used if it is in the same language as the current document. Overrides by the "&repeattpl".

### 7. Parameter : &aftertpl

**Values :**
_a chunk name_  
@CODE:template code  
@FILE:path to template file

**Description :** Specifies a template to be placed after a repeat block.
