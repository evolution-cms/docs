###Getting the child documents of a document with the values of the requested document fields and TVs; the TVs are returned with their widgets applied.

*Note: when no fields are requested, the method returns an empty array.*

*Performance: the method runs separate queries for every child document (N+1). For listings that show a few TVs per document (cards, product prices), use [getTemplateVarValues](69_getTemplateVarValues.md) - it reads the named TVs of all documents in one query.*

array getDocumentChildrenTVarOutput(int $parentid, array $tvidnames[, int $published[, string $docsort[, string $docsortdir[, string $where[, string $resultKey]]]]]);

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

**$where** - additional SQL WHERE condition (document fields only, not TVs)
Default: empty string

**$resultKey** - field whose values become the keys of the result array
false - the result array keys are numbered in order
Default: id

***

####Result format:

	Array ( 
		[16] => Array ( 
			[MyParameter] => This is my text 
			[id] => 16 
			[type] => document 
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
	
	$txt = evo()->getDocumentChildrenTVarOutput(11, array('id', 'type', 'MyParameter'));
	
	//returns the document fields id, type 
	//and the TV MyParameter 
	//of documents 111 and 112.
