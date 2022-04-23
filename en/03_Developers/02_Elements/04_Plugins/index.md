## What is a plugin
Plugins are snippets of code that are tied to system events and are executed when that event occurs.

## How plugins work
When performing almost any action, the system generates events. For example, when a resource is published, the OnDocPublished event occurs, when authorizing, OnManagerLogin occurs, and so on.

Often, add-ons themselves can generate events. For example, the Shopkeeper add-on creates more than a dozen different events, to each of which you can attach your code and add or change the functionality of almost any event that occurs on the site.

**Important:** plugins work both for events inside the administration panel and for events on the front of the site. You can see the full list of events when creating the plugin on the "SYSTEM EVENTS" tab.

## Examples of plugins
### Word replacement plugin
This plugin will work before the contents of the resource are shown to the visitor (OnWebPagePrerender) and replace the words from the array with a stub.

```
$words = array("bad word", "one more"); // words for filtration
$e = &$modx->Event;
if($e->name == 'OnWebPagePrerender') { // check if this is the event we need
	$out = &$modx->documentOutput; // get a link to the content of the resource
	$out = str_replace($words,"<b>censorship</b>",$out); // replace the words from the array with "stub".
}
```

### Plugin to modify the resource tree
The previous example worked on a custom part of the site. And this plugin will work on the event of the formation of the left menu in the administration panel. It will replace the resource icon with id=3 and create its own context menu for it.

```
$e = &$modx->Event;
if($e->name = 'OnManagerNodePrerender'){
	if($ph['id'] == '3'){
		$ph['icon'] = "<i class='fa fa-copy'></i>";
		$ph['icon_folder_open'] = "<i class='fa fa-copy'></i>";
		$ph['icon_folder_close'] = "<i class='fa fa-copy'></i>";	
		$ph['contextmenu'] = array(
			'header1' => array(
				'innerText' => "This is a catalogue"
			),
			'item3' => array(
				'innerHTML' => '<i class="fa fa-file-o fa-fw fa-lg"></i> Add product',
				'title' => 'Child resource',
				'id' => 'item3',
				'onclick' => "modx.tree.menuHandler(3);"
			),
			'item2' => array(
				'innerHTML' => '<i class="fa fa-pencil-square-o fa-fw fa-lg"></i> Edit',
				'title' => ' Edit',
				'id' => 'item2',
				'onclick' => "modx.tree.menuHandler(2);"
			),
			'item12' => array(
				'innerHTML' => '<i class="fa fa-eye fa-fw fa-lg"></i> Scan',
				'title' => 'Scan',
				'id' => 'item12',
				'onclick' => "modx.tree.menuHandler(12);",
			)
		);
	}
}
$e->output(serialize($ph));
```
Often, add-ons give plugins variables to change. As a rule, these variables are described in the documentation for the addendum.
