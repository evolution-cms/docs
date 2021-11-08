###Використання PHP в налаштуваннях ManagerManager

####Приклад 1
Створення і виведення доп вкладки в залежності від id документа
	
	if($content['id'] == 4 or $content['id'] == 5){
	
		mm_createTab('Доп. описание', 'dop-params', '', '4', '', '850');
	
		mm_moveFieldsToTab('dop-params', 'dop-params', '', '');
	}else{
	
		mm_hideFields('dop-params', '', '4');
	
	}
	
####Приклад 2
Перевіряємо чи існує ТВ, і тільки якщо є, то запускаємо віджет

	if($modx->db->getValue("SELECT COUNT(id) FROM " . $modx->getFullTableName('site_tmplvars') . " WHERE name='documentTags'")) {
    	
    	mm_widget_tags('documentTags',' ');
    
    }
