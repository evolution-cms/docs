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
Начинаем делать самое интересное, ядро модуля. Открываем core.php, проверяем кодировку. Должна быть utf-8 без BOM.

Первой же строкой после открывающего тега php мы проверим, может ли пользователь открывать этот файл.
```php
if(IN_MANAGER_MODE!='true' && !$modx->hasPermission('exec_module')) die('ERROR');
```
Зададим несколько переменных, которые нам понадобятся в работе со скриптом
```php
$Template=new Template;//новый класс. О нём позже
$bigAction = $_GET['a'];//текущее значение аргумента a из урла
$moduleId = $_GET['id'];//айди модуля
$FullTableName = $modx->getFullTableName('site_content');//полное имя таблицы контента
```

Пишем класс для шаблонизации.
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
Код достаточно сложен для понимания сходу.

Он подключает языковые файлы, исходя из того, какая версия языка выбрана в админке, инициализирует переменную-массив lang. В этот массив мы будем писать наши плейсхолдеры, кстати. Далее он парсит переданный ему шаблон, ищет соответствия между плейсхолдером в шаблоне и значением в lang-файле и возвращает результат — собранную страницу. Как пользоваться классом, мы рассмотрим чуть ниже. Пока же просто скопируйте его в core.php

Теперь начинаем думать над функционалом. Модуль должен делать 2 вещи. Первая — показать нам список товаров. Вторая — редактировать выбранный товар. Конечно, можно заморочиться с серьёзной шаблонизацией, роутингом и классами для каждого действия, но задача сейчас проще. Поэтому все наши действия заворачиваем в switch-case и получаем вот такой большой скрипт.
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
Итак, мы имеем разделение на 2 действия в case. В самом начале ловим переданный нам $\_REQUEST['action']

Действие default происходит по-умолчанию при загрузке модуля, когда никакой action нам не передан.

Здесь возникает вопрос, что за $params['sectionId'] такая. Если вы лазали в конфигурации модулей, то могли увидеть там похожую картину:

![config](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/7.png)

Это параметры модуля, особенность Эво. Скрипт модуля всегда их получает в массиве $params. Как задать параметр? Для начала надо создать новый модуль. Перейти во вкладку «Свойства» и там задать параметры в формате json. Нам нужен только 1 параметр, sectionId. В него будем писать, из какого раздела брать документы. Заполняем свойства
```php
{ "sectionId": [{"label": "ID родителя", "type": "integer","value": "2","default": "2","desc": ""    }]}
```
Всё. Я указал раздел с id=2. Теперь в тело модуля пишите подключение скрипта ядра
```php
include_once('../assets/modules/contentEditor/core.php');
```
Заполняйте название и описание. Можно смело обновлять страницу админки, модуль будет установлен. А мы продолжим разбираться со скриптом.

Как видите, в действии по-умолчанию мы делаем запрос к базе, разбираем его и в цикле присваиваем переменной lang['phpwork'] результат работы, строчка за строчкой. А phpwork — ничего не напоминает? Это наш плейсхолдер, заданный в шаблоне. Т.е. мы будем выводить на его месте результаты работы скрипта.

А как будем это делать, скажут эти 2 строчки вызова класса.
```php
$tpl = Template::parseTemplate($Template->getTpl(dirname( __FILE__ ).'/templates/main.html'),$modx->config);
$tpl = Template::parseTemplate($tpl ,$Template->lang);
```
Принцип работы: берём файл main.html и заменяем в нём все плейсхолдеры на их значения из соответствующих переменных.

В действии edit мы проверяем, пришёл ли пост-запрос. Если да, то обновляем содержимое полей в базе и выводим отчёт о работе, либо положительный, либо отрицательный. Если запрос не пришёл, рисуем форму. Ловим переданный нам параметр editDoc, делаем запрос, отображаем поля для редактирования и в них текущие значения pagetitle и introtext.

Пора сделать языковой файл. Если вы обратили внимание на код класса, то могли заметить, что подключение языка происходит по вот такой схеме:
```php
include_once(dirname(__FILE__) . '/lang/'.$lang.'.php')
```
где $lang это текущий язык системы, взятый из конфига Эво.

Руководствуясь этим, создаём 2 файла в папке lang: russian-UTF8.php и english.php

Приведу для примера русский файл. Любой файл любого другого языка абсолютно такой же, за исключением, разумеется, перевода.
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
Как видите, внутри массива $\_field мы создали элементы массива, ключи которых полностью совпадают с теми плейсхолдерами, которые заданы в шаблоне main.html.

Попробуйте запустить модуль. У вас должны работать табы, отображаться товары. Но пока что не работает редактирование. Давайте это исправим.

Посмотрите внимательно на вызов парсера при действии edit. Мы вызываем практически всё точно также, за исключением шаблона. Для редактирования применим новый шаблон, edit.html. Создайте такой файл в папке templates

Вот его полный листинг:
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
Шаблон очень похож на main.html. Но есть ньюансы. Во-первых мы задали функцию postForm, которая при вызове отправит содержимое формы с id=frm. Во-вторых, мы задали новые кнопки в панели actionButtons. Кнопка «Сохранить» как раз и будет вызывать функцию и отправлять форму, а кнопка «Закрыть» просто переадресует нас на главную страницу модуля, что равносильно закрытию страницы редактирования.

Дальше никаких изменений нет, и в phpwork подставляется содержимое переменных из секции case 'edit': файла core.php.

Конечно, в этот модуль можно было добавить ТВ-параметры, аякс-редактирование и многие другие интересные вещи, однако, статья получилась и без того объёмная.
