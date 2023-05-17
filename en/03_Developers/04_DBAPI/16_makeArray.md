###Query result as an array

mixed makeArray( $rs )

**$rs** - query result

This method returns a multidimensional associative array with query result data in the format Key => Array( FieldName => Value ).
***

#### Example
```
function show_members() {  
	global $modx;  
	$output = '';  
	$table = $modx->getFullTableName( 'members' );   

	$result = $modx->db->select( 'id, name, picture', $table, '', 'name ASC', '' );
	$members = $modx->db->makeArray( $result );   
	foreach( $members as $p_val ) {  
		foreach( $p_val as $m_key => $m_val ) {  
			$output .= '<strong>' . $m_key . ':</strong> ' . $m_val . '<br />';  
		}  
	}  
}
```
