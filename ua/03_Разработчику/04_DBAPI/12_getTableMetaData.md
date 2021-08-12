###Інформація про структуру таблиці

array getTableMetaData($table)

**$table** - назва таблиці

Ця функція повертає багатовимірний масив з докладною інформацією про структуру заданої таблиці MySQL.

Масив має вигляд *TableField => Array( Info => Value )*, де 

+ TableField - назва колонки, 
+ Info - одне з 6 інформаційних параметрів, 
+ Value - значення конкретного параметра.

***

####Інформаційні параметри:

**Field** - назва поля таблиці
**Type** - тип поля і розмір (наприклад int(5), varchar(40) або text)
**Null** - може містити значення NULL
**Key** - містить ключ для значення типу "UNI" (UNIQUE) або "PRI" (PRIMARY)
**Default** - значення за замовчуванням
**Extra** - додаткова інформація, така як використання auto_increment

***

####Приклад

	$table = 'my_table';  
	$data = $modx->db->getTableMetaData( $table );  
	$output = '';   
	
	// Цикл по всіх колонках  
	foreach( $data as $field => $arr ) {	 
	
		// Назва колонки
		$output .= '<b>' . $field . '</b><br />';
		
		// Цикл по всіх інформаційних параметрах
		foreach( $arr as $info => $value )
			$output .= $info . ': ' . $value . '<br />'; // Виведення значення  
		}  
	}
	return $output;