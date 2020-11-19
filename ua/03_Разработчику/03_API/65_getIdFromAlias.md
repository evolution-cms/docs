### Повернення ідентифікатору документа через його URL
```
string getIdFromAlias(string $alias);
```
**$alias** - псевдонім документа.

### Приклад.
```
	$id = $modx->getIdFromAlias('folder/folder/doc.html')
	//id документа doc.html
```
