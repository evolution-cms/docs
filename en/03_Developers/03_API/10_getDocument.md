###Получение информации о документе, с учетом дополнительных настроек

array getDocument(int $id[, string $fields[, int $published[, int $deleted]]]);

**$id** -идентификатор документа

**$fields** - список необходимых полей
по умолчанию: все поля

**$published** - опубликован ли документ
0 - документ не опубликован
1 - документ опубликован
По умолчанию: 1

**$deleted** - значение удаления документа
0 - документы не удалены
1 - документы удалены (в корзине)
По умолчанию: 0

***

####Формат данных результата:

````php
Array ( 
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
````

***

####Пример:

````php
/**Структура документов:

-Статьи (1)
--Недвижимость (11)
---Эконом(111)
---Элитная(112)
--Авто (12)

**/
$txt = $modx->getDocument(11); //вернет информацию о документе 11
````