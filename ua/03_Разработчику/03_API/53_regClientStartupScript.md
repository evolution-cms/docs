### Підключення JavaScript до документу або блоку ‹script› в область ‹head›

string regClientStartupScript(string $src[, bool $plaintext]);

**$src** - шлях до файла JavaScript.

**$plaintext** - потрібно розмістити в вигляді тексту, переданого в $src.
true - розміщення в вигляді тексту.
false - розміщення в вигляді зовнішнього файлу або блоку **script**
За замовчуванням: false.

***

#### Приклад 1.

	$src = "assets/js/prototype.js"; $modx->regClientStartupScript($src);
	Це додасть в документ наступний запис:

	<script type="text/javascript" url="assets/js/prototype.js"></script>

#### Приклад 2.
Так само можна розмістити блок із готовим скриптом:

	$src2 = "<script type='text/javascript'>
				function getHTML() { 
					var url = 'testing.php'; 
					var pars = 'return=test'; 
					var myAjax = new Ajax.Updater( {success: 'placeholder'}, url, {method: 'get', parameters: pars}); 
				} 
	</script>"; 
	
	$modx->regClientStartupScript($src2);
	//Буде виведений ідентичний блок.