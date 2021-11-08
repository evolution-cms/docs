###Створює список по переданому масиву з урахуванням вкладеності

string makeList(int $array[, string $ulroot[, string $ulprefix[, string $type[, bool $ordered[, int $tablevel]]]]]);

**$array** - масив значень для списку

**$ulroot** - назва класу для основного контейнера списку
за замовчуванням: root

**$ulprefix** - префікс для вкладених контейнерів списку
за замовчуванням: sub_

**$type** - тип списку по CSS (буде додано параметр: style = 'list-style-type: $ type')
за замовчуванням: не вказано

**$ordered** - список є нумерованим
true - нумерований список
false - ненумерований список
за замовчуванням: false

**$tablevel** - визначає кількість табів для відступу в HTML-документі.

***

####Приклад

	$txt = $modx->makeList(array(0 => 15,16, 15 => array(12,17)));
	
	//Поверне:
	<ul class='root'> 
		<li>15</li> 
		<li>16</li> 
		<li>15 
			<ul class='sub_root'> 
				<li>12</li> 
				<li>17</li> 
			</ul>
		</li> 
	</ul>
