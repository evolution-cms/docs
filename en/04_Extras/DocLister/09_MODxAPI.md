## Introduction MODxAPI 
is an attempt to implement the Data mapper pattern. It was originally designed as a replacement for the DocManager library, but in the end, the code was optimized and the potential to create a wrapper with arbitrary logic for any tables was laid.

### Supports 
* modResource models - Documents (data from site_content and site_tmplvar_contentvalues tables) 
* modUsers - Web users (data from web_users tables and web_user_attributes) 
* modCategories - Categories (data from categories tables) 
* modChunk - Chunks (data from tables site_htmlsnippets) 
* modModule - Modules (data from tables site_modules) 
* modPlugin - Plugins (data from tables site_plugins 
* modSnippet - Snippets (data from tables site_snippets) 
* modTV - TV parameters (data from tables site_tmplvars) modTemplate - Templates (data from tables site_templates)

If you want, you can quickly create your own model for any table. To do this, there is a preset of the autoTable class. In the most primitive case, it is enough to specify only the name of your table. Take a look at an example of creating a model for a table named tests:
```
<?php
include_once(MODX_BASE_PATH. "assets/lib/MODxAPI/autoTable.abstract.php");
class modTests extends autoTable
{
    protected $table = "tests";
}
```
### Examples
The create, edit, delete, save methods are relevant for all models. But as an example, we will consider the modResource model.
```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
$doc = new modResource($modx);

/** 
* Prepare the creation of a document with the following data:
* Template ID = 10
* As a parent use a document with ID = 1
* pagetitle document title = example
*/
$doc->create(array(
	'pagetitle' => 'example',
	'template' => 10,
	'parent' => 1
));

/** 
* change the pagetitle title of the document to a new title 
*/
$doc->set('pagetitle', 'new title');

/*
* Save document by raising the OnBeforeDocFormSave OnDocFormSave event,
* but do not reset the cache. 
* Put the ID of the new document in the id variable
*/
$id = $doc->save(true, false);

/** 
* Open for editing document with ID = 10 
*/ 
$doc->edit(10);

/** 
* Change parent document
*/
$doc->set('parent', 0);


/*
* Save the document without raising the OnBeforeDocFormSave OnDocFormSave event,
* But at the same time we produce a cache.
* Document ID is stored in a variable $id
*/
$id = $doc->save(false, true);

/***
* Delete all documents marked for deletion.
* This will raise the OnBeforeEmptyTrash and OnEmptyTrash events
* If you change the parameter value from true to false, no events will be raised, although the documents will be deleted
*/
$doc->clearTrash(true);

/** 
* Delete a document with ID = 5, bypassing the cart
* This will cause the OnBeforeEmptyTrash and OnEmptyTrash events.
*/
$doc->delete(5, true);
```
With the help of the modUsers model, you can not only record and receive data, but also manipulate authorization:
```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$user = new modUsers($modx);

/**
* Log in as a web user with ID = 1
*/
$user->authUser(1);

/**
* Check the status of blocking a web user with ID = 1 
* This method returns a boolean value
* true - blocked
* false - active
*/
$flag = $user->checkBlock(1);

/**
* Check myPassword password for web user with ID = 1 
* Then check the lock status. Even if the password is correct and the user is locked, this method will return false. If you change the value of parameter 3 to false, the lock status will not be checked.
* This method returns a boolean value
* true - correct password
* false - password is not correct
*/
$flag = $user->testAuth(1, 'myPassword', true);

/**
* Force logout of the web user
*/
$user->logOut();
```
### Practical the use of modUsers 
The following plugin for the OnWebPageInit and OnPageNotFound events allows you to instantly apply the lock. This is useful when the user seems to be banned, but continues to be active, because the session has not expired.
```
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$modx->user = new modUsers($modx);
if($modx->isFrontend() && $modx->getLoginUserID('web')){
	$modx->user->edit((int)$modx->getLoginUserID('web'));
	if(!$modx->user->getID() || $modx->user->checkBlock()){
		$modx->user->logOut();
	}
}
```
modResource The following snippet allows you to sequentially retrieve the field values of the same document without having to run a retry SQL query.
```
/**
* <h5>[[DocInfo? &id=`6` &field=`pagetitle`]]</h5>
* <img src="[[DocInfo? &id=`6` &field=`image`]]" />
* Only 1 SQL query will be executed with this snippet
*/
if(empty($modx->doc)){
	include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
	$modx->doc = new modResource($modx);
}
$id = isset($id) ? (int)$id : $modx->documentObject['id'];
$field = isset($field) ? (string)$field : 'id';
if($field == 'id'){
    $out = $id;
}else{
    if($modx->documentObject['id'] == $id){
        $out = isset($modx->documentObject[$field]) ? $modx->documentObject[$field] : '';
        if(is_array($out)){
           $out = isset($out[1]) ? $out[1] : '';
        }
    }else{
		$doc = clone $modx->doc;
        $out = $doc->edit($id)->get($field);
    }
}
return (string)$out;
```
