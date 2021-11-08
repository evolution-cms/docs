###Результат запиту в форматі XML

string getXML($dsq)

**$dsq** - результат виконання запиту або SQL-запит

####Дані отриманих результатів запиту виводяться в наступному форматі:

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

Кожен запис огортається в тег <item>. "Field#" співпадають з назвами колонок, а "Value#" значенням.

***

####Приклад

	$result = $modx->db->select( 'id, name, location', 'places', '' );  
	$xml = $modx->db->getXML( $result );   
	$output = '<textarea>' . $xml . '</textarea>';   
	return $output;