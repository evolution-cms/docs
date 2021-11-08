YAMS Language Dependent Layout
==============================

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

### How can I have a different layout for each language?

The answer is to use a different document template for each language and to get YAMS to choose the correct one based on the language:

1.  Place the document template for each language within a separate chunk. Give the chunks the names "mytemplate\_id1", "mytemplate\_id2", etc. where "id1", "id2" are the language group ids for the active languages.

2.  In the document template, use the following snippet call:


    [[YAMS? &get=`chunk` &from=`mytemplate`]]
