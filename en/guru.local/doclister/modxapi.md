
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>DocLister: MODxAPI</h2>

<h2 class="page-header">Введение</h2>
<p>MODxAPI это попытка реализовать паттерн .
Изначально проектировалось как замена библиотеки DocManager, но в итоге оптимизирован код и заложен потенциал для создания обертки с произвольной логикой для любых таблиц.</p>
<h3 class="sub-header text-bold">Поддерживаемые модели</h3>
<p><em>modResource</em> - Документы (данные из таблицы site_content и site_tmplvar_contentvalues)</p>
<p><em>modUsers</em> - Веб-пользователи (данные из таблиц web_users и web_user_attributes)</p>
<p><em>modCategories</em> - Категории (данные из таблиц categories)</p>
<p><em>modChunk</em> - Чанки (данные из таблиц site_htmlsnippets)</p>
<p><em>modModule</em> - Модули (данные из таблиц site_modules)</p>
<p><em>modPlugin</em> - Плагины (данные из таблиц site_plugins</p>
<p><em>modSnippet</em> - Сниппеты (данные из таблиц site_snippets)</p>
<p><em>modTV</em> - ТВ параметры (данные из таблиц site_tmplvars)</p>
<p><em>modTemplate</em> - Шаблоны (данные из таблиц site_templates)</p>
<p>При желании можно быстро создать свою модель для любой таблицы. Для этого существует заготовка класса autoTable. В самом примитивном случае достаточно указать лишь название вашей таблицы. Взгляните на пример создания модели для таблицы с именем tests:</p>
<pre class="brush: php;">
&lt;?php
include_once(MODX_BASE_PATH. "assets/lib/MODxAPI/autoTable.abstract.php");
class modTests extends autoTable{
	protected $table = "tests";
}
</pre>
<h3 class="sub-header text-bold">Примеры использования</h3>
<p>Методы create, edit, delete, save актуальны для всех моделей. Но в качестве примера будем рассматривать модель modResource.</p>
<pre class="brush: php;">
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
$doc = new modResource($modx);
/** 
* Подготовить создание документа со следующими данными:
* ID шаблона = 10
* В качестве родителя использовать документ с ID = 1
* pagetitle заголовок документа = example
*/
$doc-&gt;create(array(
	'pagetitle' =&gt; 'example',
	'template' =&gt; 10,
	'parent' =&gt; 1
));
/** 
* зменить pagetitle заголовок документа на new title 
*/
$doc-&gt;set('pagetitle', 'new title');
/*
* Сохранить документ вызвав события OnBeforeDocFormSave OnDocFormSave,
* но не производить сброс кеша. 
* ID нового документа поместить в переменную id
*/
$id = $doc-&gt;save(true, false);
/** 
* Открыть на редактирование документ с ID = 10 
*/ 
$doc-&gt;edit(10);
/** 
* Меняем родителя родителя документа
*/
$doc-&gt;set('parent', 0);
/*
* Сохраняем документ не вызывая события OnBeforeDocFormSave OnDocFormSave,
* Но при этом производим соброс кеша.
* ID документа сохраняется в переменной $id
*/
$id = $doc-&gt;save(false, true);
/***
* Удалить все документы помеченые на удаление.
* При этом вызвать события OnBeforeEmptyTrash и OnEmptyTrash
* Если значение параметра изменить с true на false, то события вызваны не будут, хотя документы удалятся
*/
$doc-&gt;clearTrash(true);
/** 
* Удалить документ с ID = 5, минуя корзину
* При этом события OnBeforeEmptyTrash и OnEmptyTrash, будут вызваны.
*/
$doc-&gt;delete(5, true);
</pre>
<p>При помощи модели modUsers можно производить не только запись и получение данных, но еще и производить манипуляции с авторизацией:</p>
<pre class="brush: php;">
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$user = new modUsers($modx);
/**
* Авторизоваться от имени веб-пользователя с ID = 1
*/
$user-&gt;authUser(1);
/**
* Проверить статус блокировки веб-пользователя с ID = 1 
* Данный метод возвращает значение типа boolean
* true - заблокирован
* false - активен
*/
$flag = $user-&gt;checkBlock(1);
/**
* Проверить пароль myPassword для веб-пользвоателя с ID = 1 
* После чего выполнить проверку статуса блокировки. Если даже пароль указан верный, а пользователь заблокирован, то данный метод вернет значение false. В случае, если изменить значение 3 параметра на false, то статус блокировки проверяться не будет.
* Данный метод возвращает значение типа boolean
* true - верный пароль
* false - пароль не корректен
*/
$flag = $user-&gt;testAuth(1, 'myPassword', true);
/**
* Принудительно разлогинить веб-пользователя
*/
$user-&gt;logOut();
</pre>
<h3 class="sub-header text-bold">Практическое применение</h3>
<p><em>modUsers</em>
Следующий плагин для событий OnWebPageInit и OnPageNotFound, позволяет производить моментальное применение блокировки. Это бывает полезно, когда пользователь вроде бы забанен, но продолжает проявлять активность, т.к. сессия не истекла.</p>
<pre class="brush: php;">
include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modUsers.php");
$modx-&gt;user = new modUsers($modx);
if($modx-&gt;isFrontend() &amp;&amp; $modx-&gt;getLoginUserID('web')){
	$modx-&gt;user-&gt;edit((int)$modx-&gt;getLoginUserID('web'));
	if(!$modx-&gt;user-&gt;getID() || $modx-&gt;user-&gt;checkBlock()){
		$modx-&gt;user-&gt;logOut();
	}
}
</pre>
<p><em>modResource</em>
Следующий сниппет позволяет последовательно получать значения полей одного и того же документа не выполняя при этом повторый SQL запрос.</p>
<pre class="brush: php;">
/**
* &lt;h5&gt;MODxAPI&lt;/h5&gt;
* &lt;img src="" /&gt;
* С данным сниппетом будет выполнен всего 1 SQL запрос
*/
if(empty($modx-&gt;doc)){
	include_once(MODX_BASE_PATH."assets/lib/MODxAPI/modResource.php");
	$modx-&gt;doc = new modResource($modx);
}
$id = isset($id) ? (int)$id : $modx-&gt;documentObject['id'];
$field = isset($field) ? (string)$field : 'id';
if($field == 'id'){
	$out = $id;
}else{
	if($modx-&gt;documentObject['id'] == $id){
		$out = isset($modx-&gt;documentObject[$field]) ? $modx-&gt;documentObject[$field] : '';
		if(is_array($out)){
		   $out = isset($out[1]) ? $out[1] : '';
		}
	}else{
		$doc = clone $modx-&gt;doc;
		$out = $doc-&gt;edit($id)-&gt;get($field);
	}
}
return (string)$out;
</pre>