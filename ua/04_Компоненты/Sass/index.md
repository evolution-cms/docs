
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Sass плагін для Sass плагін для MODX</h3>
Зручний інструмент для верстки, створення і розуміння роботи плагінів в MODx.
<p><i>Починаючим: зручний інструмент для верстки, створення і розуміння роботи плагінів в MODX.</i></p>
<h3 class="sub-header text-bold">Sass – правильний CSS</h3>
<p>Більшість із того (якщо не все), що не вистачало старому доброму CSS (аж до CSS3), реалізовано в розширеному форматі написання каскадних таблиць стилів – <a href="http://ru.wikipedia.org/wiki/Sass" target="_blank">Sass</a>. Недарма прихильники Ruby on Rails (звідки бере корені Sass) ласкаво називають його «синтаксичний цукор».</p>
<p>Після того, як спробуєш Sass «на смак», стає тяжко відмахнутися від идеї ввести його в бойовий арсенал кожного верстальника. Адже до чого ж зручно, наприклад, задати в <i>$змінних</i> значення кольорів корпоративної гами замовника, щоб, якщо йому раптом знадобиться, з ще більшою легкістю «зробити сайт бальш зеленим»!</p>
<h3 class="sub-header text-bold">Не відстаємо від тенденцій сучасності</h3>
<p>Для тих, хто програмує на PHP в умовах CMS MODX, пропонується створити плагін, який буде слідкувати за наявністю і змінами в <i>sass-файлах</i> і автоматично (ре)генерувати відповідні <i>css-файли</i>, які підключаються в шаблоні.</p>
<h3 class="sub-header text-bold">Використовуємо пошук: «php sass parser»</h3>
<p>Одна із реализацій потрібного нам функціонала є в надрах бібліотеки <a href="http://code.google.com/p/phamlp/">phamlp</a>. В складі phamlp присутня й інша «Ruby-цукерка» – haml (чудова заміна для HTML), але це істория на перспективу.</p>
<h3 class="sub-header text-bold">Плагін для MODX</h3> 
<p>Декілька простих кроків:</p>
<p>1. <a href="http://code.google.com/p/phamlp/downloads/detail?name=PHamlP_3.2.zip&amp;can=2&amp;q=">Завантажуємо архів з бібліотекою phamlp</a></p>
<p>2. Архів розпаковуємо в «assets/plugins/phamlp» (можна без папки haml)</p>
<p>2. В «Елементах» створюємо новий плагін «SASS»</p>
<p>4. Копіюємо і вставляємо код плагіна:</p>
<pre class="brush: php;">
// директорія з стилями (в кінці слеш обов'язково)
$style_dir = MODX_BASE_PATH.'assets/css/'; 

// скування вміст
$files = scandir(rtrim($style_dir,'/'));

// вибір файлів с розширенням sass
foreach ($files as $sass_file)
if (is_file($style_dir.$sass_file) && (strtolower(pathinfo($style_dir.$sass_file,PATHINFO_EXTENSION))=='sass')) {
	// обчислення перевірочного md5 хеша вмісту .sass файла
	$sass_hash = hash('md5',file_get_contents($style_dir.$sass_file));

	// при відсутності записаного (в .sasshash файл) хеша або його розбіжності з записаним - генерація css
	if (!file_exists($style_dir.$sass_file.'hash')||($sass_hash!=file_get_contents($style_dir.$sass_file.'hash'))) {
		// підключення бібліотеки phamlp
		include_once(MODX_BASE_PATH.'assets/plugins/phamlp/sass/SassParser.php');

		// ініціалізація і налаштування класу работи з sass форматом 
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

		// генерація css файла 
		file_put_contents( $style_dir.substr($sass_file,0,-4).'css', $sass->toCss($style_dir.$sass_file) );

		// запис хеша
		file_put_contents( $style_dir.$sass_file.'hash', $sass_hash );
	}
}
</pre>
<p>5. На вкладці «Системні події» ставим галочку навпроти OnWebPageInit. Це означає запуск коду плагіна під час ініціалізації веб-сторінки (легше кажучи – кожний раз, коли хто-небудь загружає будь-яку із сторінок сайту). З тим же успіхом можна використовувати й інші події MODX, що відбуваються в цей час (OnWebPagePrerender, OnParseDocument).</p>
<p>6. Зберігаємо плагін</p>
<h3 class="sub-header text-bold">Працюємо з стилями в Sass-форматі</h3>
<p>Звичайно, для цього підійде навіть штатний веб-редактор MODX (або завантаження по FTP файлах, створених в Блокноті), але якщо вже розширювати инструментарій веб-розробки, то краще відкрити для себе можливості однієї із інтегрованих середовищ розробки (IDE) з потужним набором вбудованих засобів (FTP-менеджер, підсвічування синтаксису, управління версіями і т.п.).</p>
<p>В директорії «assets/css» (як вказано в змінній $style_dir) создаємо файл с разширенням .sass. Для початку, в цьому файлі можна зберегти <a href="http://ru.wikipedia.org/wiki/Sass" target="_blank">приклади з вікіпедії</a>.</p>
<p>Відкриваємо сайт в браузері або оновлюємо відкриту сторінку. В момент виникнення події OnWebPageInit запуститься плагін «SASS», який при скануванні виявить свіжий sass-файл, і згенерує його css-версію, яка з цього момента доступна для завантаження в браузери користувачів з усього світу.</p>
<p>Після закінчення роботи над стильовим оформленням сайту, плагін можна відключити, щоб не здійснював холостих скануваннь.</p>
<p><span class="text-bold">UPD: MODX</span> Evo і MODX Revo мають одинакові принципи створення плагінів і назви вказаних системних подій.</p>
