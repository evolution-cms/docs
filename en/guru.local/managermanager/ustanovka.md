
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ManagerManager: Установка</h2>

<h3 class="sub-header text-bold"><a id="997"></a>Новая установка</h3><p>Данный плагин уже входит в установочный комплект MODx Evolution, поэтому, прежде чем его устанавливать, проверьте его наличие и версию в <em><span class="text-bold">Элементы &gt;&gt; Управление элементами &gt;&gt; Плагины</span></em>.</p>
<p>1. Скачайте последнюю версию <a href="http://code.divandesign.ru/modx/managermanager" rel="nofollow" target="_blank">ManagerManager</a></p>
<p>2. Разархивируйте скачанный файл.</p>
<p>3. В панели управления сайтом создайте новый плагин «ManagerManager», вставьте содержимое из файла plugin.txt.</p>
<p>4. Во вкладке "Системные события" отметьте события:</p>
<ul>
	<li><span class="text-bold">OnDocFormRender</span></li>
	<li><span class="text-bold">OnDocFormPrerender </span></li>
	<li><span class="text-bold">OnBeforeDocFormSave</span></li>
	<li><span class="text-bold">OnDocFormSave</span></li>
	<li><span class="text-bold">OnDocDuplicate</span></li>
	<li><span class="text-bold">OnPluginFormRender</span></li>
	<li><span class="text-bold">OnTVFormRender</span></li>	
</ul>
<p>5. Во вкладке "Конфигурация" вставьте нижеприведённый код в поле "Конфигурация плагина:", и щёлкните "Обновить параметры":</p>
<pre class="brush: html;">&remove_deprecated_tv_types_pref=Remove deprecated TV types;list;yes,no;yes &config_chunk=Configuration Chunk;text;</pre>
<p>6. Скопируйте все файлы из архива (кроме plugin.txt) на сайт (необходимая структура папок и файлов соблюдена в архиве, файлы плагина должны оказаться в <code>/assets/plugins/managermanager</code>)</p>
<p>7. Если вы хотите редактировать правила в панели управления сайтом, создайте чанк «mm_rules» (или с любым другим именем) и укажите его в параметре плагина «Configuration Chunk» (на вкладке «Конфигурация»). Если вы хотите редактировать правила в фале, редактируйте файл <code>/assets/plugins/managermanager/mm_rules.inc.php</code>. Внимание, параметр плагина «Configuration Chunk» должен быть пустым.</p>
<p class="alert alert-warning">Внимание, необходимо отключить плагин «ShowImageTVs» (если он у вас есть) и использовать вместо него виджет <code>mm_widget_showimagetvs</code></p>
<h3 class="sub-header text-bold"><a id="998"></a>Обновление</h3><p>Удалите все файлы из папки <code>/assets/plugins/managermanager/</code> и сам плагин ManagerManager, затем установите заново, следуя вышеописанным инструкциям.</p>
<h3 class="sub-header text-bold"><a id="999"></a>Виджеты</h3><p>Все виджеты уже содержатся в архиве, ничего дополнительно устанавливать не нужно</p>