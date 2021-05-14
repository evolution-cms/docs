YAMS + Snippets
===============

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

How can I make other snippets work with YAMS?
---------------------------------------------

> Wayfinder, Jot, eForm, Ditto, Breadcrumbs are now deprecated with Evolution CMS 2.0. Migration to DocLister and FormLister should be considered from v1.3.6

If the snippet uses templates then it will be necessary to convert the template to display the correct language content.

This should be as simple as replacing the placeholders for the standard document variables: `[+pagetitle+], [+longtitle+], [+description+], [+introtext+], [+menutitle+] and [+content+]` by a YAMS snippet call:

    [[YAMS? &get=`data` &from=`document_variable_name` &docid=`[+id+]`]]

and including language variants for free text using a

    [[YAMS? &get=text`...

snippet call.
