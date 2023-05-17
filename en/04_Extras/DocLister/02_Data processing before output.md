Most often, the data obtained are not displayed in pure form. For example, it is required to fulfill when displaying any conditions or treatments (displaying a preview for a picture, recalculating the price, formatting values).

The traditional way in MODX is to invoke snippets in output patterns or use modifiers (phx). This approach is often used by beginners because of its simplicity, but it increases the load on the parser and the database.

DocLister provides the ability to preprocess data using php using the prepare parameter.

The value of the prepare parameter can be:

 * snippet name
 * call a method of a preloaded class.
 * anonymous function.

You can specify multiple values for sequential processing.

## Using Snippets
The snippet processes array values $data returns an array $data or false after processing. In the latter case, the data will not be displayed, i.e. you can use prepare in this way to filter the data.

You can also use the $_DocLister and $_extDocLister objects in the snippet.

The $_DocLister object enables you to access the methods and properties of the controller. For example, you can replace the current output template:

```
$_DocLister->renderTPL = "@CODE:[+pagetitle+]";
```

The getStore and setStore methods are available in the $_extDocLister object. setStore stores, and getStore, respectively, retrieves data from memory. Once The DocLister has finished its work, the saved blocks are removed from memory.

## Using Class Methods
```
class DLprepare {
    public static function prepare(array $data = array(), DocumentParser $modx, $_DL, prepare_DL_Extender $_extDocLister) {
        return $data
    }
}
```
Parameter value in this case: DLprepare::p repare

Similarly, you can use anonymous functions.

## Examples from the Agel Nash blog
### Example 1
So, let's imagine that we have some kind of DocLister call:
```
[[DocLister? &tpl=`tplChunk` &parents=`1`]]
```
Where tplChunk is none other than:
```
<a href="[+url+]">[[if? &is=`[+longtitle+]:notempty` &then=`[+longtitle+]` &else=`[[snippet? &text=`[+pagetitle+]`]]`]]</a>
```
Inside the tplChunk chunk, there is a nested if call (let's say the one that was specified at the beginning of the topic). What do we do?

Add the &prepare= parameter to the DocLister call (you can use any other value instead of a test).test

Create a snippet named test (or the name that was specified in the prepare parameter)

In the snippet we write this code:
```
<?php
if(!empty($data['longtitle'])){
    $data['longtitle'] = $modx->runSnippet("snippet", array('text'=>$data['pagetitle']));
}
return $data;
```
Of course, you can instead of runSnippet write and:
```
$data['longtitle'] = "[[snippet? &text=`".$data['pagetitle']."`]]";
```
But once again, let's remember why this is bad: pagetitle can contain characters that the modx parser will stumble on. This can only be written if the pagetitle can contain a snippet call (but this is a very rare case + there are other ways to handle nested modx tags)! But back to our rams.

After getting rid of the embedded snippet, you can now safely get rid of the tplChunk chunk and put the template directly into the DocLister call:
```
[[DocLister? &tpl=`@CODE:<a href="[+url+]">[+longtitle+]</a>` &parents=`1`]]
```
Now you can summarize: Checking conditions with php (using the prepare snippet) avoids unnecessary calls to nested snippets (nested calls occur only when the condition is true). And yet, in my humble opinion, inline templates are very convenient, because you can clearly see both the call and the template - all in 1 place.

### Example No 2
This example will be harder to understand. But it demonstrates even more clearly the advantage of the prepare parameter.

The site has several groups of products (phones, TVs, tape recorders). Each group has its own items, which the user adds to the cart. On the checkout page, all selected items must still have a signature (to which product group they belong). In addition, each product in the cart has characteristics such as the number of goods ordered, the cost of the goods and the total cost taking into account the quantity. You also need to calculate the total TOTAL in the form of the full amount of the order.

Let's simplify this task a little by moving the ordered number of positions to the TV-parameter count. And the basket itself will be displayed by the exact listing of the ID of the documents. Therefore, the call takes the following form:
```
[!DocLister? 
  &documents=`5133, 5132, 5135, 5131, 5136` 
  &idType=`documents`
  &tpl=`ListShop` 
  &tvList=`price,count`     
  &ownerTPL=`@CODE:<table class="table table-hover params"><tr><td>Категория</td><td>Позиция</td><td>Остаток</td><td>Стоимость</td><td>Общая стоимость</td></tr>[+dl.wrap+]</table>`
!]
```
And Chunk ListShop contains the following code:
```
<tr>
  <td>[[DocInfo? &docid=`[+parent+]` &field=`pagetitle`]]</td>
  <td>[+pagetitle+]</td>
  <td>[+tv.count+] шт.</td>
  <td>[+tv.price+] руб.</td>
  <td>[[FullPrice? &price=`[+tv.price+]` &count=`[+tv.count+]`]] руб.</td>
</tr>
```
If the DocInfo snippet is familiar to everyone, then the FullPrice snippet is nothing more than a banal multiplication of two numbers:
```
<?php
$count = isset($count) ? (int)$count : 0;
$price = isset($price) ? (int)$price : 0;
return $count*$price;
?>
```
To make it clearer, this is what the resource tree looks like:

Resource tree

Let's finish off the last touch - let's calculate for how much we have all the goods in the basket. To do this, you will need to throw a small snippet, which will run again through all the documents and calculate the total amount of FullPrice. Let's call this snippet totalFullPrice (where 27 and 26 are TV parameter ID with price and quantity):
```
<?php
//Получаем те же самые данные только для упрощения работы используем json формат. в целом не важно как это происходит, главное получить тут список нужны id документов
$out = $modx->runSnippet("DocLister", array('documents'=>'5133, 5132, 5135, 5131, 5136', 'idType'=>'documents', 'idType'=>'parents', 'depth'=>2, 'api'=>'id', 'JSONformat'=>'id'));
$out = json_decode($out, true);
$id = array();
foreach($out as $item){
  $id[] = $item['id'];
}
 
$q = $modx->db->query("SELECT value,contentid,tmplvarid FROM ".$modx->getFullTableName("site_tmplvar_contentvalues")." WHERE contentid IN (".implode(",", $id).") AND tmplvarid IN (26, 27)");
$q = $modx->db->makeArray($q);
$out = array();
foreach($q as $item){
   $out[$item['contentid']][$item['tmplvarid']] = $item['value'];
}
$price = 0;
foreach($out as $id=>$data){
    $price += $data['27'] * $data['26'];
}
return $price;
?>
```
Since this is a basket, we make all calls to snippets unclassified and look at the result (I am interested in the total number of queries): 12 SQL queries to solve such a plough problem.

Now let's try to do the same thing with the prepare snippet.
```
[!DocLister? 
&documents=`5133, 5132, 5135, 5131, 5136` 
&idType=`documents`
&prepare=`total` 
&tpl=`@CODE: <tr><td>[+category+]</td><td>[+pagetitle+]</td><td>[+tv.count+] шт.</td><td>[+tv.price+] руб.</td><td>[+fullPrice+] руб.</td></tr>` 
&tvList=`price,count`   
&ownerTPL=`@CODE:<table class="table table-hover params"><tr><td>Категория</td><td>Позиция</td><td>Остаток</td><td>Стоимость</td><td>Общая стоимость</td></tr>[+dl.wrap+]</table>`!]
```
As you can see, in this case we again abandoned the chunk in favor of the inline template in which 2 incomprehensible placeholders are used - category and fullPrice. Let's take a look at the prepare snippet code to make it clearer:
```
<?php
$data['fullPrice'] = $data['tv.count'] * $data['tv.price'];
 
//[[DocInfo? &docid=`[+parent+]` &field=`pagetitle`]]
$data['category'] = $modx->runSnippet('DocInfo',array('docid'=>$data['parent'], 'field'=>'pagetitle'));
  
$key = 'totalFullPrice';
$price = $modx->getPlaceholder($key);
if(empty($price)){
    $price = 0;
}
$price += $data['fullPrice'];
$modx->setPlaceholder($key,$price);
 
return $data;
?>
```
fullPrice is nothing more than a banal multiplication of 2 numbers (price and quantities). Agree, there is no need for such a banal operation to create / call another 1 snippet, when you can make a calculation directly as they say "without departing from the cash register".

category runs the same DocInfo using runSnippet (i.e. nothing has changed).

And now the most important thing! A global totalFullPrice placement holder is being created, which can already be used outside of DocLister's chunks! If it is not present, the value is set to 0. If there is, then fullPrice is added to it. In this way, we get rid of the need to re-sample the same data just to calculate the total cost. That is, we count everything at once. Accordingly, the call [!totalFullPrice!] on the page is replaced by [+totalFullPrice+] (I have never seen such data obtained using a snippet nested in the ListShop chunk. As a rule, they are obtained using a snippet similar to totalFullPrice.)

Check the result - 9 SQL queries.

Let's summarize again: Thanks to prepare, the snippet was able to get rid of the need to re-process the same data that is needed to obtain and display some other information at any place on the same page.

### Example No 3
This example is even more complicated, but at the same time even more useful and interesting.

So, if you look carefully at the screenshot of the resource tree and the list of IDs of documents that we display, you can see that 2 documents are displayed from the TV and tape recorders sections. Thus, the parents of documents 5135, 5131 and 5136, 5132 will be the same respectively. That is, the first pair of parents will have 5638, and the second 5639. What does this give us? And this gives this - we call DocInfo as many as 2 times just like that. Imagine you received the pagetitle of document 5638 and remembered it. If you need it again, then you do not re-request it, but immediately use it.

It is for this purpose that docLister, or to be more precise, the prepare extender, has 2 methods: getStore and setStore. One stores, and the second, respectively, retrieves data from memory. Once DocLister has finished its work, the saved blocks are deleted from memory (the array is automatically cleared) and everything runs on without any glitches, as it might be if we saved the temporary data to a global array of placeholders. Moreover, with this approach and large volumes, a lot of memory would be required...

Okay, enough lyrics. Let's see how you can rewrite the prepare snippet with getStore and setStore in mind:
```
if(($data['category']=$_extDocLister->getStore('currentParents'.$data['parent'])) === null){
    //[[DocInfo? &docid=`[+parent+]` &field=`pagetitle`]]
    $data['category'] = $modx->runSnippet('DocInfo',array('docid'=>$data['parent'], 'field'=>'pagetitle'));
    $_extDocLister->setStore('currentParents'.$data['parent'], $data['category']);
}
```
I didn't copy-paste the entire source, I just quoted the modified part. But I think it's clear that we've wrapped up calling the DocInfo snippet into these 2 functions. And as a unique key, they specified currentParents[+parent+]. Thus, modx needed only 7 SQL queries to generate the same page.

Thus: the prepare snippet allows not only to process data, but also to exclude useless re-execution of code.

## Process a wrapper template
After each document is processed, DocLister attempts to apply the ownerTPL wrapper. Sometimes it is necessary to further process this wrapper and it is possible to replace it depending on various conditions (number of documents to be displayed, dates, etc.).

### Output of 3 blocks with uniform filling in 1 call
```
return $modx->runSnippet('DocLister', array(
	'ownerTPL' => '@CODE: <div class="mini-slider clearfix">
		<div id="carousel-left">[+slider.left+]</div>
		<div id="carousel-center">[+slider.center+]</div>
		<div id="carousel-right">[+slider.right+]</div>
		<a id="prev" href="#"></a>
		<a id="next" href="#"></a>
	</div>',
	'tpl' => '@CODE: <div class="sert">
		<img src="[+tv.image+]" alt="[+e.title+]" title="[+e.title+]">
	</div><!-- slide !-->',
	'tvList' => 'image',
	'prepareWrap' => function($data, $modx, $_DL, $_eDL){
		$plh = isset($data['placeholders']) && is_array($data['placeholders']) ? $data['placeholders'] : array();
		$plh['slider.left'] = $plh['slider.center'] = $plh['slider.right'] = '';
		$wrap = explode('<!-- slide !-->',
			(isset($plh['dl.wrap']) && is_scalar($plh['dl.wrap']) ? $plh['dl.wrap'] : '')
		);
		$count = count(
			isset($data['docs']) && is_array($data['docs']) ? $data['docs'] : array()
		);

		for($i = 0; $i <= $count; $i){
			$left = APIHelpers::getkey($wrap, $i++, '');
			$center = APIHelpers::getkey($wrap, $i++, '');
			$right = APIHelpers::getkey($wrap, $i++, '');

			if(empty($left) || empty($center) || empty($right)){
				break;
			}else{
				$plh['slider.left'] .= $left;
				$plh['slider.center'] .= $center;
				$plh['slider.right'] .= $right;
			}
		}
		return $plh;
	}
));
```
### Lookup data into a template wrapper for a specific level of menu
```
return $modx->runSnippet('DLBuildMenu', array(
    'idType' => 'parents',
    'parents' => 0,
    'debug' => 0,
    'maxDepth' => 2,
    'tvList' => 'dropMenu',
    'TplOneItem' => '@CODE: <li><a href="[+url+]" title="[+e.title+]">[+title+]</a></li>',
    'TplNoChildrenDepth1' => '@CODE: <li><a href="[+url+]" title="[+e.title+]">[+title+]</a></li>',
    'TplDepth1' => '@CODE: <li class="drop"><a href="[+url+]" title="[+e.title+]">&nbsp;[+title+]</a>[+dl.submenu+]</li>',
    'TplMainOwner' => '@CODE: <nav><ul>[+dl.wrap+]</ul></nav>',
    'TplSubOwner' => '@CODE: <div class="drop-block">
        <!--<i class="closed"></i>-->
        <div class="drop-content clearfix" style="[+background+]">
            <div class="cell">
                <ul>
                    [+dl.wrap+]
                </ul>
            </div>
            <div class="left">
                [+addText+]
            </div>
        </div>
    </div>',
    'AfterPrepare' => 'mainMenu::afterPrepare',
    'prepareWrap' => function($data, $modx, $_DL){
        $plh = $data['placeholders'];
        if($_DL->getCfgDef('currentDepth', 1)==2){
            $parent = current($_DL->getOneField('parent', true));
            $plh['addText'] = $modx->runSnippet('DDocInfo', array('id' => $parent, 'field' => 'dropMenuText'));
            $bg = $modx->runSnippet('DDocInfo', array('id' => $parent, 'field' => 'dropMenuImage'));
            if($bg && file_exists(MODX_BASE_PATH . $bg) && is_file(MODX_BASE_PATH . $bg)){
                $plh['background'] = 'background:url('.$bg.') right bottom no-repeat';
            }
        }
        return $plh;
    }
));
```
