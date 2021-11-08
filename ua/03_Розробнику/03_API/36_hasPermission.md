###Перевірка прав менеджера

bool hasPermission(string $pm);

**$pm** - назва перевіряючого права. Може приймати наступні значення:

- view_document
- new_document
- save_document
- publish_document
- delete_document
- action_ok
- logout
- help
- messages
- new_user
- edit_user
- logs
- edit_parser
- save_parser
- edit_template
- settings
- credits
- new_template
- save_template
- delete_template
- edit_snippet
- new_snippet
- save_snippet
- delete_snippet
- edit_chunk
- new_chunk
- save_chunk
- delete_chunk
- empty_cache
- edit_document
- change_password
- error_dialog
- about
- file_manager
- save_user
- delete_user
- save_password
- edit_role
- save_role
- delete_role
- new_role
- access_permissions
- bk_manager
- new_plugin
- edit_plugin
- save_plugin
- delete_plugin
- new_module
- edit_module
- save_module
- delete_module
- exec_module
- view_eventlog
- delete_eventlog
- manage_metatags
- edit_doc_metatags
- new_web_user
- edit_web_user
- save_web_user
- delete_web_user
- web_access_permissions
- view_unpublished
- import_static
- export_static

***

####Приклад

	$modx->hasPermission('delete_document');
	//поверне true, якщо є право на видалення документа, або false, якщо права немає.
