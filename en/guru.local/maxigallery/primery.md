
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>MaxiGallery: Примеры</h2>

<h3 class="sub-header text-bold"><a id="1121"></a>Загрузка изображений с помощью FTP</h3><div class="well bordered-left bordered-blue"><p>1. Определяем <span class="text-bold">ID галереи</span>, в которую необходимо закачать изображения. К примеру, эта галерея имеет ID <span class="text-bold">89</span>.</p>
<p>2. Создаем папку <em><span class="text-bold">/assets/galleries/89</span></em> если такой папки еще не существует. Если в этой галерее уже существует несколько изображений, загруженных через <span class="text-bold">MaxiGallery</span> то такая папка должна уже существовать.</p>
<p>3. Права на папку должны быть <span class="text-bold">777</span>.</p>
<p>4. Закачиваем в папку 89 изображения с помощью FTP.</p>
<p>5. Права на изображения должны быть <span class="text-bold">666</span>.</p>
<p>6. Переходим к управлению изображениями в MaxiGallery и нажимаем кнопку "<span class="text-bold">Пересинхронизировать Галерею</span>".</p></div>
<h3 class="sub-header text-bold"><a id="1122"></a>Простой вызов</h3><div class="well bordered-left bordered-blue"><p>Создайте новый документ в дереве документов MODx и поместите в нем вызов сниппета:</p>
<pre class="brush: html;">[!MaxiGallery!]</pre>
<div class="alert alert-info">
<p><span class="text-bold">Примечание:</span> управление изображениями галереи (загрузка, сортировка, удаление) осуществляется не в административной панели а на странице с выводом галереи .</p>
</div>
<p>При таком вызове на странице галереи отобразится кнопка для управления изображениями: "<span class="text-bold">Manage pictures</span>". Эта кнопка будет видна только авторизованным пользователям. Нажав на эту кнопку вы попадете на страницу с формой загрузки изображений. Все изображения загружаются в папку <em><span class="text-bold">assets/galleries/ID-галереи/</span></em> где <em><span class="text-bold">ID-галереи</span></em> - это ID документа MODx, в котором помещен вызов галереи.</p></div>
<h3 class="sub-header text-bold"><a id="1123"></a>Вызов с дополнительными параметрами</h3><div class="well bordered-left bordered-blue"><pre class="brush: html;">[!MaxiGallery? &lang=`ru-utf8` &display=`embedded` &embedtype=`slimbox` &pics_per_row=`3` &max_thumb_size=`110` &max_pic_size=`0` &thumb_use_dropshadow=`1`!]</pre>
<p>где:</p>
<ul>
<li><code>&lang=`ru-utf8`</code> - подключаем языковой файл (см. Русский язык в MaxiGallery) По умолчанию <code>en</code>.</li>
<li><code>&display=`embedded`</code> - выбираем тип галереи (по умолчанию <code>normal</code>).</li>
<li><code>&embedtype=`slimbox`</code> - выбираем эффект смены изображений (только для типа галереи <code>embedded</code>).</li>
<li><code>&pics_per_row=`3`</code> - определяем количество эскизов в одном ряду (по умолчанию <code>4</code>).</li>
<li><code>&max_thumb_size=`110`</code> - выбираем размер эскиза (по умолчанию <code>130</code>).</li>
<li><code>&max_pic_size=`0`</code> - устанавливаем размер нормального изображения как оригинальное (по умолчанию <code>450</code>).</li>
<li><code>&thumb_use_dropshadow=`1`</code> - включаем отображение тени у эскизов.</li>
</ul></div>
<h3 class="sub-header text-bold"><a id="1124"></a>Добавляем водяные знаки</h3><div class="well bordered-left bordered-blue">
<pre class="brush: html;">
[!MaxiGallery?
&lang=`ru-utf8`
&pics_per_row=`3`
&max_thumb_size=`110`
&max_pic_size=`400`
&keep_bigimg=`1`
&big_img_linkstyle=`popup`
&pic_use_watermark=`1`
&pic_watermark_type=`image`!]
</pre>
<p>где:</p>
<ul>
<li><code>&keep_bigimg=`1`</code> - сохраняем оригинал изображения.</li>
<li><code>&big_img_linkstyle=`popup`</code> - выбираем способ отображения больших изображений.</li>
<li><code>&pic_use_watermark=`1`</code> - включаем использование водяных знаков для изображений нормального размера.</li>
<li><code>&pic_watermark_type=`image`</code> - устанавливаем тип водяного знака для нормальных изображений в виде картинки. Мы можем использовать собственную картинку для водяного знака, указав к ней путь с помощью параметра <code>&pic_watermark_img=`путь к картинке`</code>.</li>
</ul></div>
<h3 class="sub-header text-bold"><a id="1125"></a>Вывод дочерних галерей</h3><div class="well bordered-left bordered-blue"><p>Создадим в папке <span class="text-bold">Галереи</span> несколько дочерних галерей <span class="text-bold">Галерея 1</span>, <span class="text-bold">Галерея 2</span> и т.д. и загрузим фотографии. Мы можем вывести список всех дочерних галерей разместив в родительской папке <span class="text-bold">Галереи</span> такой вызов сниппета.</p>
<pre class="brush: html;">[!MaxiGallery? &lang=`ru-utf8` &display=`childgalleries` &childgalleries_ids=`all` &order_by=`random` &childgalleries_order_by=`createdon`!]</pre>
<p>где:</p>
<ul>
<li><code>&display=`childgalleries`</code> - определяем тип галереи.</li>
<li><code>&childgalleries_ids=`all`</code> - включаем отображение всех дочерних галерей. Мы также можем указать только определенные галереи, указав список ID галерей через запятую.</li>
<li><code>&order_by=`random`</code> - включаем отображение случайного изображения из дочерней галереи.</li>
<li><code>&childgalleries_order_by=`createdon`</code> - поле, по которому сортируются дочерние галереи.</li>
</ul></div>
<h3 class="sub-header text-bold"><a id="1126"></a>Вывод заданных дочерних галерей</h3><div class="well bordered-left bordered-blue"><pre class="brush: html;">[!MaxiGallery? &lang=`ru-utf8`&display=`childgalleries` &childgalleries_ids=`67,5`!]</pre>
<p>где:</p>
<ul>
<li><code>&childgalleries_ids=`67,5`</code> - задаем ID галерей, которые необходимо вывести.</li>
</ul></div>
<h3 class="sub-header text-bold"><a id="1127"></a>Фотоблог с Jot</h3><div class="well bordered-left bordered-blue"><p>1. Создайте новый чанк, например, mgPictureTplComment и поместите в него код из файла maxigallery/templates/picturetpl.html.</p>
<p>2. В этот шаблон добавьте вызов Jot (вы можете изменять все параметры сниппета, кроме &tagid):</p>
<pre class="brush: html;">
[[Jot?
&subscribe=`1`
&tagid=`[+maxigallery.picture.id+]`
&pagination=`10`
&badwords=`something`
&customfields=`name,email`
&canmoderate=`Jot Moderators`
&trusted=`Jot Trusted Users`]]
</pre>
<p>3. Создайте новую галерею и поместите такой вызов сниппета (добавьте к вызову любые параметры, которые вы хотите):</p>
<pre class="brush: html;">[!MaxiGallery? &pictureTpl=`mgPictureTplComment`!]</pre></div>
<h3 class="sub-header text-bold"><a id="1128"></a>Изображения и эскизы на одной странице</h3><div class="well bordered-left bordered-blue"><p>Этот пример показывает, как сделать собственный шаблон, чтобы получить эскизы и картины в одном документе и добавить изменение изображения с помощью JavaScript.</p>
<p>1. Создаем вызов сниппета, отображающий список эскизов:</p>
<pre class="brush: html;">[!MaxiGallery? &galleryPictureTpl=`mgGalleryPicture` &js=`mgJs`!]</pre>
<p>2. Создаем чанк mgGalleryPicture , который будет использоваться при просмотре эскизов:</p>
<pre class="brush: html;">
&lt;li&gt;
	 &lt;a href="javascript:void(0);"onClick="javascript:showPic('[(base_url)][+maxigallery.path_to_gal+][+maxigallery.picture.filename+]','[+maxigallery.picture.title:htmlent+]','[+maxigallery.picture.descr:htmlent+]',[+maxigallery.picture_width_normal+],[+maxigallery.picture_height_normal+]);return false;"&gt;
		&lt;img src="[(base_url)][+maxigallery.path_to_gal+]tn_[+maxigallery.picture.filename+]" class="thumbnail" title="[+maxigallery.picture.title:htmlent+]" alt="[+maxigallery.picture.title:htmlent+]" /&gt;
	 &lt;/a&gt;
&lt;/li&gt;
</pre>
<p>3. Создаем чанк mgJs с JavaScript, котрый будем использовать для переключения изображений. (Можно также создать его как внешний файл .js и определить путь к нему в параметре &js):</p>
<pre class="brush: javascript;">
&lt;script type="text/javascript"&gt;
	function showPic(url,title,descr,width,height) {
		var img = document.getElementById('maxImage');
		var titleHolder = document.getElementById('maxTitle');
		var descrHolder = document.getElementById('maxDescr');
		var newImg = new Image();
		newImg.onLoad = doImage(img,url,width,height);
		if (titleHolder != null) {
			for (var i = 0; i &lt; titleHolder.childNodes.length; i++) {
				titleHolder.removeChild(titleHolder.childNodes[i]);
			};
			if (title != "") {
				var node=document.createTextNode(title);
			}
			else {
				var node=document.createTextNode("");
			}
			titleHolder.appendChild(node);
		}
		if (descrHolder != null) {
			for (var i = 0; i &lt; descrHolder.childNodes.length; i++) {
				descrHolder.removeChild(descrHolder.childNodes[i]);
			};
			if (descr != "") {
				var node=document.createTextNode(descr);
			}
			else {
				var node=document.createTextNode("");
			}
			descrHolder.appendChild(node);
		}
	}
	 
	function doImage(img,url,width,height) {
		img.src=url;
	}
&lt;/script&gt;
</pre>
<p>4. Создаем еще один вызов снипеета, чтобы показать изображение. Мы используем параметр &display=`pictureview`, чтобы показывать изображение в режиме просмотра по умолчанию. Если вы используете какие-то другие параметры сортировки, чем использующиеся по умолчанию, добавьте их в этот вызов сниппета, так он получает первое изображение автоматически.</p>
<pre class="brush: html;">[!MaxiGallery? &pictureTpl=`mgPicture` &display=`pictureview`!]</pre>
<p>5. Создаем чанк mgPicture для показа одного изображения:</p>
<pre class="brush: html;">
&lt;div class="picturecontainer"&gt;
	 &lt;img id="maxImage" src="[(base_url)][+maxigallery.path_to_gal+][+maxigallery.picture.filename+]" alt="[+maxigallery.picture.title:htmlent+]" /&gt;
	 &lt;p id="maxTitle"&gt;[+maxigallery.picture.title:htmlent+]&lt;/p&gt;
	 &lt;p id="maxDescr"&gt;[+maxigallery.picture.descr:htmlent+]&lt;/p&gt;
&lt;/div&gt;
</pre></div>
<h3 class="sub-header text-bold"><a id="1129"></a>Всплывающее окно с эскизами</h3><div class="well bordered-left bordered-blue"><p>Этот пример показывает, как сделать всплывающее окно с эскизами изображений, которое имеет prev/next ссылки.</p>
<p>1. Создайте новый документ для всплывающего окна. Выберите шаблон blank, снимите флажок с Показывать в меню. В содержимое документа поместите следующий код:</p>
<pre class="brush: html;">
&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en"&gt;
	&lt;head&gt;
		&lt;meta http-equiv="content-type" content="text/html; charset=iso-8859-1" /&gt;
		&lt;base href="[(site_url)]" /&gt;
		&lt;title&gt;[(site_name)] | [*pagetitle*]&lt;/title&gt;
	&lt;/head&gt;
&lt;body
	[!MaxiGallery? &is_target=`1`!]
&lt;/body&gt;
&lt;/html&gt;
</pre>
<p>2. Создайте новый документ для показа эскизов и поместите в него ттакой вызов сниппета. Замените &lt;docid&gt; на идентификатором документа, который вы сделали в шаге 1:</p>
<pre class="brush: html;">
[!MaxiGallery? &js=`mgJs` &galleryPictureTpl=`mgGalleryPicture` &picture_target=`&lt;docid&gt;`!]
</pre>
<p>3. Создать чанк mgJs, содержащий JavaScript, открывающий всплывающее окно. Измените ширину и высоту окна на необходимые:</p>
<pre class="brush: javascript;">
&lt;script type="text/javascript"&gt;
	function openWindow(URL) {
		var day = new Date();
		var id = day.getTime();
		var width=600;
		var height=600;
		var left = Math.floor( (screen.width - width) / 2);
		var top = Math.floor( (screen.height - height) / 2);
		var str = "page" + id + " = window.open('" + URL + "', '" + id +
	"','toolbar=0,scrollbars=0,location=0,statusbar=0,menubar=0,resizable=0,width="
	+ width + ",height=" + height + ",left=" + left + ",top=" + top +
	"');";
		 eval(str);
		 if (window.focus) {eval("page"+id+".focus();");}
	}
&lt;/script&gt;
</pre>
<p>4. Создайте чанк mgGalleryPicture с шаблоном, который будет использоваться при просмотре эскизов:</p>
<pre class="brush: html;">
&lt;li&gt;
	&lt;a href="javascript:void(0);"onClick="javascript:openWindow('[+maxigallery.picture_link_url+]');return false;"&gt;
		&lt;img src="[(base_url)][+maxigallery.path_to_gal+]tn_[+maxigallery.picture.filename+]" class="thumbnail" title="[+maxigallery.strings.click_to_zoom+]" alt="[+maxigallery.picture.title:htmlent+]" /&gt;
	 &lt;/a&gt;
	 &lt;p style="width: [+maxigallery.picture_width_thumb+]px;"&gt;
		[+maxigallery.picture.title:htmlent+]
	 &lt;/p&gt;
&lt;/li&gt;
</pre>
</div>