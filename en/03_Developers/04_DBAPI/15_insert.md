###Добавление записи

mixed insert($fields, $intotable [, $fromfields [, $fromtable [, $where [, $limit ]]]])

**$fields** - ассоциативный массив добавляемых значений, с названием поля в виде ключа

**$intotable**- таблица для добавления

**$fromfields** - список полей используемых для импорта из другой таблицы

**$fromtable** - таблица используемая для импорта

**$where** - условие для запроса данных из таблицы для импорта

**$limit** - ограничение количества записей для импорт

Метод INSERT позволяет добавлять новые записи в базу данных. Значения передаются в виде ассоциативного массива $fields, формат которого field => value. Ключ "field" указывает на название колонки, а "value" - добавляемое значение.

Параметры $fromfields, $fromtable, $where и $limit используются для копирования данных из одной таблицы в другую.

Этот метод возвращает AUTO_INCREMENT-идентификатор для добавленной записи.

***

####Пример

	function insert_my_rows( $data = array() ) {  
		global $modx;  
		$table_name = $modx->getFullTableName( 'cars' );  
		$fields = array('name'	=> $data['name'],  
						'color'	=> $data['color'],  
						'make'	=> $data['make'],  
						'model'	=> $data['model'], 
						);   
		$modx->db->insert( $fields, $table_name);  
	}