###Использование PHP в настройках ManagerManager

####Пример 1
Создание и вывод доп вкладки в зависимости от id документа
	
	if($content['id'] == 4 or $content['id'] == 5){
	
		mm_createTab('Доп. описание', 'dop-params', '', '4', '', '850');
	
		mm_moveFieldsToTab('dop-params', 'dop-params', '', '');
	}else{
	
		mm_hideFields('dop-params', '', '4');
	
	}
	
####Пример 2
Проверяем существует ли ТВ, и только если есть то запускаем виджет

	if($modx->db->getValue("SELECT COUNT(id) FROM " . $modx->getFullTableName('site_tmplvars') . " WHERE name='documentTags'")) {
    	
    	mm_widget_tags('documentTags',' ');
    
    }
