
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Easy Newsletter: Установка</h2>

<p><span class="text-bold">Примечание:</span> В целях безопасности, прежде, чем устанавливать Easy Newsletter, не забудьте сделать резервную копию вашего сайта!</p>
<p>1. Скачайте последнюю версию <span class="text-bold">Easy Newsletter</span>.</p>
<p>2. Поместите папку <span class="text-bold">easynewsletter</span> из скаченного архива в папку "<em><span class="text-bold">assets/modules/</span></em>"</p>
<p>3. Создайте новый модуль с названием "<span class="text-bold">Easy Newsletter</span>", описанием "<span class="text-bold">&lt;strong&gt;0.3&lt;/strong&gt; Newsletter manager.</span>" и поместите в код модуля содержимое файла "<span class="text-bold">module.txt</span>".</p>
<p>4. Сохраните модуль. Теперь нам необходимо узнать <span class="text-bold">ID</span> созданного модуля. В Mozilla Firefox это делается следующим образом: зайдите в режим редактирования модуля и нажмите правую кнопку мышки и выберете пункт <em><span class="text-bold">В этом фрейме &gt;&gt; Открыть фрейм в новой вкладке</span></em>, в появившейся вкладке в адресной строке появится примерно следующая конструкция: "<span class="text-bold">index.php?a=108&id=3</span>", где "<span class="text-bold">&id=3</span>" это и есть указание на ID модуля. Запомните цифру 3, но у вас она может отличаться. Перейдите в конфигурацию модуля и в поле "<span class="text-bold">Конфигурация модуля:</span>" поместите следующий код:</p>
<pre class="brush: html;">&modId=Module ID;int;3 &path=Path;text;../assets/modules/easynewsletter/</pre>
<p>предварительно изменив цифру <span class="text-bold">3</span>, на <span class="text-bold">ID</span> вашего модуля, если он у вас отличается.</p>
<p>5. Сохраните модуль.</p>
<p>6. Выйдите из административной части и зайдите вновь.</p>
<p>7. Создайте новый сниппет "<span class="text-bold">easy newsletter</span>" с описанием "<span class="text-bold">&lt;strong&gt;0.3&lt;/strong&gt; Subscription for front end.</span>" и поместите в код сниппета содержимое файла "<span class="text-bold">snippet.txt</span>"</p>
<p>8. Поместите вызов сниппета в том месте вашего шаблона, где это необходимо:</p>
<pre class="brush: html;">[!easy newsletter!]</pre>