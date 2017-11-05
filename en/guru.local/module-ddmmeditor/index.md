
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>ddMMEditor</h2>

<h3>Модуль для удобного редактирования файла конфигурации плагина ManagerManager.</h3>
<p>Автор: <i class="fa fa-github fa-lg text-primary"></i> <a href="https://github.com/DivanDesign/MODXEvo.module.ddMMEditor" rel="nofollow" target="_blank">DivanDesign</a></p>
<h4>Возможности:</h4>
<ul>
<li>визуальное создание правил для MM;</li>
<li>применение правил к необходимым шаблонам и ролям в два клика;</li>
<li>autocomplete со всеми именами полей и TV;</li>
<li>объединение правил в группы по смыслу (группы можно называть произвольными именами);</li>
<li>сворачивание-разворачивание групп для удобного просмотра в общем виде;</li>
<li>drag'n'drop правил и групп между собой;</li>
<li>возможность «ручной» вставки произвольного кода в начало и конец конфигурационного файла.</li>
</ul>
<h4>Установка</h4>
<p>Содержимое файла module.php должно быть скопировано в поле «Код модуля» в меню создания нового модуля.</p>
Остальные файлы должны находиться в assets/modules/ddmmeditor/... (в архиве уже создана нужная структура папок).</p>
Модуль изменяет файл assets/plugins/managermanager/mm_rules.inc.php плагина ManagerManager.</p>
<em>Внимание! Чтобы ManagerManager использовал правила, созданные модулем, параметр «Configuration Chunk» в конфигурации плагина (вкладка «Конфигурация») должен быть пустым.</em></p>