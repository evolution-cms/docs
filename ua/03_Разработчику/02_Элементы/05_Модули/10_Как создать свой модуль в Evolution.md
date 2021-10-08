## Задача ##
Пишем простой модуль для редактирования документов. Оформление стандартное, в стилях админки. Модуль мультиязычный, шаблонизируемый, расширяемый под будущие задачи. У нас получится «болванка», которую можно будет использовать дальш.

#### Главная страница модуля ####
Список товаров из нужного раздела, у каждого товара есть заголовок, аннотация и редактирование. Тв-параметры мы брать не будем, это всё же модуль для обучения.
![screenshot_1](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/1.png)

#### Процесс редактирования ####
![screenshot_2](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/2.png)

#### Дополнительная вкладка ####
![screenshot_3](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/3.png)
По функционалу она тут не нужна, сделаем её для примера.

#### Структура модуля ####
1. Лезем в assets/modules и создаём папки и пустые файлы.

![screenshot_4](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/4.png)

Основная папка модуля — contentEditor. В ней всего 1 файл — это core.php. Ядро и основной функционал нашего будущего модуля. В css будут стили, в templates шаблоны, в lang языковые версии.

#### Начальный шаблон модуля ####

Файлы шаблонов для модуля — это просто html файлы. Разумеется, раз это шаблоны, у них будет как статичная часть, так и динамические блоки, в которые мы и будем вставлять плейсхолдеры, которые сами же и зададим.

Создаём файл main.html. У всех файлов указывать кодировку utf-8 (без BOM)!
Давайте ещё раз глянем на стартовую страницу нашего будущего модуля и определимся, что нужно верстать.

![main](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/5.png)

Для того, чтобы мы могли использовать стили и некоторые возможности Evo, пишем в секции head следующее:

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

Как видите, это не совсем чистый html. Мы вставили в некоторые атрибуты плейсхолдеры. Давайте разбираться. В первой строке вставлен [+modx_charset+] — это кодировка сайта. Эво автоматически заменит её на ту, что выставлена в настройках.

Дальше 2 плейсхолдера [+manager_theme+] и [+site_url+]. Первый отвечает за путь к файлам темы админ-панели. Второй — урл сайта. Т.е. мы не задаём жёсткий путь к файлу стилей, а конструируем его.

Зачем мы это сделали? Чтобы наш модуль брал стили из той темы админки, которая установлена в настройках сайта в данный момент.

Для примера я меняю тему на старую, и вот так теперь выглядит модуль в стиле старой-доброй зелёненькой админки из версии 1.15.
![115](https://raw.githubusercontent.com/0test/docs/master/ru/02_Разработка/07_Elements/20_Modules/6.png)

Едем дальше. Как мы видим, наверху модуля у нас есть заголовок, аннотация и кнопка «Обновить». Давайте их сделаем. Открываем body и пишем:

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
Что же такое мы вставили в h1?

[+store_name+] — это плейсхолдер, где мы будем хранить название модуля. Я назвал его так, вы можете придумать своё название, главное, не забудьте. Эти самодельные плейсхолдеры мы будем потом переводить на 2 языка, чтобы модуль был мультиязычным и расширяемым.

Ниже вставляем код для кнопки «Обновить». Это более-менее стандартная секция для кнопок действия в модулях. По-умолчанию она крепится справа-сверху и стилизуется под админку. Если присмотреться, мы опять видим плейсхолдер папки в адресе картинки. Т.е. меняем тему — меняется рисунок у кнопки. В плейсхолдер [+refresh+] будет записан текст на кнопке. Запоминаем это. Действие на клик по кнопке — вполне обычный ява-скрипт для перезагрузки. Кнопка «Обновить» готова.

Hint: Если полазать в папке media/style/папка темы/images/icons то можно найти кучу иконок для своих кнопок, которые вы также можете установить, создав новый li с похожей разметкой.

Делаем тело страницы. Посмотрите на макет — нам нужны две вкладки. В первой из них будет таблица с ячейкой заголовков и содержимым. Во второй только текст.

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

Довольно непростой кусок кода на первый взгляд.

Сразу же идёт плейсхолдер [+module_description+] — это будет описание модуля.
Класс sectionBody — это стиль Эво и используется он для тела модуля.

Создадим разметку табов. Она начинается созданием слоя-оболочки с классом tab-pane и идентификатором tabPanel. Идентификатор может быть произвольным. Сразу же после открывающего тега запускаем стандартный скрипт Эво для панелей. Это вызов функции WebFXTabPane, которой мы передаём в качестве аргумента id созданного слоя-оболочки.

Сделаем вкладки. Каждая из них должна иметь уникальный id и класс tab-page. Сразу же внутри вкладки нужно разместить заголовок панели

```html
<h2 class="tab">[+tab1_header+]</h2>
```

Что такое [+tab1_header+] вы уже догадались? Правильно, это название панели, которое мы позже зададим в файлах языка.

Промотайте код до 27-й линии. Мы создаём 2-ю вкладку:

```html
<div class="tab-page" id="startTab2">
```

Всё по аналогии с первой, за исключением id. Напомню, у каждой вкладки он должен быть уникален. Для того, чтобы вкладки работали и переключались, нужно их добавить в обработчик.

За это отвечает строка скрипта

```js
mypanel.addTabPage(document.getElementById("startTab"));
```

Строку надо вызывать в теге script внутри каждой из вкладок. Как видите, в первой вкладке мы использовали id первой вкладки, во втором — второй.

Сразу закончим со вкладкой номер два, так как она попроще. Единственное содержимое там это плейсхолдер [+tab1_text+]. Это некий статичный текст, который также будет подгружен сюда позже.

Вкладка номер один. Нужно создать таблицу для того, чтобы в ней динамически выводить содержимое. Посмотрите на код, комментировать тут нечего, кроме, разве что css-классов — это стандартные классы Эво для таблицы. Плейсхолдеры для заголовков типа table_id и table_header аналогичны остальным. Под таблицей, как мы помним по макету, у нас разместится небольшой абзац текста. Давайте его тоже сделаем изменяемым. Я назвал плейсхолдер [+tab1_description+] и заключил его в абзац.

В конце концов мы добрались до плейсхолдера [+phpwork+]. Здесь разместится результат работы скрипта core.php. Давайте перейдём к нему.

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
