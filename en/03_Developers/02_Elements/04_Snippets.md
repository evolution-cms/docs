### What are snippets ###

A snippet is PHP code that outputs the result of its work at the place in the template/chunk where this snippet can be called. Any parameters can be passed in snippets, including other snippets, TV parameters or chunks.

### What are snippets for ###
As a rule, snippets are used to display dynamically changing content.
They can be used to create menus, comments, news feeds, blogs or any other functionality that is possible in the php language in connection with the API of the Evolution system.

### Snippet Call ###

You can call the snippet anywhere in the resource. As a general rule, this usually happens in a template or chunks.
It is highly discouraged to call snippets in the content field, especially if this field is editable by site managers.

```
[!mySnippet? &param=`Value`!] - non-cacheable call
[[mySnippet? &param=`Value`]] - cached call
```

### API call ###
```
$params => array('param' => 'Value');
$modx->runSnippet('mySnippet', $params);
```

### Snippet example ###

For example, let's make a snippet that shows the date the document was created in a human-readable format.
The document creation date is in the system TV parameter [\*createdon\*].
The parameter stores the creation date of the document in unixtime format and its value looks something like this: 1144904400.

```
<?php
$fullMonth = array(
     '1' => 'January',
     '2' => 'February',
     '3' => 'March',
     '4' => 'April',
     '5' => 'May',
     '6' => 'June',
     '7' => 'July',
     '8' => 'August',
     '9' => 'September',
     '10' => 'October',
     '11' => 'November',
     '12' => 'December');
$output = strftime('%d.%m.%Y',$date);
$date = explode("., $output);
$month = (int)$date[1];
$m = $fullMonth[$month];
$out = $date[0] . ' ' . $m. ' ' . $date[2];
return $out;
```

**Using.**

Let's pass the TV parameter [\*createdon\*] to the snippet:
```
[[ruDate? &date=`[*createdon*]`]]
```
As a result, we will get something like this:
```
May 21, 2018
```

### Popular Snippets ###

- **DocLister** - allows you to output data from any tables. Ideal for creating news feeds, blogs, product or service catalogs.
- **FormLister** - a snippet for working with forms. Perfectly suitable for forms for sending messages from the site, authorization-registration and any possible functionality related to a personal account.
- **phpthumb** - a snippet for creating thumbnails of images, applying watermarks and other work with images.
- **JotX** - a snippet for creating comments.
- **Sitemap** - sitemap.xml generator.