###Виджет для плагина ManagerManager, позволяющий переместить поля документа и TV в другую вкладку. 
*К сожалению, невозможно переместить следующие поля: keywords, metatags, which_editor, show_in_menu, menuindex.*

mm_moveFieldsToTab($fields, $tabId, $roles, $templates);

####Описание параметров
Название|Описание|Допустимые значения|Значение по умолчанию|Обязателен?
--------|--------|---------|--------|--------
fields|Поля документа (или TV), которые необходимо переместить.|{comma separated string}|—|true
tabId|Id вкладки, в которую необходимо переместить поля. Можно указать как id одной из стандартных вкладок, так и id вкладки, созданной при помощи mm_createTab.|{string}|—|true
roles|Роли, для которых необходимо применить виждет, пустое значение — все роли.|{comma separated string}|—|false
templates|Id шаблонов, для которых необходимо применить виджет, пустое значение — все шаблоны.|{comma separated string}|—|false

####Примеры
Переместить дату публикации и заголовок документа во вкладку «mycats» (предварительно созданную при помощи mm_createTab)
	
	mm_moveFieldsToTab('pub_date,pagetitle', 'mycats');
Переместить дату публикации документа в основную вкладку для пользователей с id роли = 2
	
	mm_moveFieldsToTab('pub_date', 'general', '2');
Переместить TV «tags» во вкладку «mycats»
	
	mm_moveFieldsToTab('tags', 'mycats');