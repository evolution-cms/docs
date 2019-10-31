###Возвращает результат выполнения сниппета с заданными параметрами

string runSnippet(string $snippetName [, array $params, int $cacheTime]);

**$snippetName** - название сниппета (чувствительно к регистру!)

**$params** - массив со значениями параметров

**$cacheTime** - время кэширования в секундах. **Доступно только в 2.0**

***

####Пример

	$txt = $modx->runSnippet('Ditto', 	array( 'startID' => 2, 
					'summarize' => 2, 
					'removeChunk' => 'Comments', 
					'tpl' => 'ditto_blog', 
					'paginate' => 1, 
					'extenders' => 'summary,dateFilter', 
					'paginateAlwaysShowLinks' => 1, 
					'tagData' => 'documentTags' 
					));

	//вернет результат работы сниппета Ditto, который идентичен вызову:
	[[Ditto? &startID=`2` &summarize=`2` &removeChunk=`Comments` &tpl=`ditto_blog` &paginate=`1` &extenders=`summary,dateFilter` &paginateAlwaysShowLinks=`1` &tagData=`documentTags`]]
