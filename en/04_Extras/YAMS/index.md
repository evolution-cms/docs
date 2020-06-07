YAMS
=====

Author : [PMS](https://github.com/Deesen/)

**Licence:** GPL v3

**YAMS** is a highly configurable Evo addon that is designed to make it easy to develop multilingual websites.

PHP version not below 5.6

[Github](https://github.com/Deesen/YAMS)

The following features are currently implemented:

*   All content is managed via a single document tree to enable a consistent site structure across all language variants.

*   Standard Evo placeholders can be used within document templates in order to generate multilingual content and URLs.

*   A tabbed language layout for multilingual documents (requires ManagerManager)

*   Document templates can be configured as multilingual or monolingual.

*   Highly configurable multilingual URLs. The following are examples of different ways YAMS could be set-up to refer to language variants of a single document:

**Multilingual aliases:**  
http://sitename/my-doc-en.html  
http://sitename/mon-doc-fr.html

**Server name mode only:**  
http://en.sitename.com/mydoc.html  
http://fr.sitename.com/mydoc.html

**Root name mode only:**  
http://sitename.com/en/mydoc.html  
http://sitename.com/fr/mydoc.html

**Root name mode only, with one language at root:**  
http://sitename.com/mydoc.html  
http://sitename.com/fr/mydoc.html

**Server name mode, root name mode, friendly alias paths, multilingual aliases and multibyte URLs:**  
http://en.sitename.com/england/folder/mydoc.html  
http://fr.sitename.com/la-france/répertoire/mon-doc.html

*   Additional URL configurability, including ability to hide alias of site start document, SEO friendly redirection, multibyte URLs and content-type dependent alias suffixes.

*   Additional YAMS Placeholders allowing access to language specific settings, such as language name and direction.

*   Additional functionality via the YAMS snippet call, including the ability to manage custom multilingual chunks, snippets and template variables to generate list-based or drop-down based language switchers (templatable), the ability to repeat content in multiple languages…

*   Extensions for Ditto, Wayfinder, Jot and eForm.

*   Possible to create custom multilingual template variables.
