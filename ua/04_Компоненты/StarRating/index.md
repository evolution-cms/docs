
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h3>Зірковий рейтинг для MODX Evolution </h3>
Відрізняється від основної збірки дуже гнучкими налаштуваннями (зображення зірок, оформлення і т.п.).
<h3 class="sub-header">Установка<a class="pull-right" data-toggle="tooltip" data-placement="left" title="СКАЧАТИ" href="assets/files/MODX-Evolution-Star-Rating-jquery.raty.zip.html"><i class="fa fa-lg fa-download"></i></a></h3>
<p>Створити новий сніппет з ім'ям <code>star_rating</code> і наступним вмістом:</p>
<pre class="brush: php;">
&lt;?php
return require MODX_BASE_PATH . 'assets/snippets/star_rating/snippet.php';
?&gt;
</pre>
<p>Створити новий модуль <code>Star Rating</code>, з наступним вмістом:</p>
<pre class="brush: php;">
include MODX_BASE_PATH . 'assets/snippets/star_rating/starrating.module.php';
</pre>
<p>Після створення модуля необхідно оновити сторінку щоб посилання на модуль появилось на вкладці <code>"Модулі"</code>. Далі якщо ви раніше не встановлювали цей компонент необхідно натиснути кнопку <code>"Установити"</code>.</p>
<h3 class="sub-header">Використання</h3>
<p>Приклад виклику сніппета:</p>
<pre class="brush: html;">
[!star_rating? &amp;id=`418` &amp;tpl=`@CHUNK:star_rating`!]
</pre>
<h3 class="sub-header">Параметри сніппета</h3>
<table class="table table-striped table-vcenter table-bordered table-condensed">
	<thead>
		<tr>
			<th>Параметр</th>
			<th class="text-center">За замовчуванням</th>
			<th>Опис</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><span class="text-bold">id</span></td>
			<td class="text-center"><code>[*id*]</code></td>
			<td>ID документа. Якщо не вказати буде використаний ID поточного документа</td>
		</tr>
		<tr>
			<td><span class="text-bold">tpl</span></td>
			<td class="text-center"><code>template</code></td>
			<td>Шаблон для виведення рейтинга. Для використання чанків MODX потрібно в імені чанка добавити приставку <code>@CHUNK:</code> як на прикладі</td>
		</tr>
		<tr>
			<td><span class="text-bold">lang</span></td>
			<td class="text-center"><code>ru</code></td>
			<td>Мова. Всі мови знаходятся в папці <code>/assets/snippets/star_rating/langs/</code></td>
		</tr>
		<tr>
			<td><span class="text-bold">interval</span></td>
			<td class="text-center"><code>86400</code></td>
			<td>Інтервал в секундах після закінчення котрого можна буде оставити голос знову</td>
		</tr>
		<tr>
			<td><span class="text-bold">noJs</span></td>
			<td class="text-center">-</td>
			<td>Якщо вказати <code>1</code> вбудовані скрипти не будуть виводитись на сторінку</td>
		</tr>
		<tr>
			<td><span class="text-bold">noCss</span></td>
			<td class="text-center">-</td>
			<td>Якщо вказати <code>1</code> вбудовані стилі не будуть виводитись на сторінку</td>
		</tr>
		<tr>
			<td><span class="text-bold">class</span></td>
			<td class="text-center">-</td>
			<td>Добавляє ваший css клас в шаблон <code>&lt;div class="star-rating-container[+class+]"&gt;</code>, вказувати без пробіла</td>
		</tr>
		<tr>
			<td><span class="text-bold">stars</span></td>
			<td class="text-center">5</td>
			<td>Кількість зірок рейтингу</td>
		</tr>
		<tr>
			<td><span class="text-bold">starOn</span></td>
			<td class="text-center">-</td>
			<td>Зображення заповненої зірки (вказувати тільки ім'я файла з розширенням)</td>
		</tr>
		<tr>
			<td><span class="text-bold">starOff</span></td>
			<td class="text-center">-</td>
			<td>Зображення не заповненої зірки (вказувати тільки ім'я файла з розширенням)</td>
		</tr>
		<tr>
			<td><span class="text-bold">starHalf</span></td>
			<td class="text-center">-</td>
			<td>Зображення напів-заповненої зірки (вказувати тільки ім'я файла з розширенням)</td>
		</tr>
		<tr>
			<td><span class="text-bold">imagesPath</span></td>
			<td class="text-center">-</td>
			<td>Шлях до папки із зображенням зірок. <code>starOn</code>, <code>starOff</code>, <code>starHalf</code> звязані з цим параметром</td>
		</tr>
		<tr>
			<td><span class="text-bold">readOnly</span></td>
			<td class="text-center"><code>false</code></td>
			<td>Забороняє можливість голосувати, тільки перегляд рейтингу</td>
		</tr>
		<tr>
			<td><span class="text-bold">starType</span></td>
			<td class="text-center"><code>img</code></td>
			<td>За замовчуванням <code>img</code>, якщо вказати <code>span</code> то замість зображень буде використовуватись шрифт із зірками</td>
		</tr>
	</tbody>
</table>
