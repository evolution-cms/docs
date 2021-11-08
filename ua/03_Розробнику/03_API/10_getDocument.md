###Отримання інформації про документ, з врахуванням додаткових налаштувань

array getDocument(int $id[, string $fields[, int $published[, int $deleted]]]);

**$id** -идентифікатор документу

**$fields** - список необхідних полів
за замовчуванням: всі поля

**$published** - чи опубліковано документ
0 - документ не опубліковано
1 - документ опубліковано
За замовчуванням: 1

**$deleted** - значення видалення документа
0 - документи не видалені
1 - документи видалені (в кошику)
За замовчуванням: 0

***

####Формат даних результату:

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

####Приклад:

````php
/**Структура документів:

-Статті (1)
--Нерухомість (11)
---Економ(111)
---Елітна(112)
--Авто (12)

**/
$txt = $modx->getDocument(11); //поверне інформацію про документ 11
````