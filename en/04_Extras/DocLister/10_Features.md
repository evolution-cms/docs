## Features
### Features of DocLister

Snippet for displaying information from various tables. It was originally developed as a replacement for the Ditto snippet, but in the end significantly surpassed it in capability, flexibility and performance. However, in simple cases, using DocLister is no more difficult than Ditto (many parameters are the same).

DocLister requires PHP 5.6 or higher.

## Distinctive features of the DocLister snipette:
* easy to expand;
* allows you to display data from any tables (including the Shopkeeper catalog);
* it is possible to output data in json-format;
* the possibility of arbitrary data processing before output;
* convenient debugging tools
* sorting by TV parameters with type conversion;
* filtering of documents, including by TV-parameters;
* lexicon support;
* load parameters from files.
A class for displaying information from tables according to predefined rules. If there are no rules, the data is displayed without additional processing and communication. That is, all fields and values are the same as the database.

Rules for information processing are described in controllers. Main Controller - site_content that determines the relationship of the main documents of the site_content with the data in the TV parameters

## On the basis of the DocLister class, 12 snippets have been formed:
* __DocLister__ - the main snippet for displaying information on the principle of Ditto and CatalogView snippets
* __DLcrumbs__ - for the formation of bread crumbs on the principle of the Breadcrumbs snippet
* __DLglossary__ - to filter documents by the first character in a specific field
* __DLvaluelist__ - to replace the DropDownDocs snippet
* __DLTemplate__ - to replace $modx->parseChunk()
* __DLFirstChar__ - fetch documents and groupings in blocks by the first letter
* __DLPrevNext__ - circular forward/backward navigation between adjacent documents
* __DLMenu__ - Building a Menu of Unlimited Nesting
* __DLSitemap__ - Building an xml sitemap
* __DLReflect__ - Building a list of dates
* __DLReflectFilter__ - Filter documents by date
* __DLBeforeAfter__ - Pagination of past and upcoming events taking into account the current date

### Components based on DocLister:
* __SimpleGallery__ – display the gallery on the page
* __SimpleTube__ – plugin and snippet for creating video galleries
* __SimpleFiles__ – attach files to the page
* __SimplePolls__
* __LikeDislike__ – ability to rate
* __FormLister__ - a snippet for working with forms
* __FastImageTV__
* __DLRequest__ - run snippets with parameters from get/post
* __evoSearch__
* __eFilter__
* __Selector__ - custom TV for compiling a list of documents

Author: Agel_Nash
