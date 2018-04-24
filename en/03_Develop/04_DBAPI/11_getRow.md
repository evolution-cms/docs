###Получение записи из результата запроса

array getRow($ds, $mode)

**$ds** - результат выполнения запроса
**$mode** - режим работы

+ assoc - получение ассоциативного массива
+ num - получение нумерованного массива
+ both - получение массива совмещающего ассоциативного и нумерованный

***

####Пример

	function getAlbum() {  
		global $modx;  
		$output = '';  
		$table = $modx->getFullTableName( 'albums' );   
		
		$result = $modx->db->select( 'id, album_name, artist', $table, '', 'artist ASC', '0, 50');   
		
		if( $modx->db->getRecordCount( $result ) >= 1 ) {
			$output .= '<ul>';  
			while( $row = $modx->db->getRow( $result ) ) {  
				$output .= '<li>Идентификатор: ' . $row['id'] . ' | Альбом: ' . $row['album_name'] . ' | Исполнитель: ' . $row['artist'] . '</li>';  
			}  
			$output .= '</ul>';  
		}else{  
			$output = 'Не подходящих записей.';  
		}  
		
		return $output;  
	}