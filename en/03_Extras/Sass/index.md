
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Sass плагин для Sass плагин для MODX</h3>
Удобный инструмент для верстки, создание и понимание работы плагинов в MODx.
<p><i>Начинающим: удобный инструмент для верстки, создание и понимание работы плагинов в MODX.</i></p>
<h3 class="sub-header text-bold">Sass – правильный CSS</h3>
<p>Многое (если не всё), чего не хватало старому доброму CSS (вплоть до CSS3), реализовано в расширенном формате написания каскадных таблиц стилей – <a href="http://ru.wikipedia.org/wiki/Sass" target="_blank">Sass</a>. Не зря приверженцы Ruby on Rails (откуда берет корни Sass) ласково называют его «синтаксический сахар».</p>
<p>После того, как попробуешь Sass «на вкус», становится трудно отмахнуться от идеи ввести его в боевой арсенал каждого верстальщика. Ведь до чего удобно, например, задать в <i>$переменных</i> значения цветов корпоративной гаммы заказчика, чтобы, если тому вдруг понадобится, с еще большей легкостью «сделать сайт более зеленым»!</p>
<h3 class="sub-header text-bold">Не отстаем от тенденций современности</h3>
<p>Для тех, кто программирует на PHP в условиях CMS MODX, предлагается создать плагин, который будет следить за наличием и изменениями в <i>sass-файлах</i> и автоматически (ре)генерировать соответствующие <i>css-файлы</i>, подключаемые в шаблоне.</p>
<h3 class="sub-header text-bold">Пользуемся поиском: «php sass parser»</h3>
<p>Одна из реализаций нужного нам функционала есть в недрах библиотеки <a href="http://code.google.com/p/phamlp/">phamlp</a>. В составе phamlp присутствует и другая «Ruby-сладость» – haml (чудесная замена для HTML), но это история на перспективу.</p>
<h3 class="sub-header text-bold">Плагин для MODX</h3> 
<p>Несколько простых шагов:</p>
<p>1. <a href="http://code.google.com/p/phamlp/downloads/detail?name=PHamlP_3.2.zip&amp;can=2&amp;q=">Скачиваем архив с библиотекой phamlp</a></p>
<p>2. Архив распаковываем в «assets/plugins/phamlp» (можно без папки haml)</p>
<p>2. В «Элементах» создаем новый плагин «SASS»</p>
<p>4. Копируем и вставляем код плагина:</p>
<pre class="brush: php;">
// директория со стилями (в конце слэш обязательно)
$style_dir = MODX_BASE_PATH.'assets/css/'; 

// сканирование содержимого
$files = scandir(rtrim($style_dir,'/'));

// выбор файлов с расширением sass
foreach ($files as $sass_file)
if (is_file($style_dir.$sass_file) && (strtolower(pathinfo($style_dir.$sass_file,PATHINFO_EXTENSION))=='sass')) {
	// вычисление проверочного md5 хэша содержимого .sass файла
	$sass_hash = hash('md5',file_get_contents($style_dir.$sass_file));

	// при отсутствии записанного (в .sasshash файл) хэша или его несовпадении с записанным - генерация css
	if (!file_exists($style_dir.$sass_file.'hash')||($sass_hash!=file_get_contents($style_dir.$sass_file.'hash'))) {
		// подключение библиотеки phamlp
		include_once(MODX_BASE_PATH.'assets/plugins/phamlp/sass/SassParser.php');

		// инициализация и настройка класса работы с sass форматом 
		$sass = new SassParser(
			array(
				'cache'=>false,
				'style'=>'expanded',
				'vendor_properties'=>array(
					'border-radius' => array(
						'-moz-border-radius',
						'-webkit-border-radius',
						'-khtml-border-radius'
					),
						'border-top-right-radius' => array(
						'-moz-border-radius-topright',
						'-webkit-border-top-right-radius',
						'-khtml-border-top-right-radius'
					),
					'border-bottom-right-radius' => array(
						'-moz-border-radius-bottomright', 
						'-webkit-border-bottom-right-radius',
						'-khtml-border-bottom-right-radius'
					),
					'border-bottom-left-radius' => array(
						'-moz-border-radius-bottomleft',
						'-webkit-border-bottom-left-radius',
						'-khtml-border-bottom-left-radius'
					),
					'border-top-left-radius' => array(
						'-moz-border-radius-topleft',
						'-webkit-border-top-left-radius',
						'-khtml-border-top-left-radius'
					),
					'box-shadow' => array('-moz-box-shadow', '-webkit-box-shadow'),
					'box-sizing' => array('-moz-box-sizing', '-webkit-box-sizing'),
					'opacity' => array('-moz-opacity', '-webkit-opacity', '-khtml-opacity'),
				)
			)
		);

		// генерация css файла 
		file_put_contents( $style_dir.substr($sass_file,0,-4).'css', $sass->toCss($style_dir.$sass_file) );

		// запись хэша
		file_put_contents( $style_dir.$sass_file.'hash', $sass_hash );
	}
}
</pre>
<p>5. На вкладке «Системные события» ставим галочку напротив OnWebPageInit. Это означает запуск кода плагина во время инициализации веб-страницы (проще говоря – каждый раз, когда кто-либо загружает любую из страниц сайта). С тем же успехом можно использовать и другие события MODX, происходящие в это время (OnWebPagePrerender, OnParseDocument).</p>
<p>6. Сохраняем плагин</p>
<h3 class="sub-header text-bold">Работаем со стилями в Sass-формате</h3>
<p>Конечно, для этого подойдет даже штатный веб-редактор MODX (или загрузка по FTP файлов, созданных в Блокноте), но если уж расширять инструментарий веб-разработки, то лучше открыть для себя возможности одной из интегрированных сред разработки (IDE) с мощным набором встроенных средств (FTP-менеджер, подсветка синтаксиса, управление версиями и т.п.).</p>
<p>В директории «assets/css» (как указано в переменной $style_dir) создаем файл с расширением .sass. Для начала, в этом файле можно сохранить <a href="http://ru.wikipedia.org/wiki/Sass" target="_blank">примеры из википедии</a>.</p>
<p>Открываем сайт в браузере или обновляем открытую страницу. В момент возникновения события OnWebPageInit запустится плагин «SASS», который при сканировании обнаружит свежий sass-файл, и сгенерирует его css-версию, которая с этого момента доступна для загрузки в браузеры пользователей со всего мира.</p>
<p>После окончания работы над стилевым оформлением сайта, плагин можно отключить, чтобы не совершал холостых сканирований.</p>
<p><span class="text-bold">UPD: MODX</span> Evo и MODX Revo имеют одинаковые принципы создания плагинов и названия указанных системных событий.</p>