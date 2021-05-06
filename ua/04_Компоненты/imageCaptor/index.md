
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Плагін для Modx Evo який копіює фотографії зі сторонніх сайтів </h3>
Невеликий плагін для Modx Evo який дозволяє автоматично при збереженні ресурсу копіювати фотографії зі сторонніх сайтів.
<p>Кожному веб-майстру доводилося коли-небудь забирати контент з чужих сайтів звичайним копіпастом. І якщо з текстом проблем немає, то, ось, коли там присутні фотографії доводиться витрачати наш безцінний час на непотрібні дії. Спочатку ми по кожній фотографії натискаємо правою кнопочкою, зберігаємо в окрему папочку картинку, потім заливаємо на сервер, а потім для кожної картинки прописуємо новий шлях. Це може і не так складно якщо ми копіюємо 1-2 фотографії. А якщо ми маємо справу з сотнею сторінок де на кожній по десяток фотографій? Можна звичайно не морочитися, і залишити посилання на сторонні сайти, але це вже зовсім поганий тон.</p>
<p>Олексій Лібер написав невеликий плагін для Modx Evo який дозволяє автоматично при збереженні ресурсу копіювати фотографії зі сторонніх сайтів до себе на сервер і відповідно перезаписувати до них шляхи.</p>
<p>Створюємо плагін з назвою наприклад: <span class="text-bold">imageCaptor</span>.</p>
<p>Системні події: <code>OnDocFormSave</code></p>
<pre class="brush: php;">
/*
Captor 1.0a - Забираємо автоматом контент з чужих сайтів
Подія в плагінах - OnBeforeDocFormSave
*/

if(!defined('MODX_BASE_PATH')){die('Ти хто такий? Давай, до побачення!');}
global $tmplvars,$content;
define('ROOT', $modx->config['base_path']);
define('EX', 'jpg,png,gif,jpeg,doc,xls,zip,pdf'); // Через кому імена розширень (нижній регістр)
$folder=isset($folder) ? $folder : "assets/images/captor/"; // папка призначення стиреного контенту
if(!is_dir(MODX_BASE_PATH.$folder)) mkdir(MODX_BASE_PATH.$folder);
// функція трасліта
function rus2translit($string) {
    $converter = array(
        'а' => 'a',   'б' => 'b',   'в' => 'v',
        'г' => 'g',   'д' => 'd',   'е' => 'e',
        'ё' => 'e',   'ж' => 'zh',  'з' => 'z',
        'и' => 'i',   'й' => 'y',   'к' => 'k',
        'л' => 'l',   'м' => 'm',   'н' => 'n',
        'о' => 'o',   'п' => 'p',   'р' => 'r',
        'с' => 's',   'т' => 't',   'у' => 'u',
        'ф' => 'f',   'х' => 'h',   'ц' => 'c',
        'ч' => 'ch',  'ш' => 'sh',  'щ' => 'sch',
        'ь' => '\'',  'ы' => 'y',   'ъ' => '\'',
        'э' => 'e',   'ю' => 'yu',  'я' => 'ya',
        
        'А' => 'A',   'Б' => 'B',   'В' => 'V',
        'Г' => 'G',   'Д' => 'D',   'Е' => 'E',
        'Ё' => 'E',   'Ж' => 'Zh',  'З' => 'Z',
        'И' => 'I',   'Й' => 'Y',   'К' => 'K',
        'Л' => 'L',   'М' => 'M',   'Н' => 'N',
        'О' => 'O',   'П' => 'P',   'Р' => 'R',
        'С' => 'S',   'Т' => 'T',   'У' => 'U',
        'Ф' => 'F',   'Х' => 'H',   'Ц' => 'C',
        'Ч' => 'Ch',  'Ш' => 'Sh',  'Щ' => 'Sch',
        'Ь' => '\'',  'Ы' => 'Y',   'Ъ' => '\'',
        'Э' => 'E',   'Ю' => 'Yu',  'Я' => 'Ya',
    );
    return strtr($string, $converter);
}
function str2url($str) {
    // переводимо в трансліт
    $str = rus2translit($str);
    // в нижній регістр
    $str = strtolower($str);
    // заміням все непотрібне нам на "-"
    $str = preg_replace('~[^-a-z0-9_]+~u', '-', $str);
    // видаляємо початкові і кінцеві '-'
    $str = trim($str, "-");
    return $str;
}
function clearUrl ($url){
	$pieces = explode("#", $url);
	$url=$pieces[0];
	$pieces = explode("?", $url);
	$url=$pieces[0];
	return end(explode(".", $url));		 
}


function captor($value,$folder){
	//Заповітна регулярка
	preg_match_all('#(?<!\])\bhttp://[^\s\[<]+\b#i', $value, $matches);
	foreach ($matches[0] as $srcOrig){
		$src =  urldecode($srcOrig);
		$info = pathinfo($src); 
		if (in_array(mb_strtolower($info['extension']),explode(',',EX))){
			// Операції по копіюванню
			$filename = @basename($src,'.'.$info['extension']);
			$name = ROOT.''.$folder.''.str2url(trim($filename)).''.mt_rand().'.'.$info['extension'];
			@copy($src,$name);
			$nameArr = explode('/',$name);
			$name = './'.$folder.''.array_pop($nameArr);
			$value = str_replace($srcOrig,$name,$value);				
		}
	}
	return $value;
}
// Забираємо фото з тематичної частини
$content = captor($content,$folder);

//Забираємо фотки з ТВшок. Був якийсь глюк, потрібно перевірити
foreach($tmplvars as $key => $val){
	if ($val[1]) $tmplvars[$key][1] = captor($val[1],$folder);
}
</pre>
