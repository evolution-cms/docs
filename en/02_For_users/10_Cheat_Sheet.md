## Placeholders

Place holders must take the format as:
```
[*pagetitle*]
```

| Placeholders | Description |
| --- | --- |
| pagetitle | document title |
|longtitle |  long document title |
|description| document description |
|introtext| document summary text | 
|content| document content
|alias| URL alias |
|link_attributes| document link attributes |
|id| document id number |
|pub_date| publish date |
|unpub_date| unpublish date |
|createdby| created by username |
|createdon| created on | 
|editedby| edited by username |
|editedon| edited on
|type| type of document |
|contentType| |
|published| yes or no | 
|parent| parent document id |
|isfolder| is this document a container |
|richtext| richtext or plaintext
|template| template id
|menuindex| integer for ordering documents
|searchable| 0 or 1 |
|cacheable| 0 or 1 |
|deleted| 0 or 1 |
|deletedon| deleted date |
|deletedby| delete by username |
|menutitle| Short menu title |
|donthit| 0 or 1 |
|haskeywords| 
|hasmetatags| 0 or 1 |
|privateweb| The document is part of a private group of user documents (1|0) |
|privatemgr| The document is included in the private group of management documents (1|0) |
|content_dispo| 
|hidemenu| Show in Menu 0 or 1 |

## Tags

The below tags represent the different ways EvolutionCMS can produce output

| Tags | Description |
| --- | --- |
| [[snippet]] | 
| [!snippet!]	|
| [(setting)]	| 
| ```[*resourceField/TV*]``` | 
| [^timing^] |
| ```[~link~]``` |
| {{chunk}}	|
| [+placeholder+]	|

### SystemInfo

| System Info | Description |
| --- | --- |
| [^qt^] |
| [^q^] |
| [^p^] |
| [^t^] |
| [^s^] |
| [^m^] |

## System settings

System settings are the configurable variables that can be changed from Manager | Configuration.

| System Settings | Description |
| --- | --- |
| [(allow_duplicate_alias)] | 
| [(automatic_alias)] | 
| [(base_url)] or [(site_url)] |
| [(cache_default)] | 
| [(captcha_words)] | 
| [(custom_contenttype)] | 
| [(default_template)] | 
| [(editor_css_path)] | 
| [(emailsender)] | 
| [(emailsubject)] |
| [(error_page)] | 
| [(modx_charset)] | 
| [(fck_editor_autolang)] | 
| [(fck_editor_style)] | 
| [(fck_editor_toolbar)] |
| [(filemanager_path)] |
| [(friendly_alias_urls)] |
| [(friendly_urls)] |
| [(friendly_url_prefix)] |
| [(friendly_url_suffix)] |
| [(manager_language)] |
| [(manager_layout)] | 
| [(manager_theme)] | 
| [(number_of_logs)] | 
| [(number_of_messages)] | 
| [(number_of_results)] | 
| [(publish_default)] | 
| [(rb_base_dir)] | 
| [(rb_base_url)] | 
| [(reset_template)] | 
| [(resolve_hostnames)] | 
| [(search_default)] | 
| [(server_offset_time)] | 
| [(server_protocol)] | 
| [(settings_version)] | 
| [(show_preview)] | 
| [(signupemail_message)] | 
| [(site_name)] |
| [(site_start)] | 
| [(site_status)] | 
| [(site_unavailable_message)] | 
| [(site_unavailable_page)] | 
| [(strip_image_paths)] | 
| [(top_howmany)] | 
| [(track_visitors)] | 
| [(udperms_allowroot)] | 
| [(unauthorized_page)] | 
| [(upload_files)] | 
| [(upload_maxsize)] | 
| [(use_alias_path)] | 
| [(use_captcha)] | 
| [(use_editor)] |
| [(use_udperms)] | 
| [(webpwdreminder_message)] | 
| [(websignupemail_message)] | 
| [(which_editor)] | 
