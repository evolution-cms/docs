
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>thumb</h2>

<p>Казалось бы, типовая задача, заполнить каталог изображений, подготовить для каждого несколько размеров и наложить произвольные фильтры, однако не нахожу в <span class="text-bold">modx</span> подходящего, простого и удобного инструмента.</p>
<p>Простая реализация phpThumb генератора на основе единственного tv и заданных параметров.</p>
<h3 class="sub-header text-bold">Пример вызова</h3>
<pre class="brush: php;">
[!thumb? &path=`[+thumb+]` &size=`320x240` &tpl=`thumb`!]
</pre>
<p>Исходное изображение задается переменной шаблона <i>[+thumb+]</i>. Сниппет [[thumb]] из имени исходного файла (например image.jpg) и параметров (320x240) формирует единое имя нового файла (image.320x240.jpg). При обращении к каталогу картинок, в соответсвии с правилом <i>RewriteRule</i> apache перенаправляет запрос обработчику <i>index.php</i>, который разбивает имя файла обратно на параметры и при помощи phpThumb формирует требуемое изображение.</p>
<p><span class="text-bold">Сниппет <i>[[thumb]]</i></span></p>
<p>Принимает один обязательный и два опциональных параметра</p>
<p><i>path</i> путь к файлу картинки</p>
<p><i>[size]</i> размер генерируемой картинки</p>
<p><i>[tpl]</i> шаблон офромления</p>
<p>В зависимости от шаблона, сниппет либо возвращает оформленный в соответствии с шаблоном результат, либо строку с итоговым путем <i>path</i></p>
<pre class="brush: php;">
&lt;?php
if (!empty($path)) {
	$size = (empty($size)) ? $size : '320x240';

	$path = explode('.', $path);
	array_splice($path, -1, 0, $size);
	$output = $path = implode('.', $path);

	if (!empty($tpl)) {
		$params['path'] = $path;
		$output = $modx->parseChunk($tpl, $params, '[+', '+]');
	}
}
return $output;
?>
</pre>
<p><span class="text-bold">Чанк <i></i></span><br>
Принимает один едиственный плейсхолдер <i>[+path+]</i></p>
<pre class="brush: php;">
&lt;img src="[+path+]"&gt;
</pre>
<p><span class="text-bold">Обработчик запросов <i>index.php</i></span></p>
<p>Принимает адрес изображения, разбивает адрес на аргументы и в соответствии с заданными параметрами генерирует и возвращает результат.</p>
<pre class="brush: php;">
&lt;?php
if (!empty($_GET['path'])) {
	if (!file_exists($path = $_GET['path'])) {
		$image = explode('.', $path);
		$size = end(array_splice($image, -2, 1));
		if (in_array($size, array('100x50', '200x100', '300x150'))) {
			$image = implode('.', $image);
			if (file_exists($image)) {
				list($width, $height) = explode('x', $size);
				require('phpthumb.class.php');
				$phpThumb = new phpThumb();
				$phpThumb->setSourceFilename($image);
				$phpThumb->setParameter('w', $width);
				$phpThumb->setParameter('h', $height);
				$phpThumb->setParameter('zc', '1');
				$phpThumb->setParameter('q', '100');

				if ($phpThumb->GenerateThumbnail()) {
					if ($phpThumb->RenderToFile($path)) {
						return header('Location: '.$path);
					}
				}
			}
		}
	}
}
return header("HTTP/1.0 404 Not Found");
?>
</pre>
<p><span class="text-bold">Правило перенаправления apache <i>.htaccess</i></span></p>
<p>Запускает процедуру обработки изображения</p>
<pre class="brush: php;">
&lt;IfModule mod_rewrite.c&gt;
	RewriteEngine on
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteRule ^(.*)$ index.php?path=$1 [L,QSA]
&lt;/IfModule&gt;
</pre>