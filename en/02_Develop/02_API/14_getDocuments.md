###Возвращает информацию для указанных документов, с учетом дополнительных настроек. По умолчанию возвращаются опубликованные документы, которые не удалены

array getDocument(array $ids[, int $published[, int $deleted[, string $fields[, string $where[, string $sort[, string $dir[, string $limit]]]);

**$ids** - массив идентификаторов документов

**$published** - опубликован ли документ
0 - документ не опубликован
1 - документ опубликован
По умолчанию: 1

**$deleted** - значение удаления документа
0 - документы не удалены
1 - документы удалены (в корзине)
По умолчанию: 0

**$fields** - список необходимых полей
по умолчанию: все поля

**$where** - дополнительные условия запроса в БД (соответствует where в MySQL)

**$sort** - поле, по которому будет производиться сортировка
по умолчанию: menuindex

**$dir** - вариант сортировки:
ASC - по возрастанию
DESC - по убыванию
по умолчанию: ASC

**$limit** - максимальное количество документов (соответствует like в MySQL)
по умолчанию: без ограничения

***

####Формат данных результата:

	Array ( 
		[0] => Array ( 
			[id] => 16 
			[type] => document 
			[contentType] => text/html 
			[pagetitle] => Ajax1 
			[longtitle] => Ajax and Web 2.0 ready 
			[description] =>  
			[alias] =>  
			[link_attributes] =>  
			[published] => 1 
			[pub_date] => 1159264800 
			[unpub_date] => 0 
			[parent] => 15 
			[isfolder] => 1 
			[introtext] =>  
			[content] => Содержимое документа 
			[richtext] => 1 
			[template] => 4 
			[menuindex] => 1 
			[searchable] => 1 
			[cacheable] => 1 
			[createdby] => 1 
			[createdon] => 1144904400 
			[editedby] => 1 
			[editedon] => 1219426098 
			[deleted] => 0 
			[deletedon] => 0 
			[deletedby] => 0 
			[publishedon] => 0 
			[publishedby] => 0 
			[menutitle] =>  
			[donthit] => 0 
			[haskeywords] => 0 
			[hasmetatags] => 0 
			[privateweb] => 0 
			[privatemgr] => 0 
			[content_dispo] => 0 
			[hidemenu] => 0 
			[alias_visible] => 1 
		) 
	)

***

####Пример


	/**Структура документов:
	-Статьи (1)
	--Недвижимость (11)
	---Эконом(111)
	---Элитная(112)
	--Авто (12)
	**/
	
	$txt = $modx->getDocuments(array(11,111)); //вернет информацию о документах 11 и 111
