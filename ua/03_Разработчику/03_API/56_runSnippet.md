### Повернення результату виконання сніпета з заданими параметрами

string runSnippet(string $snippetName [, array $params, int $cacheTime, string $cacheKey]);

**$snippetName** - назва сніпета (чутливість до регістру).

**$params** - масив зі значеннями параметрів.

**$cacheTime** - час кешування в секундах. Збереження до повного очищення кеша при вказаному 0.  **Доступно тільки в 2.0**

**$cacheKey** - ключ кешування. Якщо не вказати час кешування, ключ буде сформованим з використанням $_GET та $params масивів. **Доступно тільки в 2.0**

***

#### Приклад.

	$txt = $modx->runSnippet('Ditto', 	array( 'startID' => 2, 
					'summarize' => 2, 
					'removeChunk' => 'Comments', 
					'tpl' => 'ditto_blog', 
					'paginate' => 1, 
					'extenders' => 'summary,dateFilter', 
					'paginateAlwaysShowLinks' => 1, 
					'tagData' => 'documentTags' 
					));

	//Поверне результат роботи сніпета Ditto, що ідентичний виклику:
	[[Ditto? &startID=`2` &summarize=`2` &removeChunk=`Comments` &tpl=`ditto_blog` &paginate=`1` &extenders=`summary,dateFilter` &paginateAlwaysShowLinks=`1` &tagData=`documentTags`]]
