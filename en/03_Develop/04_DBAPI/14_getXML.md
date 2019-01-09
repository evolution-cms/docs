###Результат запроса в формате XML

string getXML($dsq)

**$dsq** - результат выполнения запроса или SQL-запрос

####Данные полученных результатов запроса выводятся в следующем формате:

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

Каждая запись заключается в тег <item>. "Field#" соответствуют названиям колонок, а "Value#" значениям.

***

####Пример

	$result = $modx->db->select( 'id, name, location', 'places', '' );  
	$xml = $modx->db->getXML( $result );   
	$output = '<textarea>' . $xml . '</textarea>';   
	return $output;