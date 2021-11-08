###Підключення файлу стилів CSS до документа або блоку <style> в область <head>

*Зауваження: метод має перевірку на дублювання підключення.*

void regClientCSS(string $src[, string $media]);

**$src** - шлях до файлу стилів CSS

**$media** - визначення параметра media для підключеної таблиці стилів
screen
print
За замовчуванням: порожньо

***

####Приклад

	$myCSS = '<style media="screen">* { margin:0; padding:0 }</style>'; 
	$modx->regClientCSS( $myCSS );
