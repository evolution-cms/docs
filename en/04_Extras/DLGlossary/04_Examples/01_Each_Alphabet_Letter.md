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
	$params['parents'] = 145;
	$params['field'] = 'c.pagetitle';
	$params['char'] = chr($alpha);
	$params['register'] = 1;
	$params['debug']= 0;
	$params['tpl'] = "@CODE:<li><img src='[+tv.image+]' alt='[+e.pagetitle+]'><a href='[+url+]'>[+title+] ([+id+])</a></li>";
	
	$output .= "<h2>".chr($alpha)."</h2>";
	$output .= $modx->runSnippet("DLGlossary", $params);
}

return $output;
```
