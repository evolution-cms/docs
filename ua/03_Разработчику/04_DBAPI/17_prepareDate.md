### Форматування виведення дати

string prepareDate($timestamp, $fieldType)

**$timestamp** - дата в форматі Unix timestamp

**$fieldType** - варіант форматування

+ DATE - формат виду Y-m-d. Приклад: "2007-04-30"
+ TIME - формат виду H:i:s. Приклад: "13:43:27"
+ YEAR - формат виду Y. Приклад: "2007"
+ DATETIME (за замовчуванням) - формат виду Y-m-d H:i:s. Приклад: "2007-04-30 13:43:27"

***

#### Приклад

	function getEvents( $date ) {  
		global $modx;  
		$output = '';  
		$fulldate = $modx->db->prepareDate( $date, 'DATE' );		
		//Перетворює дату в зручний для читання вигляд
		$result = $modx->db->select( 'event_name', 'events', 'timestamp = ' . intval( $date ) );  
		while( $row = $modx->db->getRow( $result ) ) {  
			$output .= $row['event_name'] . ' відбудеться ' . $fulldate . '.';  
		}  
	}