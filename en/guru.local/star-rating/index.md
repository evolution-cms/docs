
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>Star Rating</h2>

<h3 class="sub-header">Установка<a class="pull-right" data-toggle="tooltip" data-placement="left" title="СКАЧАТЬ" href="assets/files/MODX-Evolution-Star-Rating-jquery.raty.zip.html"><i class="fa fa-lg fa-download"></i></a></h3>
<p>Создать новый сниппет с именем <code>star_rating</code> и следующим содержимым:</p>
<pre class="brush: php;">
&lt;?php
return require MODX_BASE_PATH . 'assets/snippets/star_rating/snippet.php';
?&gt;
</pre>
<p>Создать новый модуль <code>Star Rating</code>, со следующим содержимым:</p>
<pre class="brush: php;">
include MODX_BASE_PATH . 'assets/snippets/star_rating/starrating.module.php';
</pre>
<p>После создания модуля необходимо обновить страницу чтобы ссылка на модуль появилась на вкладке <code>"Модули"</code>. Далее если вы ранее не устанавливали этот компонент необходимо нажать кнопку <code>"Установить"</code>.</p>
<h3 class="sub-header">Использование</h3>
<p>Пример вызова сниппета:</p>
<pre class="brush: html;">
[!star_rating? &amp;id=`418` &amp;tpl=`@CHUNK:star_rating`!]
</pre>
<h3 class="sub-header">Параметры сниппета</h3>
<table class="table table-striped table-vcenter table-bordered table-condensed">
	<thead>
		<tr>
			<th>Параметр</th>
			<th class="text-center">По умолчанию</th>
			<th>Описание</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><span class="text-bold">id</span></td>
			<td class="text-center"><code>[*id*]</code></td>
			<td>ID документа. Если не указать будет использован ID текущего документа</td>
		</tr>
		<tr>
			<td><span class="text-bold">tpl</span></td>
			<td class="text-center"><code>template</code></td>
			<td>Шаблон для вывода рейтинга. Для использования чанков MODX следует у имени чанка добавить приставку <code>@CHUNK:</code> как на примере</td>
		</tr>
		<tr>
			<td><span class="text-bold">lang</span></td>
			<td class="text-center"><code>ru</code></td>
			<td>Язык. Все языки находятся в папке <code>/assets/snippets/star_rating/langs/</code></td>
		</tr>
		<tr>
			<td><span class="text-bold">interval</span></td>
			<td class="text-center"><code>86400</code></td>
			<td>Интервал в секундах по итечении которого можно будет оставить голос снова</td>
		</tr>
		<tr>
			<td><span class="text-bold">noJs</span></td>
			<td class="text-center">-</td>
			<td>Если указать <code>1</code> встроенные скрипты не будут выводиться на страницу</td>
		</tr>
		<tr>
			<td><span class="text-bold">noCss</span></td>
			<td class="text-center">-</td>
			<td>Если указать <code>1</code> встроенные стили не будут выводиться на страницу</td>
		</tr>
		<tr>
			<td><span class="text-bold">class</span></td>
			<td class="text-center">-</td>
			<td>Добавляет ваш css класс в шаблон <code>&lt;div class="star-rating-container[+class+]"&gt;</code>, указывать без пробела</td>
		</tr>
		<tr>
			<td><span class="text-bold">stars</span></td>
			<td class="text-center">5</td>
			<td>Количество звезд рейтинга</td>
		</tr>
		<tr>
			<td><span class="text-bold">starOn</span></td>
			<td class="text-center">-</td>
			<td>Изображение заполненной звезды (указывать только имя файла с расширением)</td>
		</tr>
		<tr>
			<td><span class="text-bold">starOff</span></td>
			<td class="text-center">-</td>
			<td>Изображение не заполненной звезды (указывать только имя файла с расширением)</td>
		</tr>
		<tr>
			<td><span class="text-bold">starHalf</span></td>
			<td class="text-center">-</td>
			<td>Изображение полу-заполненной звезды (указывать только имя файла с расширением)</td>
		</tr>
		<tr>
			<td><span class="text-bold">imagesPath</span></td>
			<td class="text-center">-</td>
			<td>Путь к папке с изображениями звезд. <code>starOn</code>, <code>starOff</code>, <code>starHalf</code> связыны с этим параметром</td>
		</tr>
		<tr>
			<td><span class="text-bold">readOnly</span></td>
			<td class="text-center"><code>false</code></td>
			<td>Запрещает возможность голосовать, только просмотр рейтинга</td>
		</tr>
		<tr>
			<td><span class="text-bold">starType</span></td>
			<td class="text-center"><code>img</code></td>
			<td>По умолчанию <code>img</code>, если указать <code>span</code> то вместо изображений будет использоваться шрифт со звездами</td>
		</tr>
	</tbody>
</table>