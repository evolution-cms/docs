Возвращает идентификатор документа по его урл
```
string getIdFromAlias(string $alias);
```
**$alias** - псевдоним документа

### Пример
```
	$id = $modx->getIdFromAlias('folder/folder/doc.html')
	//id документа doc.html
```
