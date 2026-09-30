###Reading TV values of many documents in one query

*Available since Evolution CMS 3.5.9.*

The method reads only the named template variables of the given documents in a single SQL query, however many documents there are.
Use it for listings where every item shows a few TVs: article cards, product prices and SKUs, ratings and so on.
Calling getTemplateVarOutput() for each document in a loop runs separate queries per document (N+1).

array getTemplateVarValues(array $docIds, array $tvNames[, bool $withDefaults]);

**$docIds** - array of document ids

**$tvNames** - array of TVs
array of names
array of ids (when every element is numeric)

**$withDefaults** - fall back to default values
true - an empty or missing value is returned as the TV default value (default_text)
false - an empty or missing value is returned as an empty string
Default: true

*Note: the values are raw - no widgets are applied (unlike getTemplateVarOutput) and there is no check that the TV is 
assigned to the document's template. Every requested document gets every TV that was found. When no TV is found, an empty array is returned.*

***

####Result format:

	Array (
		[111] => Array ( [price] => 19.90 [sku] => A-111 )
		[112] => Array ( [price] => 0 [sku] => )
	)

***

####Example

	/**Document tree:
	-Catalog (1)
	--Laptops (11)
	---Laptop A (111)
	---Laptop B (112)
	**/

	$goods = evo()->getDocumentChildren(11, 1, 0, 'id,pagetitle');
	$tvs = evo()->getTemplateVarValues(array_column($goods, 'id'), ['price', 'sku']);

	foreach ($goods as $good) {
		echo $good['pagetitle'] . ': ' . $tvs[$good['id']]['price'];
	}
	//the TVs of all goods are read in one query, not one query per product.

For Eloquent collections of documents, SiteContent::tvList($docs, ['price', 'sku']) runs the same query and adds a tvs key to every document.
