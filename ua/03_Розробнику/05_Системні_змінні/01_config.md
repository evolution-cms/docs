###Системні налаштування

array config

Містить інформацію про системні налаштування у вигляді асоціативного масива. Використовувати напряму його не рекомендується і для отримання інформації існує метод API - getConfig

####Приклад
````
echo $modx->config['modx_charset'];
````
Можна переглянути всі можливі елементи налаштувань

````
var_dump($modx->config);
````
    
Поверне:

````
array(162) {
  ["manager_theme"]=>  string(20) "MODxRE2_DropdownMenu"
  ["settings_version"]=>  string(12) "1.2.1-d9.1.3"
  ["show_meta"]=>  string(1) "1"
  ["server_offset_time"]=>  string(1) "0"
  ["server_protocol"]=>  string(4) "http"
  ["manager_language"]=>  string(12) "russian-UTF8"
  ["modx_charset"]=>  &string(5) "UTF-8"
  ["site_name"]=>  string(6) "site"
  ["site_start"]=>  string(1) "1"
  ["error_page"]=>  string(2) "41"
  ["unauthorized_page"]=>  string(2) "43"
  ["site_status"]=>  string(1) "1"
  ["site_unavailable_message"]=>  string(33) "The site is currently unavailable"
  ["track_visitors"]=>  string(1) "0"
  ["top_howmany"]=>  string(2) "10"
  ["auto_template_logic"]=>  string(7) "sibling"
  ["default_template"]=>  string(1) "3"
  ["old_template"]=>  string(1) "3"
  ["publish_default"]=>  string(1) "1"
  ["cache_default"]=>  string(1) "1"
  ["search_default"]=>  string(1) "1"
  ["friendly_urls"]=>  string(1) "1"
  ["friendly_url_prefix"]=>  string(0) ""
  ["friendly_url_suffix"]=>  string(5) ".html"
  ["friendly_alias_urls"]=>  string(1) "1"
  ["use_alias_path"]=>  string(1) "1"
  ["use_udperms"]=>  string(1) "1"
  ["udperms_allowroot"]=>  string(1) "0"
  ["failed_login_attempts"]=>  string(1) "3"
  ["blocked_minutes"]=>  string(2) "60"
  ["use_captcha"]=>  string(1) "0"
  ["captcha_words"]=>  string(19) "0,1,2,3,4,5,6,7,8,9"
  ["emailsender"]=>  string(15) "email@mail.ru"
  ["email_method"]=>  string(4) "mail"
  ["smtp_auth"]=>  string(1) "0"
  ["smtp_host"]=>  string(0) ""
  ["smtp_port"]=>  string(2) "25"
  ["smtp_username"]=>  string(0) ""
  ["emailsubject"]=>  string(18) "Your login details"
  ["number_of_logs"]=>  string(3) "100"
  ["number_of_messages"]=>  string(2) "30"
  ["number_of_results"]=>  string(2) "20"
  ["use_editor"]=>  string(1) "1"
  ["use_browser"]=>  string(1) "1"
  ["rb_base_dir"]=>  string(46) "/home/site/web/site.ru/public_html/assets/"
  ["rb_base_url"]=>  string(7) "assets/"
  ["which_editor"]=>  string(4) "none"
  ["fe_editor_lang"]=>  string(12) "russian-UTF8"
  ["fck_editor_toolbar"]=>  string(8) "standard"
  ["fck_editor_autolang"]=>  string(1) "0"
  ["editor_css_path"]=>  string(0) ""
  ["editor_css_selectors"]=>  string(0) ""
  ["strip_image_paths"]=>  string(1) "1"
  ["upload_images"]=>  string(37) "bmp,ico,gif,jpeg,jpg,png,psd,tif,tiff"
  ["upload_media"]=>  string(31) "au,avi,mp3,mp4,mpeg,mpg,wav,wmv"
  ["upload_flash"]=>  string(11) "fla,flv,swf"
  ["upload_files"]=>  string(210) "bmp,ico,gif,jpeg,jpg,png,psd,tif,tiff,fla,flv,swf,aac,au,avi,css,cache,doc,docx,gz,gzip,htaccess,htm,html,js,mp3,mp4,mpeg,mpg,ods,odp,odt,pdf,ppt,pptx,rar,tar,tgz,txt,wav,wmv,xls,xlsx,xml,z,zip,JPG,JPEG,PNG,GIF"
  ["upload_maxsize"]=>  string(7) "1048576"
  ["new_file_permissions"]=>  string(4) "0644"
  ["new_folder_permissions"]=>  string(4) "0755"
  ["filemanager_path"]=>  string(39) "/home/site/web/site.ru/public_html/"
  ["theme_refresher"]=>  string(13) "1492629357000"
  ["manager_layout"]=>  string(1) "4"
  ["custom_contenttype"]=>  string(156) "application/rss+xml,application/pdf,application/vnd.ms-word,application/vnd.ms-excel,text/html,text/css,text/xml,text/javascript,text/plain,application/json"
  ["auto_menuindex"]=>  string(1) "1"
  ["session.cookie.lifetime"]=>  string(6) "604800"
  ["mail_check_timeperiod"]=>  string(3) "600"
  ["manager_direction"]=>  string(3) "ltr"
  ["tinymce_editor_theme"]=>  string(6) "editor"
  ["tinymce_custom_plugins"]=>  string(112) "style,advimage,advlink,searchreplace,print,contextmenu,paste,fullscreen,nonbreaking,xhtmlxtras,visualchars,media"
  ["tinymce_custom_buttons1"]=>
  string(216) "undo,redo,selectall,separator,pastetext,pasteword,separator,search,replace,separator,nonbreaking,hr,charmap,separator,image,link,unlink,anchor,media,separator,cleanup,removeformat,separator,fullscreen,print,code,help"
  ["tinymce_custom_buttons2"]=>
  string(201) "bold,italic,underline,strikethrough,sub,sup,separator,bullist,numlist,outdent,indent,separator,justifyleft,justifycenter,justifyright,justifyfull,separator,styleselect,formatselect,separator,styleprops"
  ["tree_show_protected"]=>  string(1) "0"
  ["rss_url_news"]=>  string(41) "http://feeds.feedburner.com/modx-announce"
  ["rss_url_security"]=>  string(40) "http://feeds.feedburner.com/modxsecurity"
  ["validate_referer"]=>  string(1) "1"
  ["datepicker_offset"]=>  string(3) "-10"
  ["xhtml_urls"]=>  string(1) "0"
  ["allow_duplicate_alias"]=>  string(1) "0"
  ["automatic_alias"]=>  string(1) "1"
  ["datetime_format"]=>  string(10) "dd-mm-YYYY"
  ["warning_visibility"]=>  string(1) "0"
  ["remember_last_tab"]=>  string(1) "1"
  ["enable_bindings"]=>  string(1) "1"
  ["seostrict"]=>  string(1) "1"
  ["cache_type"]=>  string(1) "2"
  ["maxImageWidth"]=>  string(4) "1600"
  ["maxImageHeight"]=>  string(4) "2500"
  ["thumbWidth"]=>  string(3) "150"
  ["thumbHeight"]=>  string(3) "150"
  ["thumbsDir"]=>  string(7) ".thumbs"
  ["jpegQuality"]=>  string(2) "90"
  ["denyZipDownload"]=>  string(1) "0"
  ["denyExtensionRename"]=>  string(1) "0"
  ["showHiddenFiles"]=>  string(1) "0"
  ["docid_incrmnt_method"]=>  string(1) "0"
  ["make_folders"]=>  string(1) "1"
  ["tree_page_click"]=>  string(2) "27"
  ["clean_uploaded_filename"]=>  string(1) "1"
  ["site_id"]=>  string(13) "58f7b74c2db76"
  ["site_unavailable_page"]=>  string(0) ""
  ["reload_site_unavailable"]=>  string(0) ""
  ["siteunavailable_message_default"]=>  string(63) "В настоящее время сайт недоступен."
  ["aliaslistingfolder"]=>  string(1) "0"
  ["check_files_onlogin"]=>  string(72) "index.php
.htaccess
manager/index.php
manager/includes/config.inc.php"
  ["error_reporting"]=>  string(1) "1"
  ["send_errormail"]=>  string(1) "3"
  ["pwd_hash_algo"]=>  string(7) "UNCRYPT"
  ["reload_captcha_words"]=>  string(0) ""
  ["captcha_words_default"]=>  string(379) "MODX,Access,Better,BitCode,Chunk,Cache,Desc,Design,Excell,Enjoy,URLs,TechView,Gerald,Griff,Humphrey,Holiday,Intel,Integration,Joystick,Join(),Oscope,Genetic,Light,Likeness,Marit,Maaike,Niche,Netherlands,Ordinance,Oscillo,Parser,Phusion,Query,Question,Regalia,Righteous,Snippet,Sentinel,Template,Thespian,Unity,Enterprise,Verily,Tattoo,Veri,Website,WideWeb,Yap,Yellow,Zebra,Zygote"
  ["smtp_secure"]=>  string(4) "none"
  ["reload_emailsubject"]=>  string(0) ""
  ["emailsubject_default"]=>  string(42) "Дані для авторизації"
  ["reload_signupemail_message"]=>  string(0) ""
  ["signupemail_message"]=>  string(450) "Добрий день, !

Ваші дані для авторизації у системі керування сайтом :

Ім'я користувача: 
Пароль: 

Після успішної авторизації у системі керування сайтом (), ви зможете змінити свій пароль.

З повагою, Адміністрація"
  ["system_email_signup_default"]=>
  string(450) "Добрий день, !

Ваші дані для авторизації у системі керування сайтом :

Ім'я користувача: 
Пароль: 

Після успішної авторизації у системі керування сайтом (), ви зможете змінити свій пароль.

З повагою, Адміністрація"
  ["reload_websignupemail_message"]=>  string(0) ""
  ["websignupemail_message"]=>  string(366) "Добрий день,, !

Ваші дані для авторизації на :

Ім'я користувача: 
Пароль: 

Після успішної авторизації у системі керування сайтом (), ви зможете змінити свій пароль.

З повагою, Адміністрація"
  ["system_email_websignup_default"]=>  string(366) "Добрий день, !

Ваші дані для авторизації на :

Ім'я користувача: 
Пароль: 

Після успішної авторизації у системі керування сайтом (), ви зможете змінити свій пароль.

З повагою, Адміністрація"
  ["reload_system_email_webreminder_message"]=>  string(0) ""
  ["webpwdreminder_message"]=>  string(490) "Добрий день, !

Щоб активувати ваш новий пароль, перейдіть за наступним посиланням :



Пізніше ви зможете викоритовувати наступинй пароль для авторизації: 

Якщо цей лист прийшов до вас по помилці, будь ласка, проігноруйте його.

З повагою, Адміністрація"
  ["system_email_webreminder_default"]=>  string(490) "Добрий день, !

Щоб активувати ваш новий пароль, перейдіть за наступним посиланням :



Пізніше ви зможете викоритовувати наступний пароль для авторизації: 

Якщо цей лист прийшов до вас через помилку, будь ласка, проігноруйте його.

З повагою, Адміністрація"
  ["resource_tree_node_name"]=>  string(9) "pagetitle"
  ["mce_editor_skin"]=>  string(7) "cirkuit"
  ["mce_template_docs"]=>  string(0) ""
  ["mce_template_chunks"]=>  string(0) ""
  ["mce_entermode"]=>  string(1) "p"
  ["mce_element_format"]=>  string(5) "xhtml"
  ["mce_schema"]=>
  string(5) "html4"
  ["tinymce_custom_buttons3"]=>  string(0) ""
  ["tinymce_custom_buttons4"]=>  string(0) ""
  ["tinymce_css_selectors"]=>  string(35) "left=justifyleft;right=justifyright"
  ["rb_webuser"]=>  string(1) "0"
  ["sys_files_checksum"]=>  string(198) "a:2:{s:48:"/home/site/web/site.ru/public_html/index.php";s:32:"ed8dd02021b28b9227b44d5a76ef7440";s:48:"/home/site/web/site.ru/public_html/.htaccess";s:32:"8e4ef1ec7e19ae4055764166b85cad6f";}"
  ["use_breadcrumbs"]=>  string(1) "1"
  ["tinymce4_theme"]=>  string(8) "advanced"
  ["tinymce4_skin"]=>  string(9) "lightgray"
  ["tinymce4_template_docs"]=>  string(0) ""
  ["tinymce4_template_chunks"]=>  string(0) ""
  ["tinymce4_entermode"]=>  string(1) "p"
  ["tinymce4_element_format"]=>  string(5) "xhtml"
  ["tinymce4_schema"]=>  string(5) "html5"
  ["tinymce4_custom_plugins"]=>  string(328) "advlist autolink lists link image charmap print preview hr anchor pagebreak searchreplace wordcount visualblocks visualchars code fullscreen spellchecker insertdatetime media nonbreaking save table contextmenu directionality emoticons template paste textcolor codesample colorpicker textpattern imagetools paste modxlink youtube"
  ["tinymce4_custom_buttons1"]=>  string(186) "undo redo | cut copy paste | searchreplace | bold italic underline strikethrough | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent blockquote | styleselect"
  ["tinymce4_custom_buttons2"]=>  string(168) "link unlink anchor image media codesample table | hr removeformat | subscript superscript charmap | nonbreaking | visualchars visualblocks print preview fullscreen code"
  ["tinymce4_custom_buttons3"]=>  string(0) ""
  ["tinymce4_custom_buttons4"]=>  string(0) ""
  ["tinymce4_blockFormats"]=>  string(47) "Paragraph=p;Header 1=h1;Header 2=h2;Header 3=h3"
  ["which_browser"]=>  string(5) "mcpuk"
  ["enable_filter"]=>  string(1) "0"
  ["minifyphp_incache"]=>  string(1) "0"
  ["session_timeout"]=>  string(2) "15"
  ["allow_eval"]=>  string(9) "with_scan"
  ["safe_functions_at_eval"]=>  string(28) "time,date,strtotime,strftime"
  ["lang_code"]=>  string(2) "ru"
  ["etomite_charset"]=>  &string(5) "UTF-8"
  ["base_url"]=>  string(1) "/"
  ["base_path"]=>  string(39) "/home/site/web/site.ru/public_html/"
  ["site_url"]=>  string(17) "http://site.ru/"
  ["valid_hostnames"]=>  string(0) ""
  ["site_manager_url"]=>  string(24) "http://site.ru/dostup/"
  ["site_manager_path"]=>  string(46) "/home/site/web/site.ru/public_html/dostup/"
}
````
