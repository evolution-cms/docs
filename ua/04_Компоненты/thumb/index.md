
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Простая реализация phpThumb генератора на основе единственного tv и заданных параметров. </h3>
Простая реализация phpThumb генератора на основе единственного tv и заданных параметров.
//Проста реалізація phpThumb генератора на основі одного tv и заданих параметрів.

<p>Казалось бы, типовая задача, заполнить каталог изображений, подготовить для каждого несколько размеров и наложить произвольные фильтры, однако не нахожу в <span class="text-bold">modx</span> подходящего, простого и удобного инструмента.</p>
//Здаавалося, типова задача, заповнити каталог зображень, підготувати для кожного декілька розмірів і накласти довільні фільтри, але я не можу знайти в modx потрібного, //простого і зручного інструмента.

<p>Простая реализация phpThumb генератора на основе единственного tv и заданных параметров.</p>
//Проста реалізація phpThumb генератора на основі одного tv и заданих параметрів.

<h3 class="sub-header text-bold">Пример вызова</h3>
//Приклад виклика
<pre class="brush: php;">
[!thumb? &path=`[+thumb+]` &size=`320x240` &tpl=`thumb`!]
</pre>
<p>Исходное изображение задается переменной шаблона <i>[+thumb+]</i>. Сниппет [[thumb]] из имени исходного файла (например image.jpg) и параметров (320x240) формирует единое имя нового файла (image.320x240.jpg). При обращении к каталогу картинок, в соответсвии с правилом <i>RewriteRule</i> apache перенаправляет запрос обработчику <i>index.php</i>, который разбивает имя файла обратно на параметры и при помощи phpThumb формирует требуемое изображение.</p>
//Початкове зображення задається змінною шаблона <i>[+thumb+]</i>. Снипет [[thumb]] зі змінної первинного файла (наприклад image.jpg) і параметрів (320x240) формує єдине //ім'я нового файла (image.320x240.jpg). При зверненні до каталогу картинок, згідно з правилом <i>RewriteRule</i> apache перенаправляє запит обробнику <i>index.php</i>, //який розбиває ім'я файла назад на параметри і за допомогою phpThumb формує потрібне зображення.

<p><span class="text-bold">Сниппет <i>[[thumb]]</i></span></p>
//Сніпет
<p>Принимает один обязательный и два опциональных параметра</p>
//Приймає один обов'язковий і два опціональних параметра
<p><i>path</i> путь к файлу картинки</p>
//<i>path</i> шлях до файла картинок
<p><i>[size]</i> размер генерируемой картинки</p>
//<i>[size]</i> розмір картинки, що генерується
<p><i>[tpl]</i> шаблон офромления</p>
//<i>[tpl]</i> шаблон оформлення
<p>В зависимости от шаблона, сниппет либо возвращает оформленный в соответствии с шаблоном результат, либо строку с итоговым путем <i>path</i></p>
//Залежно від шаблона, сніпет або повертає оформлений згідно з шаблоном результат, або рядок з кінцевим шляхом <i>path</i>
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
//Чанк
Принимает один едиственный плейсхолдер <i>[+path+]</i></p>
//Приймає лише єдиний плейсхолдер <i>[+path+]</i>
<pre class="brush: php;">
&lt;img src="[+path+]"&gt;
</pre>

<p><span class="text-bold">Обработчик запросов <i>index.php</i></span></p>
//Обробник запитів <i>index.php</i>
<p>Принимает адрес изображения, разбивает адрес на аргументы и в соответствии с заданными параметрами генерирует и возвращает результат.</p>
//Приймає адресу зображення, розбиває адресу на аргументи і відповідно до заданих параметрів генерує і повертає результат.
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
//Правило перенаправлення apache <i>.htaccess</i>
<p>Запускает процедуру обработки изображения</p>
//Запускає процедуру обробки зображення
<pre class="brush: php;">
&lt;IfModule mod_rewrite.c&gt;
	RewriteEngine on
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d
	RewriteRule ^(.*)$ index.php?path=$1 [L,QSA]
&lt;/IfModule&gt;
</pre>
