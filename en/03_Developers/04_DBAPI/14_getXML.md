### Query result in XML format

string getXML($dsq)

* **$dsq** - query result or SQL query

#### Data of received query results are displayed in the following format:
```
<xml>  
	<recordset>  
		<item>  
			<field1>Value1</field1>  
			<field2>Value2</field2>  
			<field3>Value3</field3>  
		</item>  
		<item>  
			<field1>Value1</field1>  
			<field2>Value2</field2>  
			<field3>Value3</field3>  
		</item>  
	</recordset>  
</xml>
```
Each entry is enclosed in an <item> tag. "Field#" corresponds to column names, and "Value#" to values.

***

#### Example
```
$result = $modx->db->select( 'id, name, location', 'places', '' );  
$xml = $modx->db->getXML( $result );   
$output = '<textarea>' . $xml . '</textarea>';   
return $output;
```
