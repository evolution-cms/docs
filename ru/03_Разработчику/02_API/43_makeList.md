###Создает список по переданному массиву с учетом вложенности

string makeList(int $array[, string $ulroot[, string $ulprefix[, string $type[, bool $ordered[, int $tablevel]]]]]);

**$array** - массив значений для списка

**$ulroot** - название класса для основного контейнера списка
по умолчанию: root

**$ulprefix** - префикс для вложенных контейнеров списка
по умолчанию: sub_

**$type** - тип списка по CSS (будет добавлен параметр: style='list-style-type: $type')
по умолчанию: не указан

**$ordered** - список является нумерованным
true - нумерованный список
false - ненумерованный список
по умолчанию: false

**$tablevel** - определяет количество табов для отступа в HTML-документе.

***

####Пример

	$txt = $modx->makeList(array(0 => 15,16, 15 => array(12,17)));
	
	//Вернет:
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