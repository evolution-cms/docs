
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>multiTV: Установка</h2>

<p>Есть две возможности установить multiTV в MODX Evolution</p>
<ul>
	<li>Используйте <a rel="nofollow" target="_blank" href="https://github.com/Jako/PackageManager">Менеджер Пакетов</a> и установите <a rel="nofollow" target="_blank" href="https://github.com/Jako/multiTV/archive/master.zip">последний пакет multiTV</a></li>
	<li>Или установите вручную:
		<ol>
			<li>Загрузите папку <code>assets/tvs/multitv</code> в соответствующую папку в вашей установке.</li>
			<li>Создайте новый шаблон и переменную с типом ввода <code>custom input</code> (если имя этой переменной будет <code>multidemo</code> то будет использоваться файл конфигурации <code>multidemo</code>)</li>
			<li>Вставьте следующий код в возможные значения <code>@INCLUDE/assets/tvs/multitv/multitv.customtv.php</code></li>
			<li>Создайте новый сниппет с названием multiTV и поместите в него следующий код:<br><code>&lt;?php return include(MODX_BASE_PATH.'assets/tvs/multitv/multitv.snippet.php'); ?&gt;</code></li>
		</ol>
	</li>
</ul>
<h3 class="sub-header text-bold">Совместимость</h3>
<ol>
	<li>Если вы хотите использовать multiTV с ManagerManager <em>до версии MODX 1.0.9</em> вы должны исправить файл <code>mm.inc.php</code> и вставить <code>case 'custom_tv':</code> в 136 строке перед строкой <code>$t = 'textarea';</code></li>
	<li>Если вы хотите использовать multiTV с YAMS, вы должны исправить <code>yams.plugin.inc.php</code> согласно этой <a rel="nofollow" target="_blank" href="https://github.com/Jako/multiTV/issues/9#issuecomment-6992127">инструкции</a>.</li>
	<li>Если вы обновляете 1.4.10 и ниже можно установить сниппет updateTV и изменить данные в вашей переменной multiTV в новый формат. Это необходимо, если вы хотите добавить/удалить столбцы в multiTV или если вы хотите отсортировать результаты по столбцу.</li>
	<li>Если вы хотите использовать PHx с multiTV необходимо немного изменить код плагина PHx:</li>
</ol>
<pre class="brush: php;">if (!class_exists('PHxParser')) {
	include MODX_BASE_PATH . "assets/plugins/phx/phx.parser.class.inc.php";
}
$e = &$modx-&gt;Event;
switch($e-&gt;name) {
	case 'OnParseDocument':
	$PHx = new PHxParser($phxdebug,$phxmaxpass);
	$PHx-&gt;OnParseDocument();
	break;
}</pre>