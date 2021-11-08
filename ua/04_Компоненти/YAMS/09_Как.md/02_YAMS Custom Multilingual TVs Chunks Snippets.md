YAMS Custom Multilingual TVs, Chunks, Snippets
==============================================

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

### How do I make custom multilingual template variables, chunks & snippets?

Create one tv, chunk or snippet call for each language, using the following naming convention: "myresource\_langid", where "langId" is the language group id.

Include the tv, chunk or snippet call in a multilingual document like so:

    [[YAMS? &get=`type` &from=`myresource`]]

where type is either tv for a template variable, chunk for a chunk, csnippet for a cacheable snippet call, or usnippet for an uncacheable snippet call. Note that it is currently not possible to pass parameters to multilingual snippet calls.

The correct language resource will be output depending on the language being displayed.
