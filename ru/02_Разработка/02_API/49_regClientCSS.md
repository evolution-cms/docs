###Подключение файла стилей CSS к документу или блока ‹style› в область ‹head›

*Замечание: метод имеет проверку на дублирование подключения.*

void regClientCSS(string $src[, string $media]);

**$src** - путь до файла стилей CSS

**$media** - определение параметра media для подключаемой таблицы стилей
screen
print
По умолчанию: пусто

***

####Пример

	$myCSS = '<style media="screen">* { margin:0; padding:0 }</style>'; 
	$modx->regClientCSS( $myCSS );