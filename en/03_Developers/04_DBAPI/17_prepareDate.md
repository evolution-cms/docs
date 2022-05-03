### Date output formatting

string prepareDate($timestamp, $fieldType)

**$timestamp** - date in Unix timestamp format

**$fieldType** - formatting option

+ DATE - Y-m-d format. Example: "2007-04-30"
+ TIME - H:i:s format. Example: "13:43:27"
+ YEAR - Y format. Example: "2007"
+ DATETIME (default) - Y-m-d H:i:s format. Example: "2007-04-30 13:43:27"

***

#### Example
```
function getEvents( $date ) {  
	global $modx;  
	$output = '';  
	$fulldate = $modx->db->prepareDate( $date, 'DATE' );		
	// Converts the date to a readable form
	$result = $modx->db->select( 'event_name', 'events', 'timestamp = ' . intval( $date ) );  
	while( $row = $modx->db->getRow( $result ) ) {  
		$output .= $row['event_name'] . ' состоится ' . $fulldate . '.';  
	}  
}
```
