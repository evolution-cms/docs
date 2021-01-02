### Возвращает результат выполнения сниппета с заданными параметрами

```string runSnippet(string $snippetName [, array $params][, int $cacheTime][, string $cacheKey]);```

**$snippetName** - название сниппета (чувствительно к регистру!)

**$params** - массив со значениями параметров

**$cacheTime** - время кэширования в секундах. Если указано 0, то хранение до полного сброса кэша **Доступно только в 2.x**

**$cacheKey** - ключ для кэширования. Используется только в связке с cacheTime, если не указать, то будет сформирован на основании `$_GET` и `$params массивов` **Доступно только в 2.x**

***

#### Пример
```
$txt = $modx->runSnippet('Ditto', array(
	'startID' => 2, 
	'summarize' => 2, 
	'removeChunk' => 'Comments', 
	'tpl' => 'ditto_blog', 
	'paginate' => 1, 
	'extenders' => 'summary,dateFilter', 
	'paginateAlwaysShowLinks' => 1, 
	'tagData' => 'documentTags' 
));
```

Вернет результат работы сниппета Ditto, который идентичен вызову:

```[[Ditto? &startID=`2` &summarize=`2` &removeChunk=`Comments` &tpl=`ditto_blog` &paginate=`1` &extenders=`summary,dateFilter` &paginateAlwaysShowLinks=`1` &tagData=`documentTags`]]```

#### Коментарий
**$cacheTime** и **$cacheKey** - актуально для использования в шаблонах BLADE. Так как по умолчанию у нас все сниппеты не кешированные и нет `[[ ]]` и `[! !]` вариантов выполнения сниппетов, так же это дает возможность кешировать снипет не навсегда до сброса кеша как было раньше, а на какой то определенный период времени + самому завадавать cacheKey, что даст возможность кешировать один и тот же снипет для многих страниц сразу.
