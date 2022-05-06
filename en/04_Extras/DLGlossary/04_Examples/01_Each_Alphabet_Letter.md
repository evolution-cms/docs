## Produce a glossary page for each letter of the alphabet
In order to achieve this we need to call the snippet for each letter.
### pre-requisites
* DocLister
* DLGlossary

### Required
You will need to create a new snippet to loop through each letter. This allows you to add one snippet call to your resource for the output.

#### Snippet: GlossaryList
```
<?php
$output = '';

for($alpha = 65; $alpha <= 90; $alpha++) {
	// run snippet	
	$params['parents'] = &parents;
	$params['field'] = 'c.pagetitle';
	$params['char'] = chr($alpha);
	$params['register'] = 1;
	$params['debug']= &debug;
	$params['tpl'] = "@CODE:<li><img src='[+tv.image+]' alt='[+e.pagetitle+]'><a href='[+url+]'>[+title+] ([+id+])</a></li>";
	
	$output .= "<h2>".chr($alpha)."</h2>";
	$output .= $modx->runSnippet("DLGlossary", $params);
}

return $output;
```

### Parameters

* parents - a comma seperated list of parent document ids.
* debug - 0 - none, 1 - debug code. default: 0

### Snippet call
```
[[GlossaryList? &parents=`145` &debug=`0`]]
