###Отримання запису з результату запиту

array getRow($ds, $mode)

**$ds** - результат виконання запиту
**$mode** - режим роботи

+ assoc - отримання асоціативного масиву
+ num - отримання нумерованного масиву
+ both - отримання масиву поєднуючого асоціативний і нумерований

***

####Приклад

	function getAlbum() {  
		global $modx;  
		$output = '';  
		$table = $modx->getFullTableName( 'albums' );   
		
		$result = $modx->db->select( 'id, album_name, artist', $table, '', 'artist ASC', '0, 50');   
		
		if( $modx->db->getRecordCount( $result ) >= 1 ) {
			$output .= '<ul>';  
			while( $row = $modx->db->getRow( $result ) ) {  
				$output .= '<li>Ідентифікатор: ' . $row['id'] . ' | Альбом: ' . $row['album_name'] . ' | Виконавець: ' . $row['artist'] . '</li>';  
			}  
			$output .= '</ul>';  
		}else{  
			$output = 'Немає відповідних записів.';  
		}  
		
		return $output;  
	}