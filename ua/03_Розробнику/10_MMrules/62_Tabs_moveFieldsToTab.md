###Віджет для плагіна ManagerManager, дозволяє перемістити поля документа і TV в іншу вкладку. 
*На жаль, неможливо перемістити наступні поля: keywords, metatags, which_editor, show_in_menu, menuindex.*

mm_moveFieldsToTab($fields, $tabId, $roles, $templates);

####Опис параметрів
Назва|Опис|Допустимі значення|Значення за замовчуванням|Обов'язковий?
--------|--------|---------|--------|--------
fields|Поля документа (або TV), які необхідно перемістити.|{comma separated string}|—|true
tabId|Id вкладки, в яку необхідно перемістити поля. Можна вказати як id однієї зі стандартних вкладок, так і id вкладки, створеної за допомогою mm_createTab.|{string}|—|true
roles|Ролі, для яких необхідно застосувати віджет, порожнє значення — всі ролі.|{comma separated string}|—|false
templates|Id шаблонів, для яких необхідно застосувати віджет, порожнє значення — всі шаблони.|{comma separated string}|—|false

####Приклади
Перемістити дату публікації та заголовок документа у вкладку «mycats» (попередньо створену за допомогою mm_createTab)
	
	mm_moveFieldsToTab('pub_date,pagetitle', 'mycats');
Перемістити дату публікації документа в основну вкладку для користувачів з id ролі = 2
	
	mm_moveFieldsToTab('pub_date', 'general', '2');
Перемістити TV «tags» у вкладку «mycats»
	
	mm_moveFieldsToTab('tags', 'mycats');
