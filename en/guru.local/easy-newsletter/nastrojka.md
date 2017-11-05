
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Easy Newsletter: Настройка</h2>

<h3 class="sub-header text-bold"><a id="1252"></a>Настройка языкового файла</h3><div class="well bordered-left bordered-blue"><p>1. В папке <em><span class="text-bold">/assets/modules/easynewsletter/languages/</span></em> находятся языковые файлы. Здесь уже есть файлы для датского, немецкого, итальянского и английского языков. Чтобы создать собственный языковой файл, скопируйте, например, файл english.php и переименуйте его в <span class="text-bold">russian.php</span>. Затем откройте файл r<span class="text-bold">ussian.php</span> и переведите его. Языковой файл для русского языка должен быть в кодировке <span class="text-bold">utf-8</span>.</p>
<p>2. Чтобы подключить файл русского языка, необходимо отредактировать файл <em><span class="text-bold">/assets/modules/easynewsletter/backend.php</span></em>, откройте этот файл и найдите эти строки, которые встречаются в коде дважды (<span class="text-bold">319-320 </span>и<span class="text-bold"> 331-332 </span>строки):</p>
<div class="well-box-shadow">
<pre class="brush: php;">
if(mysql_result($result,$i,"lang_frontend") == 'german'){$dropdown2 = ' selected="selected"';} else {$dropdown2 = '';}
$list .= '&lt;option value="german"'.$dropdown2.'&gt;Deutsch&lt;/option&gt;';
</pre>
</div>
<p>в первом блоке происходит подключение языкового файла для формы подписки, которая отображается на странице сайта, а во втором блоке для языка установленного модуля. Такие же конструкции используются для остальных языковых пакетов. Вставьте сразу после этих строк подключение собственного языкового пакета:</p>
<div class="well-box-shadow">
<pre class="brush: php;">
if(mysql_result($result,$i,"lang_backend") == 'russian'){$dropdown2 = ' selected="selected"';} else {$dropdown2 = '';}
$list .= '&lt;option value="russian"'.$dropdown2.'&gt;Русский&lt;/option&gt;';
</pre>
</div>
<p>Вы можете сами создать файл <span class="text-bold">russian.php</span> и отредактировать файл <span class="text-bold">backend.php</span>, либо скачайте уже готовые файлы по <a href="assets/files/easynewsletter/easynewsletter_rus.zip.html" target="_blank">этой ссылке</a>.</p></div>
<h3 class="sub-header text-bold"><a id="1253"></a>Настройка конфигурации модуля</h3><div class="well bordered-left bordered-blue"><p>Зайдите в модуль <em><span class="text-bold">Модули &gt;&gt; Easy Newsletter</span></em> и перейдите в раздел <span class="text-bold">Configuration</span>. В поле <span class="text-bold"><span class="text-bold">Language - website</span></span> выберите <span class="text-bold">Русский</span>, в поле <span class="text-bold">Language - manager</span> тоже выберите <span class="text-bold">Русский</span>. Сохраните изменения. Выйдите из модуля и зайдите занова, и если вы все сделали правильно, форма подписки и модуль будут теперь на русском языке.</p>
<p>Вновь зайдите в модуль <em><span class="text-bold">Модули &gt;&gt; Easy Newsletter</span></em> и перейдите в раздел Конфигурация, здесь вам необходимо заполнить поля <span class="text-bold">Имя отправителя, Электронная почта отправителя, Метод отправки писем</span> и настройки почтового сервера. Если вы не знаете, какие настройки выбрать, уточните информацию у вашего хостера.</p>
<div class="alert alert-info"><p><span class="text-bold">ВАЖНО!</span></p>
<p>Работа модуля может быть нестабильной при большом количестве подписчиков 1000 и более.</p>
<p>При создании рассылки вы не можете использовать жирный, курсивный и подчеркнутые шрифты.</p>
<p>Вы не сможете добавлять в рассылку картинки.</p></div></div>