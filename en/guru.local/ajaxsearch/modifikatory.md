
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>AjaxSearch: Модификаторы</h2>

<p>Служат для подключения изображений в результаты поиска. Применяются в шаблонах. Возможны следующие модификаторы:</p>
<h3 class="sub-header text-bold">imgwidth : ширина изображения</h3>
<pre class="brush: html;">&lt;img src="[+as.imgTag+]" width="[+as.imgTag:imgwidth+]" /&gt;</pre>
<h3 class="sub-header text-bold">imgheigth : высота изображения</h3>
<pre class="brush: html;">&lt;img src="[+as.imgTag+]" width="[+as.imgTag: imgheigth+]" /&gt;</pre>
<h3 class="sub-header text-bold">Imgattr : атрибуты изображения</h3>
<p>задает изображению атрибуты, такие как height="xxx" и width="yyy"</p>
<pre class="brush: html;">&lt;img src="[+as.imgTag +]" [+as.imgTag:imgattr+] /&gt;</pre>
<h3 class="sub-header text-bold">Imgmaxwidth : максимальная ширина изображения</h3>
<p>Ограничивает изображение по ширине. Не может быть больше истинной ширины.</p>
<pre class="brush: html;">&lt;img src="[+as.imgTag +]" width="[+as.imgTag:imgmaxwidth=`60`+]" /&gt;</pre>
<h3 class="sub-header text-bold">Imgmaxheight : максимальная высота изображения</h3>
<p>Ограничивает изображение по высоте. Не может быть больше истинной высоты.</p>
<pre class="brush: html;">&lt;img src="[+as.imgTag +]" width="[+as.imgTag:imgmaxheight=`90`+]" /&gt;</pre>