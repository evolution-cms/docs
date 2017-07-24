###Значение первой колонки из результата запроса

mixed getValue($dsq)

**$dsq** - результат выполнения запроса или SQL-запрос

Эта функция возвращает первое значение из первой колонки в результате запроса. Благодаря этому можно быстро получить единственное предполагаемое значение (например, результат запроса SELECT COUNT(*)).

***

####Пример

	function display_rows() {  
		global $modx;  
		$count = $modx->db->getValue( $modx->db->select( 'count(*)', 'people' ) );   		if( $count < 1 ) {  
			return 'No records found';  
		}else{  
			return 'Найдено ' . $count . ' записей в базе.';  
		}  
	}