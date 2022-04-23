Caching for a document can be enabled using the "Cached" option on the "Page Setup" tab.

If you enable document caching, this means that the document and its contents will only run the first time the document is requested. Then the results of the work are "saved" in the cache and retrieved from there for any subsequent requests.

** This can speed up page loading because snippets won't be executed on every request. **

If you clear the site's cache by clicking "Clear Cache" in the admin interface, you'll see new content because the page will be parsed again.

## Snippet caching ##
Snipets, if you call them using the [[Snippet]] construct, will be cached.

You can make the snippet work every time the page loads, even if the document itself is cached, by calling: (Note that the parentheses are replaced with exclamation points) Such a snippet will be executed each time the page is visited.[!Snippet!]

As a rule, on sites with low traffic, all snippets are launched uncachable. But if you want to optimize your site, you can call snippets whose data rarely changes in cached mode. This will speed up the site.

## Caching and development ##
When you design a site, it is best to disable caching in the system configuration. This can help you, as data changes frequently during the development process and you should always see the latest version of how snippets and documents work.

Then, once your site is up and running, you can set some snippets to cache mode.
