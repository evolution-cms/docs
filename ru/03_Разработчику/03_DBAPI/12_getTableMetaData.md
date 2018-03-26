###Информация о структуре таблицы

array getTableMetaData($table)

**$table** - название таблицы

Эта функция возвращает многомерный массив с подробной информацией о структуре заданной таблицы MySQL.

Массив имеет вид *TableField => Array( Info => Value )*, где 

+ TableField - название колонки, 
+ Info - одно из 6 информационных параметров, 
+ Value - значение конкретного параметра.

***

####Информационные параметры:

**Field** - название поля таблицы
**Type** - тип поля и размер (например int(5), varchar(40) или text)
**Null** - может содержать значение NULL
**Key** - содержит ключ для значения типа "UNI" (UNIQUE) или "PRI" (PRIMARY)
**Default** - значение по умолчанию
**Extra** - дополнительная информация, такая как использование auto_increment

***

####Пример

	$table = 'my_table';  
	$data = $modx->db->getTableMetaData( $table );  
	$output = '';   
	
	// Цикл по всем колонкам  
	foreach( $data as $field => $arr ) {	 
	
		// Название колонки 
		$output .= '<b>' . $field . '</b><br />';
		
		// Цикл по всем информационным параметрам
		foreach( $arr as $info => $value )
			$output .= $info . ': ' . $value . '<br />'; // Вывод значения  
		}  
	}
	return $output;