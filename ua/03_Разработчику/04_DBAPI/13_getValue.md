### Значення першої комірки з першого рядка результату запиту

mixed getValue($dsq)

**$dsq** - результат виконання запиту або SQL-запит

Ця функція повертає перше значення з першої колонки в результаті запиту.
Завдяки цьому можна швидко отримати єдине передбачуване значення (наприклад, результат запиту SELECT COUNT(*)).

***

#### Приклад
```
function display_rows() {
	$modx = evolutionCMS();
	$count = $modx->db->getValue( $modx->db->select( 'count(*)', 'people' ) );
	if( $count < 1 ) {
		return 'No records found';
	} else {
		return 'Знайдено ' . $count . ' записів в базі.';
	}
}
```
