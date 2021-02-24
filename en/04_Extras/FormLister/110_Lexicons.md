## Lexicons

To use lexicons you should create a file named "lexicon name.inc.php" in a folder named as full language name (russian-UTF8, english etc.) or ISO 639-1 code (en, ru etc.):
```
<?php
if (!defined('MODX_BASE_PATH')) {die();}
$_lang = array();
$_lang['key'] = 'Value.';
return $_lang;
?>
```
Parameters to load lexicons are:

* langDir - lexicon folder path;
* lang - lexicon language name (the "manager_language" configuration parameter value by default) or ISO 639-1 code; ISO codes are translated to language names for bundled languages;
* lexicon - lexicon names, comma separated. Or specify an array of values right here:
```
&lexicon=`{
    "english":{
        "test":"Test lexicon value",
        "foo":"Another lexicon value",
        "bar":"And one more value"
    },
    "russian-UTF8":{
        "test":"Проверка",
        "foo":"Еще проверка",
        "bar":"И еще"
    }
}`
```
Or:
```
&lexicon=`{
    "en":{
        "test":"Test lexicon value",
        "foo":"Another lexicon value",
        "bar":"And one more value"
    },
    "ru":{
        "test":"Проверка",
        "foo":"Еще проверка",
        "bar":"И еще"
    }
}`
```

After that you can use the [%key%] placeholders to output lexicon entries. It possible to connect external lexicons with the help of adapter class (see "assets/snippets/FormLister/lib/LexiconHandlers/EvoBabelLexiconHandler.php" file for details; adapter class name should be set in "lexiconHandler" parameter.
