###Повертає інформацію для зазначених документів, з урахуванням додаткових налаштувань. За замовчуванням повертаються опубліковані документи, що не видалені

array getDocument(array $ids[, int $published[, int $deleted[, string $fields[, string $where[, string $sort[, string $dir[, string $limit]]]);

**$ids** - масив ідентифікаторів документів

**$published** - чи опублікований документ
0 - документ не опублікований
1 - документ опублікований
За замовчуванням: 1

**$deleted** - значення видалення документа
0 - документи не видалені
1 - документи вилучені (в кошику)
За замовчуванням: 0

**$fields** - список необхідних полів
за замовчуванням: всі поля

**$where** - додаткові умови запиту в БД (відповідає where в MySQL)

**$sort** - поле, по якому буде проводитися сортування
за замовчуванням: menuindex

**$dir** - варіант сортування:
ASC - по зростанню
DESC - по спадаючій
за замовчуванням: ASC

**$limit** - максимальна кількість документів (відповідає like в MySQL)
за замовчуванням: без обмеження

***

####Формат даних результату:

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
			[content] => Вміст документу 
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

####Приклад


	/ ** Структура документів:
	-Статті (1)
	--Нерухомість (11)
	--- Економ (111)
	--- Елітна (112)
	--Авто (12)
	**/
	
	$txt = $modx->getDocuments(array(11,111)); //поверне інформацію про документи 11 та 111
