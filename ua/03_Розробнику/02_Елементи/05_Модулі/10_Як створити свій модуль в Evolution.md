## Задача ##
Пишемо простий модуль для редагування документів. Оформлення стандартне, в стилях адмінки. Модуль багатомовний, шаблонний, розширюваний під майбутні завдання. У нас вийде «болванка», яку можна буде використовувати далі.

#### Главная страница модуля ####
Список товарів з потрібного розділу, у кожного товару є заголовок, анотація і редагування. Тв-параметри ми брати не будемо, це все ж модуль для навчання.![screenshot_1](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/1.png)

#### Процесс редактирования ####
![screenshot_2](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/2.png)

#### Дополнительная вкладка ####
![screenshot_3](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/3.png)
За функціоналом вона тут не потрібна, зробимо її для прикладу.

#### Структура модуля ####
1. Лізимо в assets/modules и створюємо папки и пусті файли.

![screenshot_4](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/4.png)

Основна папка модуля — contentEditor. В ній всього 1 файл — це core.php. Ядро и основний функціонал нашого майбутнього модуля. В css будуть стилі, в templates шаблони, в lang мовні версії.

#### Начальный шаблон модуля ####

Файли шаблонов для модуля — це просто html файли. Розуміється, раз це шаблони, у них буде як статична частина, так і динамічні блоки, в які ми і будемо вставляти плейсхолдери, які самі ж і задамо.

Створюємо файл main.html. У всіх файлів вказувати кодування utf-8 (без BOM)!
Давайте ще раз глянемо на початкову сторінку нашего майбутнього модуля і визначимось, що потрібно верстати.

![main](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/5.png)

Для того, щоб ми могли використовувати стилі і деякі можливості Evo, пишемо в секції head наступне:

```html
<head>
<meta content="text/html; charset=[+modx_charset+]" http-equiv="Content-Type">
<title>[+store_name+]</title>
<link rel="stylesheet" type="text/css" href="media/style/[+manager_theme+]/style.css">
<link rel="stylesheet" type="text/css" href="[+site_url+]assets/modules/contentEditor/css/main.css">
<script type="text/javascript" src="media/script/mootools/mootools.js" ></script>
<script type="text/javascript" src="media/script/mootools/moodx.js"></script>
<script type="text/javascript" src="media/script/tabpane.js"></script>
</head>
```


Як бачите, це не зовсім чистий html. Ми вставили в деякі атрибути плейсхолдери. Давайте розбиратися. У першому рядку вставлений [+ modx_charset +] - це кодування сайту. Ево автоматично замінить її на ту, що виставлена в налаштуваннях.

Далі 2 плейсхолдери [+manager_theme+] і [+site_url+]. Перший відповідає за шлях до файлів теми адмін-панелі. Другий - урл сайту. Тобто ми не задаємо жорсткий шлях до файлу стилів, а конструюємо його.

Навіщо ми це зробили? Щоб наш модуль брав стилі з тієї теми адмінки, яка встановлена в налаштуваннях сайту в даний момент.

Для прикладу я міняю тему на стару, і ось так тепер виглядає модуль в стилі старої-доброї зелененький адмінки з версії 1.15.![115](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/6.png)

Ідем далі. Як ми бачимо, нагорі модуля у нас є заголовок, анотація і кнопка «Оновити». Давайте їх зробимо. Відкриваємо body і пишемо:
```html
<h1>[+store_name+]</h1>
	<div id="actions">
		<ul class="actionButtons">
			<li id="Button1">
				<a href="#" onclick="document.location.href=document.location.href;">
					<img src="media/style/[+manager_theme+]/images/icons/refresh.png">[+refresh+]
				</a>
			</li>
		</ul>
	</div>
```
Що ж таке ми вставили в h1?

[+store_name+] — це плейсхолдер, де ми будемо зберігати назву модуля. Я назвав його так, ви можете придумати свою назву, головне, не забудьте. Ці саморобні плейсхолдери ми будемо потім переводити на 2 мови, щоб модуль був багатомовним і розширюваним.

Нижче вставляємо код для кнопки «Оновити». Це більш-менш стандартна секція для кнопок дії в модулях. За замовчуванням вона кріпиться справа-зверху і стилізується під адмінку. Якщо придивитися, ми знову бачимо плейсхолдер папки в адресі картинки. Тобто міняємо тему - змінюється малюнок у кнопки. У плейсхолдер [+ refresh +] буде записаний текст на кнопці. Запам'ятовуємо це. Дія на клік по кнопці - цілком звичайний ява-скрипт для перезавантаження. Кнопка «Оновити» готова.
Hint: Якщо полазити в папці media/style/папка темы/images/icons то можна знайти купу іконок для своїх кнопок, які ви також можете встановити, створивши новий li зі схожою розміткою.

Робимо тіло сторінки. Подивіться на макет - нам потрібні дві вкладки. У першій з них буде таблиця з осередком заголовків і вмістом. У другій тільки текст.
```html
<div class="sectionBody">
	<p>[+module_description+]</p>
	<div class="tab-pane" id="tabPanel">
		<script type="text/javascript">
			mypanel = new WebFXTabPane(document.getElementById("tabPanel"), true);
		</script>
		<div class="tab-page" id="startTab">
			<h2 class="tab">[+tab1_header+]</h2>
			<script type="text/javascript">mypanel.addTabPage(document.getElementById("startTab"));</script>
			<div>
				<table class="grid">
					<thead>
						<tr>
							<td  class="gridHeader">[+table_id+]</td>
							<td  class="gridHeader">[+table_header+]</td>
							<td  class="gridHeader">[+table_header2+]</td>
							<td  class="gridHeader">[+table_action+]</td>
						</tr>
					</thead>
					<tbody>
						[+phpwork+]
					</tbody>
				</table>
			</div>
			<p>[+tab1_description+]</p>
		</div>	
		<div class="tab-page" id="startTab2">
			<h2 class="tab">[+tab2_header+]</h2>
			<script type="text/javascript">mypanel.addTabPage( document.getElementById("startTab2"));</script>
			<div>
				[+tab1_text+]
			</div>
		</div>	
	</div>
</div>
```

Досить непростою шматок коду на перший погляд.

Відразу ж йде плейсхолдер [+ module_description +] - це буде опис модуля.
Клас sectionBody - це стиль Ево і використовується він для тіла модуля.

Створимо розмітку табів. Вона починається створенням шару-оболонки з класом tab-pane і ідентифікатором tabPanel. Ідентифікатор може бути довільним. Відразу ж після відкриваючого тега запускаємо стандартний скрипт Ево для панелей. Це виклик функції WebFXTabPane, якії ми передаємо в якості аргументу id створеного шару-оболонки.

Зробимо вкладки. Кожна з них повинна мати унікальний id і клас tab-page. Відразу ж всередині вкладки потрібно розмістити заголовок панелі
Dosytʹ neprostoyu shmat


```html
<h2 class="tab">[+tab1_header+]</h2>
```

Що таке [+ tab1_header +] ви вже здогадалися? Правильно, це назва панелі, яку ми пізніше задамо в файлах мови.

Прокрутіть код до 27-ї лінії. Ми створюємо 2-ю вкладку:

```html
<div class="tab-page" id="startTab2">
```

Все по аналогії з першої, за винятком id. Нагадаю, у кожної вкладки він повинен бути унікальний. Для того, щоб вкладки працювали і переключалися, потрібно їх додати в обробник.

За це відповідає рядок скрипта
```js
mypanel.addTabPage(document.getElementById("startTab"));
```
Рядок треба викликати в тезі script всередині кожної з вкладок. Як бачите, в першій вкладці ми використовували id першої вкладки, у другому - другий.

Відразу закінчимо зі вкладкою номер два, так як вона простіше. Єдиний вміст там це плейсхолдер [+ tab1_text +]. Це якийсь статичний текст, який також буде довантажений сюди пізніше.


Вкладка номер один. Потрібно створити таблицю для того, щоб в ній динамічно виводити вміст. Подивіться на код, коментувати тут нічого, крім, хіба що css-класів - це стандартні класи Ево для таблиці. Плейсхолдери для заголовків типу table_id і table_header аналогічні іншим. Під таблицею, як ми пам'ятаємо по макету, у нас розміститься невеликий абзац тексту. Давайте його теж зробимо змінним. Я назвав плейсхолдер [+ tab1_description +] і уклав його в абзац.

Врешті-решт ми дісталися до плейсхолдера [+ phpwork +]. Тут розміститься результат роботи скрипта core.php. Давайте перейдемо до нього.

#### Ядро модуля ####
Починаємо робити найцікавіше, ядро модуля. Відкриваємо core.php, перевіряємо кодування. Повинна бути utf-8 без BOM.

Після відкриваючого тега php ми перевіримо, чи може користувач відкривати цей файл.
```php
if(IN_MANAGER_MODE!='true' && !$modx->hasPermission('exec_module')) die('ERROR');
```
Задамо деілька змінних, які нам знадобляться в роботі зі скриптом.
```php
$Template=new Template;//новый класс. О нём позже
$bigAction = $_GET['a'];//текущее значение аргумента a из урла
$moduleId = $_GET['id'];//айди модуля
$FullTableName = $modx->getFullTableName('site_content');//полное имя таблицы контента
```

Пишемо клас для шаблонізації.
```php
class Template{
	public $lang;
	function __construct(){
		global $modx;
		$lang = $modx->config['manager_language'];
		if (file_exists( dirname(__FILE__) .  '/lang/'.$lang.'.php')){
			include_once(dirname(__FILE__) .  '/lang/'.$lang.'.php');
		} else {
			include_once(dirname(__FILE__) .  '/lang/english.php');
		}
		$this->lang = $_field;
	}
	
	function getTpl($file){
		ob_start();
		include($file);
		$tpl = ob_get_contents();  
		ob_end_clean(); 
		return $tpl;
	}
	
	static function parseTemplate($tpl,$field){
		foreach($field as $key=>$value)  $tpl = str_replace('[+'.$key.'+]',$value,$tpl);
		return $tpl;
	}
}
```

Код досить складний для розуміння відразу.

Він підключає мовні файли, виходячи з того, яка версія мови обрана в адмінці, ініціалізує змінну-масив lang. В цей масив ми будемо писати наші плейсхолдери, до речі. Далі він парсит переданий йому шаблон, шукає відповідності між плейсхолдером в шаблоні і значенням в lang-файл і повертає результат - зібрану сторінку. Як користуватися класом, ми розглянемо трохи нижче. Поки ж просто скопіюйте його в core.php

Тепер починаємо думати над функціоналом. Модуль повинен робити 2 речі. Перша - показати нам список товарів. Друга - редагувати обраний товар. Звичайно, можна заморочитись з серйозною шаблонізацією, роутингом і класами для кожної дії, але завдання зараз простіше. Тому всі наші дії загортаємо в switch-case і отримуємо ось такий великий скрипт.
```php
switch($_REQUEST['action']){
	default:	//	Действия при загрузке модуля
		$section=$params['sectionId'];	//	Получаем из конфига id раздела
		$result = $modx->db->select('id,pagetitle,introtext', $FullTableName, 'parent='.$section, '', 30);
		if($modx->db->getRecordCount($result)>= 1){
			while($row = $modx->db->getRow( $result )){
				if($class){$class="gridAltItem";}else{$class="gridItem";}	//	Оформление ячеек, "зёбра"			
				$Template->lang['phpwork'] .='<tr class="'.$class.'">';
				$Template->lang['phpwork'] .='<td >'.$row["id"].'</td>';
				$Template->lang['phpwork'] .='<td>'.$row["pagetitle"].'</td>';
				$Template->lang['phpwork'] .='<td >'.$row["introtext"].'</td>';
				$Template->lang['phpwork'] .='<td ><a href="index.php?&a=' . $bigAction. '&id='.$moduleId . '&editDoc='. $row['id'].'&action=edit" data-id="'.$row["id"].'">' . $Template->lang['edit'] . '</a></td>';
				$Template->lang['phpwork'] .='</tr>';
			}
		}
		else{
			$Template->lang['phpwork'] = '';
		}
		$tpl = Template::parseTemplate($Template->getTpl(dirname( __FILE__ ).'/templates/main.html'),$modx->config);
		$tpl = Template::parseTemplate($tpl ,$Template->lang);
		echo $tpl;
	break;
	case 'edit':
		if($_POST){
			$fields = array(
			"pagetitle" => $modx->db->escape($_POST["pagetitle"]),
			"introtext" => $modx->db->escape($_POST["introtext"])
			);
			$result = $modx->db->update($fields, $FullTableName, "id=" . $_GET['editDoc']);
			if($result){
				$Template->lang['phpwork'] = $Template->lang['save_success'];
			}
			else{
				$Template->lang['phpwork'] = $Template->lang['save_error'];
			}
		}
		else{
			$result = $modx->db->select('id,pagetitle,introtext', $FullTableName, 'id='.$modx->db->escape($_GET['editDoc']));
			if($modx->db->getRecordCount($result)>= 1){
				
				while($row = $modx->db->getRow( $result )){
					if($class){$class="gridAltItem";}else{$class="gridItem";}	//	Оформление ячеек, "зёбра"			
					$Template->lang['phpwork'] .='<tr class="'.$class.'">';
					$Template->lang['phpwork'] .='<td>'.$Template->lang['header'].'</td>';
					$Template->lang['phpwork'] .='<td><input name="pagetitle" type="text" maxlength="255" value="'.$row["pagetitle"].'" class="inputBox" onchange="documentDirty=true;" spellcheck="true"></td>';
					$Template->lang['phpwork'] .='</tr>';
					$Template->lang['phpwork'] .='<tr class="'.$class.'">';
					$Template->lang['phpwork'] .='<td>'.$Template->lang['table_header2'].'</td>';
					$Template->lang['phpwork'] .='<td><textarea id="introtext" name="introtext" class="inputBox" rows="3" cols="" onchange="documentDirty=true;">'.$row["introtext"].'</textarea></td>';				
					$Template->lang['phpwork'] .='</tr>';
				}
			}
		}
		$tpl = Template::parseTemplate($Template->getTpl(dirname( __FILE__ ).'/templates/edit.html'),$modx->config);
		$tpl = Template::parseTemplate($tpl ,$Template->lang);
		echo $tpl;		
	break;
}
```
Отже, ми маємо поділ на 2 дії в case. На самому початку ловимо переданий нам $ \ _ REQUEST [ 'action']

Дія default відбувається за замовчуванням при завантаженні модуля, коли ніякої action нам не переданий.
Тут виникає питання, що за $params['sectionId'] така. Якщо ви лазили в конфігурації модулів, то могли побачити там схожу картину:
![config](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/7.png)

Це параметри модуля, особливість Ево. Скрипт модуля завжди їх отримує в масиві $params. Як задати параметр? Для початку треба створити новий модуль. Перейти у вкладку «Властивості» і там задати параметри в форматі json. Нам потрібен тільки 1 параметр, sectionId. У нього будемо писати, з якого розділу брати документи. Заповнюємо властивості

```php
{ "sectionId": [{"label": "ID родителя", "type": "integer","value": "2","default": "2","desc": ""    }]}
```
Все. Я вказав разділ з id=2. Тепер в тіло модуля пишіть підключення скрипта ядра
```php
include_once('../assets/modules/contentEditor/core.php');
```
Заповнюйте назву і опис. Можна сміливо оновлювати сторінку адмінки, модуль буде встановлено. А ми продовжимо розбиратися зі скриптом.

Як бачите, в дії за замовчуванням ми робимо запит до бази, розбираємо його і в циклі присвоюємо змінної lang [ 'phpwork'] результат роботи, рядок за рядком. А phpwork - нічого не нагадує? Це наш плейсхолдер, заданий в шаблоні. Тобто ми будемо виводити на його місці результати роботи скрипта.

А як будемо це робити, скажуть ці 2 рядки виклику класу.
```php
$tpl = Template::parseTemplate($Template->getTpl(dirname( __FILE__ ).'/templates/main.html'),$modx->config);
$tpl = Template::parseTemplate($tpl ,$Template->lang);
```
Принцип роботи: беремо файл main.html і замінюємо в ньому все плейсхолдери на їх значення з відповідних змінних.

У дії edit ми перевіряємо, чи прийшов пост-запит. Якщо так, то оновлюємо вміст полів в базі і виводимо звіт про роботу, або позитивний, або негативний. Якщо запит не прийшов, малюємо форму. Ловимо переданий нам параметр editDoc, робимо запит, відображаємо поля для редагування і в них поточні значення pagetitle і introtext.

Пора зробити мовний файл. Якщо ви звернули увагу на код класу, то могли помітити, що підключення мови відбувається по ось такою схемою:
`` `Php
include_once (dirname (__ FILE__). '/lang/'.$lang.'.php')
`` `
де $ lang це поточна мова системи, взятий з конфіга Ево.

Керуючись цим, створюємо 2 файли в папці lang: russian-UTF8.php і english.php

Наведу для прикладу російський файл. Будь-який файл будь-якого іншої мови абсолютно такий же, за винятком, зрозуміло, перекладу.
```php
$_field['store_name'] = "Редактор товаров";
$_field['module_description'] = "<p>Модуль редактирования товаров.</p>";
$_field['close'] = "Закрыть";
$_field['edit'] = "Редактировать";
$_field['refresh'] = "Обновить";
$_field['header'] = "Заголовок";
$_field['save'] = "Сохранить";
$_field['table_id'] = "id";
$_field['table_header'] = "Заголовок";
$_field['table_header2'] = "Аннотация";
$_field['table_action'] = "Действия:";
$_field['tab1_header']='Товары';
$_field['tab1_description']='Раздел для управления вы можете указать в конфигурации модуля ("Модули" - "Управление модулями")';
$_field['tab2_header']='О модуле';
$_field['tab1_text']='Тестовый модуль для просмотра и редактирования товаров';
$_field['save_success']='Сохранили';
$_field['save_error']='Ошибка сохранения';
?>  
```

Як бачите, всередині масиву $ \ _ field ми створили елементи масиву, ключі яких повністю збігаються з тими плейсхолдерами, які задані в шаблоні main.html.

Спробуйте запустити модуль. У вас повинні працювати таби, відображатися товари. Але поки що не працює редагування. Давайте це виправимо.

Подивіться уважно на виклик парсеру при дії edit. Ми викликаємо практично все точно також, за винятком шаблону. Для редагування застосуємо новий шаблон, edit.html. Створіть такий файл в папці templates

Ось його повний лістинг:
```html
<!DOCTYPE html>
<html>
	<head>
		<meta content="text/html; charset=UTF-8" http-equiv="Content-Type">
		<title>[+store_name+]</title>
		<link rel="stylesheet" type="text/css" href="media/style/[+manager_theme+]/style.css"> 
		<link rel="stylesheet" type="text/css" href="[+site_url+]/assets/modules/contentEditor/css/main.css"> 
		<script type="text/javascript" src="media/script/mootools/mootools.js" ></script>
		<script type="text/javascript" src="media/script/mootools/moodx.js"></script>
		<script type="text/javascript" src="media/script/tabpane.js"></script>
		<script>
		function postForm(){
			document.frm.submit();
		}
		</script>
	</head>
	<body>
		<h1>[+store_name+]</h1>
		<div id="actions">
			<ul class="actionButtons">		
				<li>
					<a href="index.php?a=112&id=<?php echo $_GET['id'];?>" class="primary" id="save" onclick="postForm();return false;">
					<img alt="icons_save" src="media/style/MOD_Anytheme/images/icons/save.png">[+save+]</a>
				</li>
				<li>
					<a href="index.php?a=112&id=<?php echo $_GET['id'];?>">
						<img src="media/style/[+manager_theme+]/images/icons/stop.png">[+close+]
					</a>
				</li>				
			</ul>
		</div>	
		<div class="sectionBody">
			<div class="tab-pane" id="cePanel">
				<script type="text/javascript">
					mypanel = new WebFXTabPane(document.getElementById("cePanel"), true );
				</script>
				<div class="tab-page" id="startTab">
					<h2 class="tab">[+tab1_header+]</h2>
					<script type="text/javascript">mypanel.addTabPage(document.getElementById("startTab"));</script>
					<div>
						<form name="frm" class="content" method="post" enctype="multipart/form-data">
							<table class="grid">
								<tbody>
									[+phpwork+]									
								</tbody>
							</table>
						</form>
					</div>
				</div>
			</div>
		</div>
	</body>
</html>
```

Шаблон дуже схожий на main.html. Але є нюанси. По-перше ми задали функцію postForm, яка при виклику відправить вміст форми з id = frm. По-друге, ми задали нові кнопки в панелі actionButtons. Кнопка «Зберегти» якраз і буде викликати функцію і відправляти форму, а кнопка «Закрити» просто переадресує нас на головну сторінку модуля, що рівносильно закриття сторінки редагування.

Далі ніяких змін немає, і в phpwork підставляється вміст змінних з секції case 'edit': файлу core.php.

Звичайно, в цей модуль можна було додати ТВ-параметри, ajax-редагування і багато інших цікавих речей, проте, стаття вийшла і без того об'ємна.
