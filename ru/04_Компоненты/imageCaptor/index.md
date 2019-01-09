
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Плагин для Modx Evo который копирует фотографии со сторонних сайтов </h3>
Небольшой плагин для Modx Evo который позволяет автоматически при сохранении ресурса копировать фотографии со сторонних сайтов.
<p>Каждому веб-мастеру приходилось когда-либо забирать контент с чужих сайтов обычным копипастом. И если с текстом проблем нет, то, вот, когда там присутствуют фотографии приходится тратить наше бесценное время на ненужные действия. Сначала мы по каждой фотографии кликаем правой кнопочкой, сохраняем в отдельную папочку картинку, потом заливаем на сервер, а потом для каждой картинки прописываем новый путь. Это может и не так сложно если мы копируем 1-2 фотографии. А если мы имеем дело с сотней страниц где на каждой по десяток фотографий? Можно конечно не заморачиваться, и оставить ссылки на сторонние сайты, но это уж совсем дурной тон.</p>
<p>Алексей Либер написал небольшой плагин для Modx Evo который позволяет автоматически при сохранении ресурса копировать фотографии со сторонних сайтов к себе на сервер и соответственно перезаписывать к ним пути.</p>
<p>Создаем плагин с названием например: <span class="text-bold">imageCaptor</span>.</p>
<p>Системные события: <code>OnDocFormSave</code></p>
<pre class="brush: php;">
/*
Captor 1.0a - Забираем автоматом контент с чужих сайтов
Событие в плагинах - OnBeforeDocFormSave
*/

if(!defined('MODX_BASE_PATH')){die('Ты кто такой? Давай, до свидания!');}
global $tmplvars,$content;
define('ROOT', $modx->config['base_path']);
define('EX', 'jpg,png,gif,jpeg,doc,xls,zip,pdf'); // Через запятую имена расширений (нижний регистр)
$folder=isset($folder) ? $folder : "assets/images/captor/"; // папка назначения стыренного контента
if(!is_dir(MODX_BASE_PATH.$folder)) mkdir(MODX_BASE_PATH.$folder);
// Функция траслита
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
    // переводим в транслит
    $str = rus2translit($str);
    // в нижний регистр
    $str = strtolower($str);
    // заменям все ненужное нам на "-"
    $str = preg_replace('~[^-a-z0-9_]+~u', '-', $str);
    // удаляем начальные и конечные '-'
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
	//Заветная регулярка
	preg_match_all('#(?<!\])\bhttp://[^\s\[<]+\b#i', $value, $matches);
	foreach ($matches[0] as $srcOrig){
		$src =  urldecode($srcOrig);
		$info = pathinfo($src); 
		if (in_array(mb_strtolower($info['extension']),explode(',',EX))){
			// Операции по копированию
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
// Забираем фотки из контентной части
$content = captor($content,$folder);

//Забираем фотки из ТВшек. Был какой-то глюк, нужно проверить
foreach($tmplvars as $key => $val){
	if ($val[1]) $tmplvars[$key][1] = captor($val[1],$folder);
}
</pre>
