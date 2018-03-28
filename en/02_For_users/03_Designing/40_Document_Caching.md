When you create a document, you can set it cacheable or not cacheable in the "Page Settings" tab. If you set the document to be cacheable it means that the document and it's content will be parsed only at the first request of the document, i.e. the snippets are run and their output becomes part of the page content.

Then the parsing results from the page are "saved" to the cache and retrieved from there on any following requests. It can speed up the page loads when every snippet on the page is not parsed on every request.

So test this: if you create a document and set it to be cacheable, then save the document and visit the page first time, it will prosess it and save to cache. Then if you go an edit the page again, and in the page settings uncheck "Empty cache" and save it, and now visit the document, it will still show the old content, because it's being retrieved from cache instead of parsing it every time.

Now if you go and clear your site cache by doing Site > Clear Cache (or Refresh Site in versions prior to 0.9.5) in the Evo admin interface and visit the page, you will see the new content, because the page is now parsed again at the first visit and saved back to cache.

Now when you have some dynamic content on the page, i.e. snippets and you call them using [[Snippet]], they will be cached. They'll run only at the first request and after that, its all coming from cache. If you change some parameters on your cached snippet call on a cached document, you might not see the changes because it's not parsed on every request.

But you can force the snippet to run on every request even if the document itself is cached by using [!Snippet!] call (note the ! chars). Then your snippet will be parsed on every visit to the page. Or you could set the whole page to be uncached at the "Page settings" tab (uncheck cacheable).

Then it doesn't matter if the snippet calls are [[cached]], because the entire document will be parsed on every request regardless.

Keep in mind that all snippets that need to process REQUEST data (i.e. POST or GET) must be running uncached or the first person to hit the page is the only one that will get dynamic results. I typically run everything uncached on low-traffic sites, but if you want to optimize your site, you could set many of your snippets (such as menu snippets or other snippets whose data changes rarely) to run cached so that your site will render faster.

And when you do add or change pages just hit "refresh site" in the admin interface to make it clear the existing cache items and reparse the document.

When you're building your site, I'd suggest to set in the system configuration that document's will not be cacheable by default. It can help you get over these things when you wonder why something doesn't work like it should.

Then after your site is starting to be done, you can set the more static pages to be cacheable, so they'll load a little bit faster. Then when you edit some of these cacheable documents, always do a site refresh. Or be sure to just use uncached snippet calls always i.e. [!snippet!] when the snippet outputs dynamic content.