### Додавання запису

mixed insert($fields, $intotable [, $fromfields [, $fromtable [, $where [, $limit ]]]])

**$fields** - асоціативний масив доданих значень, з назвою поля у вигляді ключа

**$intotable**- таблиця для додавання

**$fromfields** - список полів використовуваних для імпорту з іншої таблиці

**$fromtable** - таблиця використовується для імпорту

**$where** - умова для запиту даних з таблиці для імпорту

**$limit** - обмеження кількості записів для імпорту

Метод INSERT дозволяє додавати нові записи в базу даних. Значення передаються у вигляді асоціативного масиву $fields, формат якого field => value. Ключ "field" вказує на назву колонки, а "value" - додане значення.

Параметри $fromfields, $fromtable, $where и $limit використовуються для копіювання даних з однієї таблиці в іншу.

Цей метод повертає AUTO_INCREMENT-ідентифікатор для доданої записи.

***

#### Приклад

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