## Options

### customLang

Loading an arbitrary lexicon.

The possible values are the name of the php file from the /lang/ folder with the associative array $_lang

The default value is empty.

Using the lexicon, you can override both standard language messages from the /core/lang/[(manager_language)]/ folder and create new ones. To override, it is important to specify the full name of the standard language key in the array (for example, core.test or paginate.next). To use the lexicon, it is enough to write the [%Lexicon Key%] tag in the template
