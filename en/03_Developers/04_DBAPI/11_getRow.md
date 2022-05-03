### Retrieving a record from a query result

array getRow($ds, $mode)

* **$ds** - query result
* **$mode** - operating mode

+ assoc - obtaining an associative array
+ num - obtaining a numbered array
+ both - obtaining an array combining associative and numbered

***

#### Example
```
function getAlbum() {  
	global $modx;  
	$output = '';  
	$table = $modx->getFullTableName( 'albums' );   

	$result = $modx->db->select( 'id, album_name, artist', $table, '', 'artist ASC', '0, 50');   

	if( $modx->db->getRecordCount( $result ) >= 1 ) {
		$output .= '<ul>';  
		while( $row = $modx->db->getRow( $result ) ) {  
			$output .= '<li>Identifier: ' . $row['id'] . ' | Album: ' . $row['album_name'] . ' | Artist: ' . $row['artist'] . '</li>';  
		}  
		$output .= '</ul>';  
	}else{  
		$output = 'No records found.';  
	}  

	return $output;  
}
```
