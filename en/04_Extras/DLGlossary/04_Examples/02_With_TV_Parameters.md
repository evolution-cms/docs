## Produce a glossary page for each letter of the alphabet including TV Parameters
In order to achieve this we need to call the snippet for each letter.
We also need to duplicate and amend the original DLGlossary snippet in order to make this work.
### pre-requisites
* DocLister
* DLGlossary

### Required
You will need to create a new snippet to loop through each letter. This allows you to add one snippet call to your resource for the output.

You will need to duplicate DLGlossary and make a change to the code in order to allow this to work.

#### Snippet: GlossaryList
```
<?php
$params['debug'] = &debug;
$params['parents'] = $parents;
$params['field'] = 'c.pagetitle';

$params['register'] = 1;
$params['tvList'] = $tvList;

$params['paginate'] = 'pages';
$params['ownerTPL'] = '@CODE:<ul>[+dl.wrap+]</ul>';
$params['noneTPL'] = '@CODE:Nothing to display';
$params['noneWrapOuter'] = 0;
$params['tpl'] = "@CODE:<li><img src='[+tv.image+]' alt='[+e.pagetitle+]'><a href='[+url+]'>[+title+] ([+id+]) [+tv.tags+]</a></li>";

$output = '';

for($alpha = 65; $alpha <= 90; $alpha++) {
	$params['char'] = chr($alpha);
	
	$filters = explode(",",$params['tvList']);

	$filterOut = 'OR(';
	foreach ( $filters as $key => $value )
	{
		$filterOut .= 'tv:'.$value.':like-r:'.chr($alpha).';';	
	}
	$filterOut = rtrim($filterOut, ";");
	$filterOut.= ')';
	
	$params['filters'] = $filterOut;
	
	$output .= "<h2>".chr($alpha)."</h2>";
	$output .= $modx->runSnippet("DLGlossaryTags", $params);
}

return $output;
```

### Parameters

* parents - a comma seperated list of parent document ids.
* tvList - a comma seperated list of TV parameters to include.
* debug - 0 - none, 1 - debug code. default: 0

### Snippet call
```
[[GlossaryList? &parents=`145` &tvList=`documentTags` &debug=`0`]]
```

## DLGlossaryTags
### create a new snippet: DLGlossaryTags

```
<?php
if (! defined('MODX_BASE_PATH')) {
    die('HACK???');
}

require_once(MODX_BASE_PATH . "assets/snippets/DocLister/lib/sqlHelper.class.php");

switch (true) {
    case ( ! empty($fromget)):
        /** Брать ли данные из GET */
        $data = $_GET;
        $from = $fromget;
        break;
    case ( ! empty($frompost)):
        /** Брать ли данные из POST */
        $data = $_POST;
        $from = $frompost;
        break;
    default:
        $from = $data = null;
}
if (! empty($from)) {
    $char = (isset($data[$from]) && is_scalar($data[$from])) ? $data[$from] : null;
}
$char = ( ! empty($char) || (isset($char) && $char == 0)) ? $char : '';
/** С какого символа должен начинаться текст */

$field = ! empty($field) ? $field : 'c.pagetitle';
/** Поле по которому фильтровать */

$setActive = ! empty($setActive) ? true : false;
/** Активировать наборы символов */

$regexpSep = ! empty($regexpSep) ? $regexpSep : '||';
/** Разделитель в наборах регулярок */

$regexp = ! empty($regexp) ? $regexp : 'az||0-9||a-z';
/** Наборы поддерживаемых регулярок */
$regexp = explode($regexpSep, $regexp);

$loadfilter = ! empty($loadfilter) ? $loadfilter : '';
/** Какой фильтр загружать */

$register = empty($register) ? true : false; //Чувствительность к регистру.

if (preg_match("/\s+/", $field)) {
    /** SQL-injection protection :-)  */
    $char = '';
}

$out = $where = '';
$action = "like-r";

if ($char !== null) {
    if ($register) {
        $char = mb_strtolower($char, 'UTF-8');
    }

    if (mb_strlen($char, 'UTF-8') == 1) {
        $char = preg_match('/^[aza-z0-9]/iu', $char) ? $char : null;
    } else {
        if ($setActive && in_array($char, $regexp)) {
            $action = "regexp";
            $char = "^[{$char}]";
        } else {
            $char = null;
        }
    }
}

if ($char === null) {
    $modx->sendErrorPage();
}

$p = &$modx->event->params;
if (! is_array($p)) {
    $p = array();
}
if (! empty($loadfilter)) {
    $field = explode(".", $field);
    $field = end($field);
    if (! empty($p['filters'])) {
        $p['filters'] = rtrim(trim($p['filters']), ";") . ";";
    }
    $p['filters'] = "AND({$loadfilter}:{$field}:{$action}:{$char})";
} else {
    $field = sqlHelper::tildeField($field);
    if ($action === 'regexp') {
        $where = $field . " REGEXP '" . $modx->db->escape($char) . "'";
    } else {
        $where = sqlHelper::LikeEscape($modx, $field, $char, '=', '[+value+]%');
    }
    if (empty($p['addWhereList'])) {
        $p['addWhereList'] = $where;
    } else {
        $p['addWhereList'] = sqlHelper::trimLogicalOp($p['addWhereList']) . " AND " . $where;
    }
}
// We have to unset this parameter so the SQL statement looks in the TVs only.
unset($p['addWhereList']);

return $modx->runSnippet("DocLister", $p);
```

This snippet is identical to the original but with one change.  We are removing the &addWhereList parameter completely so we can allow for TV parameters.
#### Caveat

This method will duplicate the documents in the glossary list as each step runs through the parent document and TV parameters. 

For instance, a document with a title "How To" and a TV Parameter "Tutorial" will show up in both **H** and **T**.

Also, when using TV parameters the program will view a comma seperated list as a string. So, "Test, Tutorial, First" would only appear in **T** for "Test" as this is the first letter in the string.
