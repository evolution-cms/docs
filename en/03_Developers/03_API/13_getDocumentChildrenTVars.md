####Getting the child documents of a document with the values of the requested document fields and TVs

*Note: when no fields are requested, the method returns an empty array.*

*Performance: the method runs separate queries for every child document (N+1). For listings that show a few TVs per document
(cards, product prices), use [getTemplateVarValues](69_getTemplateVarValues.md) - it reads the named TVs of all documents in one query.*

array getDocumentChildrenTVars(int $parentid, array $tvidnames[, int $published[, string $docsort[, string $docsortdir[,string $tvfields[, string $tvsort[, string $tvsortdir]]]]]]);

**$parentid** - id of the parent document

**$tvidnames** - array of the requested fields and TVs

**$published** - document publication status
0 - unpublished documents
1 - published documents
Default: 1

**$docsort** - field the documents are sorted by
Default: menuindex

**$docsortdir** - sort direction of the documents
ASC - ascending
DESC - descending
Default: ASC

**$tvfields** - columns to return for every TV
Comma-separated list of columns
* - all columns
Default: *

**$tvsort** - field the TVs are sorted by
Default: rank

**$tvsortdir** - sort direction of the TVs
ASC - ascending
DESC - descending
Default: ASC

***

####Result format:

	Array ( 
		[0] => Array ( 
			[0] => Array ( 
				[id] => 4 
				[type] => text 
				[name] => MyParameter 
				[caption] => Caption 
				[description] => Description 
				[editor_type] => 0 
				[category] => 0 
				[locked] => 0 
				[elements] => Text 
				[rank] => 0 
				[display] =>  
				[display_params] =>  
				[default_text] =>  
				[value] => This is my text 
			) 
			[1] => Array ( 
				[name] => id 
				[value] => 16 
			) 
			[2] => Array ( 
				[name] => type 
				[value] => document 
			) 
		) ... 
	)

***

####Example

	/**Document tree:
	-Articles (1)
	--Real estate (11)
	---Budget (111)
	---Premium (112)
	--Cars (12)
	**/
	
	$txt = evo()->getDocumentChildrenTVars(11, array('id', 'type', 'MyParameter'));
	//returns the document fields id, type and the TV 
	//MyParameter of documents 111 and 112.
