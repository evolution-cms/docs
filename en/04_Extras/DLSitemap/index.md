## Overview
DLSitemap is a snippet to build XML site map for search engines and robots. It's much faster than [sitemap](https://github.com/extras-evolution/sitemap/) and can define priority and change frequency by the time of the last document modification.

The snippet itself is a wrapper for DocLister to run it with predefined parameters (see `assets/snippets/DocLister/config/core/sitemap.json`), so you can use all [DocLister parameters](http://docs.evo.im/en/04_extras/doclister.html) to filter docs, change order and so on. But `prepare` parameter is filled with DLSitemap, so use `BeforePrepare` and `AfterPrepare` parameters instead of it.

If you want to control priority and change frequency manually, then you have to create TV-parameters named `sitemap_priority` and `sitemap_changefreq` (these names can be changed with `priority` и `changefreq` parameters). If document has no these TV-parameters, then priority and change frequency are defined automatically.
