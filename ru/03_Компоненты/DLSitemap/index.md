## Описание
**DLSitemap** сниппет, позволяющий строить XML карту сайта для поисковиков. Он намного быстрее, чем  [sitemap](https://github.com/extras-evolution/sitemap/), и способен изменять приоритет и менять частоту обновления, основываясь на времени последней модификации документа. 

Сам сниппет это обёртка для [DocLister](http://docs.evo.im/03_extras/doclister.html), который запускается с предопределенными параметрами (находятся в `assets/snippets/DocLister/config/core/sitemap.json`), так что можно использовать все параметры [DocLister](http://docs.evo.im/03_extras/doclister.html) для фильтрации, изменения порядка и тому подобного. Так как в конфигурации параметр `prepare` уже заполнен вызовом **DLSitemap**, то вместо него используйте параметры `BeforePrepare` и `AfterPrepare`.

Если необходимо изменить приоритет и частоту обновления вручную, тогда необходимо создать ТВ-параметры с именами `sitemap_priority` и `sitemap_changefreq` (имена могут быть изменены при помощи параметров `priority` и `changefreq`). Если документ не имеет этих ТВ-параметров, то приоритет и частота обновления будут определены автоматически. 


## Overview
DLSitemap is a snippet to build XML site map for search engines and robots. It's much faster than [sitemap](https://github.com/extras-evolution/sitemap/) and can define priority and change frequency by the time of the last document modification.

The snippet itself is a wrapper for DocLister to run it with predefined parameters (see `assets/snippets/DocLister/config/core/sitemap.json`), so you can use all DocLister parameters to filter docs, change order and so on. But `prepare` parameter is filled with DLSitemap, so use `BeforePrepare` and `AfterPrepare` parameters instead of it.

If you want to control priority and change frequency manually, then you have to create TV-parameters named `sitemap_priority` and `sitemap_changefreq` (these names can be changed with `priority` и `changefreq` parameters). If document has no these TV-parameters, then priority and change frequency are defined automatically.

