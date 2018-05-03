## Template Service Events ##
Все события, связанные с отображением страницы
### OnAfterLoadDocumentObject 
### OnBeforeLoadDocumentObject
### OnBeforeLoadExtension 
### OnBeforeParseParams

### OnDocPublished
Запускается при публикации документа
```
manager/processors/publish_content.processor.php
```
**Возвращает:**
```
docid - id документа
```

### OnDocUnPublished
Запускается при снятии документа с публикации
```
manager/processors/unpublish_content.processor.php
```
**Возвращает:**
```
docid - id документа
```

### OnLoadDocumentObject
Запускается после формирования $modx->documentObject
```
manager/includes/document.parser.class.inc.php
```

### OnLoadWebDocument
Запускается, если документ был взят из базы
```
manager/includes/document.parser.class.inc.php
```


### OnLogPageHit 
Запускается, если стоит настройка "Отслеживать посещения". Это событие вызывается перед загрузкой документа.
```
manager/includes/document.parser.class.inc.php
```

### OnMakeDocUrl

### OnParseDocument
Запускается перед тем, как будут обработаны ТВ, сниппеты и чанки
```
manager/includes/document.parser.class.inc.php
```

### OnParseProperties

### OnWebPageComplete
Запускается, если стоит настройка "Отслеживать посещения"
```
manager/includes/document.parser.class.inc.php
```
	

### OnWebPageInit
Запускается после того, как кэш был загружен в $modx

### OnWebPagePrerender
Запускается перед тем, как страница будет отдана клиенту. Это последнее событие, вызванное до того, как страница будет отправлена в клиентский браузер.
```
manager/includes/document.parser.class.inc.php
```

 
## Cache Service Events ## 
События кэширования

### OnBeforeCacheUpdate 
Запускается перед обновлением кэша

### OnBeforeSaveWebPageCache
Запускается после сохранения страницы в кэше

### OnCacheUpdate
Запускается сразу после записи в кэш

### OnLoadWebPageCache
Запускается после загрузки кэшируемой страницы

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
Запускается при отображении формы редактирования веб-пользователя
```
manager/actions/mutate_web_user.dynamic.php
```
Возвращает:
```
id - id пользователя
```
### OnWUsrFormSave