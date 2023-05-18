## Template Service Events ##
All events related to the display of the page
### OnAfterLoadDocumentObject 
### OnBeforeLoadDocumentObject
### OnBeforeLoadExtension 
### OnBeforeParseParams

### OnDocPublished
Runs when a document is published
```
manager/processors/publish_content.processor.php
```
**Returns:**
```
docid - id Document
```

### OnDocUnPublished
Runs when a document is unpublished
```
manager/processors/unpublish_content.processor.php
```
**Returns:**
```
docid - id Document
```

### OnLoadDocumentObject
Runs after formation $modx->documentObject
```
manager/includes/document.parser.class.inc.php
```

### OnLoadWebDocument
Runs if the document was taken from the database
```
manager/includes/document.parser.class.inc.php
```


### OnLogPageHit 
It is launched if the "Track visits" setting is selected. This event is raised before the document is loaded.
```
manager/includes/document.parser.class.inc.php
```

### OnMakeDocUrl

### OnParseDocument
Runs before TV, snippets and chunks are processed
```
manager/includes/document.parser.class.inc.php
```

### OnParseProperties

### OnWebPageComplete
Triggered when the "Track visits" setting is worth it
```
manager/includes/document.parser.class.inc.php
```
	

### OnWebPageInit
Runs after the cache has been loaded into the $modx

### OnWebPagePrerender
Runs before the page is given to the client. This is the last event raised before the page is sent to the client browser.
```
manager/includes/document.parser.class.inc.php
```

 
## Cache Service Events ## 
Caching events

### OnBeforeCacheUpdate 
Runs before the cache is refreshed

### OnBeforeSaveWebPageCache
Runs after the page is cached

### OnCacheUpdate
Runs immediately after being written to the cache

### OnLoadWebPageCache
Runs after the cached page is loaded

### OnMakePageCacheKey
 
## Web Access Service Events ## 

### OnBeforeWebLogin
### OnBeforeWebLogout
### OnWebAuthentication 
### OnWebChangePassword
### OnWebCreateGroup 
### OnWebDeleteUser
### OnWebLogin 
### OnWebLogout
### OnWebSaveUser
 
## Manager Access Events ## 

### OnBeforeManagerLogin 
### OnBeforeManagerLogout
### OnBeforeManagerPageInit 
### OnManagerAuthentication
### OnManagerChangePassword 
### OnManagerCreateGroup
### OnManagerDeleteUser 
### OnManagerFrameLoader
### OnManagerLogin 
### OnManagerLoginFormPrerender
### OnManagerLoginFormRender 
### OnManagerLogout
### OnManagerMainFrameHeaderHTMLBlock 
### OnManagerMenuPrerender
### OnManagerNodePrerender 
### OnManagerNodeRender
### OnManagerPageInit 
### OnManagerPreFrameLoader
### OnManagerSaveUser 
### OnManagerTopPrerender
### OnManagerTreeInit 
### OnManagerTreePrerender
### OnManagerTreeRender 
### OnManagerWelcomeHome
Use this event you can add custom widgets to home page of admin panel.
```php
     Event::listen(
        'evolution.OnManagerWelcomeHome',
        function ($params) {
            $params['widgets']['tutorial'] = [
                'menuindex' => '1',
                'id'        => 'tutorial',
                'cols'      => 'col-sm-12',
                'icon'      => 'fab fa-leanpub',
                'title'     => 'Video-tutorial',
                'body'      => '<div class="card-body text-center">
                            <iframe width="500" height="250" src="https://www.youtube.com/embed/videoseries?list=yourplaylist" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
                        </div>'
            ];
            return serialize($params['widgets']);
        }
    );
```
### OnManagerWelcomePrerender 
### OnManagerWelcomeRender
 
## Parser Service Events ## 

### OnFileManagerUpload 
### OnPageNotFound
### OnPageUnauthorized 
### OnSiteRefresh
 
## Chunks ## 

### OnBeforeChunkFormDelete 
### OnBeforeChunkFormSave
### OnChunkFormDelete 
### OnChunkFormPrerender
### OnChunkFormRender 
### OnChunkFormSave
 
## Documents ## 

### OnAfterMoveDocument 
### OnBeforeDocDuplicate
### OnBeforeDocFormDelete 
### OnBeforeDocFormSave
### OnBeforeEmptyTrash 
### OnBeforeMoveDocument
### OnCreateDocGroup 
### OnDocDuplicate
### OnDocFormDelete 
### OnDocFormPrerender
### OnDocFormRender 
### OnDocFormSave
### OnDocFormTemplateRender 
### OnDocFormUnDelete
### OnEmptyTrash 
### OnStripAlias
 
## File Browser Events ## 

### OnFileBrowserUpload
 
## Modules ## 

### OnBeforeModFormDelete 
### OnBeforeModFormSave
### OnModFormDelete 
### OnModFormPrerender
### OnModFormRender 
### OnModFormSave
 
## Plugins ## 

### OnBeforePluginFormDelete 
### OnBeforePluginFormSave
### OnPluginFormDelete 
### OnPluginFormPrerender
### OnPluginFormRender 
### OnPluginFormSave
 
## RichText Editor

### OnRichTextEditorInit 
### OnRichTextEditorRegister
 
## Snippets ## 

### OnBeforeSnipFormDelete 
### OnBeforeSnipFormSave
### OnSnipFormDelete 
### OnSnipFormPrerender
### OnSnipFormRender 
### OnSnipFormSave
 
## System Settings ## 

### OnFriendlyURLSettingsRender 
### OnInterfaceSettingsRender
### OnMiscSettingsRender 
### OnSiteSettingsRender
### OnUserSettingsRender
 
## Template Variables ## 

### OnBeforeTVFormDelete 
### OnBeforeTVFormSave
### OnTVFormDelete 
### OnTVFormPrerender
### OnTVFormRender 
### OnTVFormSave
 
## Templates ## 

### OnBeforeTempFormDelete 
### OnBeforeTempFormSave
### OnTempFormDelete 
### OnTempFormPrerender
### OnTempFormRender 
### OnTempFormSave
 
## Users ## 

### OnBeforeUserFormDelete 
### OnBeforeUserFormSave
### OnUserFormDelete 
### OnUserFormPrerender
### OnUserFormRender 
### OnUserFormSave
 
## Web Users ## 

### OnBeforeWUsrFormDelete 
### OnBeforeWUsrFormSave
### OnWUsrFormDelete 
### OnWUsrFormPrerender

### OnWUsrFormRender 
Runs when the Web user's edit form is displayed
```
manager/actions/mutate_web_user.dynamic.php
```
Returns:
```
id - User Id
```
### OnWUsrFormSave
