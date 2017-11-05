
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>MaxiGallery: Параметры</h2>

<div class="panel-group accordion">				
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="460"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse460"><span class="text-bold">&admin_webgroups</span> - Названия групп веб-пользователей с администраторскими правами, которые могут редактировать все галлереи.</a></h4>
		</div>
		<div id="collapse460" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Разделённые запятой названия групп веб пользователей<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> Разделённые запятой названия групп веб пользователей<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&admin_webgroups=`manager`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="461"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse461"><span class="text-bold">&admin_webusers</span> - Веб-пользователи с администраторскими правами, которым разрешено редактировать все галлереи</a></h4>
		</div>
		<div id="collapse461" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Разделённые запятой имена веб-пользователей 	<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> Разделённые запятой имена веб-пользователей<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&admin_webusers=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="462"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse462"><span class="text-bold">&big_img_linkstyle</span> - Описывает способ отображения Больших картинок</a></h4>
		</div>
		<div id="collapse462" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> slidebox | lightboxv2 | popup | external <br>
				<span class="text-bold">Значение по умолчанию:</span> external<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_img_linkstyle=`popup`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="463"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse463"><span class="text-bold">&big_mask_bgcolor</span> - Маска цвета заднего фона для больших картинок. </a></h4>
		</div>
		<div id="collapse463" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal <br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF<br>
				<span class="text-bold">Примечание:</span> Должна быть того же цвета что и задний фон.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_mask_bgcolor=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="464"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse464"><span class="text-bold">&big_mask_img</span> - Путь к imagemask для больших изображений</a></h4>
		</div>
		<div id="collapse464" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets/ maxigallery/ imagemask/ demomask–frame2.png <br>
				<span class="text-bold">Примечание:</span> Путь к изображению которые вы хотели бы использовать как imagemask для больших изображений (Изображение - водяной знак).<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_mask_img=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="465"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse465"><span class="text-bold">&big_mask_position </span> - Позиция Imagemask</a></h4>
		</div>
		<div id="collapse465" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | topleft | topright | left | center | right | bottom | bottomleft | bottomright | resize<br>
				<span class="text-bold">Значение по умолчанию:</span> resize<br>
				<span class="text-bold">Примечание:</span> Расположение Изображение - водяной знак для больших картинок.
				Опция resize изменяет размер imagemask до размера изображения.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_mask_position =`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="466"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse466"><span class="text-bold">&big_shadow_bgcolor</span> - Цвет тени для больших изображений</a></h4>
		</div>
		<div id="collapse466" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal<br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF <br>
				<span class="text-bold">Примечание:</span> Должен быть таким же, как и цвет фона страницы.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_shadow_bgcolor=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="467"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse467"><span class="text-bold">&big_shadow_path</span> - Путь к вашему изображению заднего фона</a></h4>
		</div>
		<div id="collapse467" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/dropshadow/<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_shadow_path=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="468"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse468"><span class="text-bold">&big_use_dropshadow</span> - Отбрасывание тени для больших изображений.</a></h4>
		</div>
		<div id="collapse468" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_use_dropshadow=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="469"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse469"><span class="text-bold">&big_use_imagemask</span> - Использовать imagemask для больших изображений</a></h4>
		</div>
		<div id="collapse469" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_use_imagemask=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="470"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse470"><span class="text-bold">&big_use_watermark </span> - Использовать Watermark (водяные знаки) для больших изображений.</a></h4>
		</div>
		<div id="collapse470" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_use_watermark =`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="471"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse471"><span class="text-bold">&big_watermark_font</span> - Размер шрифта для водяных знаков.</a></h4>
		</div>
		<div id="collapse471" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 1 | 2 | 3 | 4 | 5<br>
				<span class="text-bold">Значение по умолчанию:</span> 5<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_font=`3`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="472"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse472"><span class="text-bold">&big_watermark_halign</span> - Горизонтальное выравнивание водяных знаков.</a></h4>
		</div>
		<div id="collapse472" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> left | center | right<br>
				<span class="text-bold">Значение по умолчанию:</span> right<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_halign=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="473"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse473"><span class="text-bold">&big_watermark_img</span> - Путь к изображению с водяными знаками.</a></h4>
		</div>
		<div id="collapse473" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets/ maxigallery/watermark/ watermark.png <br>
				<span class="text-bold">Примечание:</span> Изображение может быть прозрачным PNG. <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_img=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="474"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse474"><span class="text-bold">&big_watermark_txt </span> - Для текстовых водяных знаков. Текст будет наложен на картинку.</a></h4>
		</div>
		<div id="collapse474" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> текст<br>
				<span class="text-bold">Значение по умолчанию:</span> Copyright &lt;YEAR&gt; &lt;SITENAME&gt;<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_txt =``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="475"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse475"><span class="text-bold">&big_watermark_txt_color</span> - Цвет текста водяного знака.</a></h4>
		</div>
		<div id="collapse475" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal<br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_txt_color=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="476"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse476"><span class="text-bold">&big_watermark_txt_hmargin</span> - Горизонтальное расположение текстового водяного знака (в pixels).</a></h4>
		</div>
		<div id="collapse476" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 15<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_txt_hmargin=`25`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="477"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse477"><span class="text-bold">&big_watermark_txt_vmargin</span> - Вертикальное расположение текстового водяного знака (в pixels).</a></h4>
		</div>
		<div id="collapse477" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 15<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_txt_vmargin=`25`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="478"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse478"><span class="text-bold">&big_watermark_type</span> - Тип водяного знака: Текстовый или изображение </a></h4>
		</div>
		<div id="collapse478" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> text | image<br>
				<span class="text-bold">Значение по умолчанию:</span> text <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_type=`image`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="479"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse479"><span class="text-bold">&big_watermark_valign</span> - Вертикальное выравнивание водяных знаков.</a></h4>
		</div>
		<div id="collapse479" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | center | bottom<br>
				<span class="text-bold">Значение по умолчанию:</span> bottom<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&big_watermark_valign=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="480"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse480"><span class="text-bold">&childgalleries_ids</span> - Родительская галерея, отображает дочерние галлереи.</a></h4>
		</div>
		<div id="collapse480" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ID документов, через запятую | all<br>
				<span class="text-bold">Значение по умолчанию:</span> Текущий документ<br>
				<span class="text-bold">Примечание:</span> <br>Разделяемый запятыми список ID для поиска галерей в них.<br>
				"all" отобразить все галереи.
				<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&childgalleries_ids=`all`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="481"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse481"><span class="text-bold">&childgalleries_level_limit</span> - Определяет сколько уровней из родительской галереи перечислить</a></h4>
		</div>
		<div id="collapse481" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> Ноль - все уровни.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&childgalleries_level_limit=`3`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="482"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse482"><span class="text-bold">&childgalleries_limit</span> - Определяет сколько дочерних галерей необходимо отобразить</a></h4>
		</div>
		<div id="collapse482" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> Значение 0 служит для вывода всех дочерних галерей.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&childgalleries_limit=`10`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="483"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse483"><span class="text-bold">&childgalleries_order_by </span> - Имя поля по которому нужно произвести сортировку галерей</a></h4>
		</div>
		<div id="collapse483" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> поле документа<br>
				<span class="text-bold">Значение по умолчанию:</span> menuindex<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&childgalleries_order_by =`pagetitle`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="484"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse484"><span class="text-bold">&childgalleries_order_direction</span> - Направление сортировки дочерних галерей</a></h4>
		</div>
		<div id="collapse484" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ASC | DESC<br>
				<span class="text-bold">Значение по умолчанию:</span> ASC<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&childgalleries_order_direction=`DESC`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="485"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse485"><span class="text-bold">&childgalleryTpl</span> - Шаблон используемый для отображения дочерней галереи</a></h4>
		</div>
		<div id="collapse485" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets /maxigallery/templates /childgallerytpl.html <br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;
				<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&childgalleryTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="486"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse486"><span class="text-bold">&clearerTpl</span> - Шаблон используемый при использовании параметра pics_per_row.</a></h4>
		</div>
		<div id="collapse486" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets /maxigallery/templates /clearertpl.html<br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&clearerTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="487"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse487"><span class="text-bold">&css</span> - Путь к стилю (css) используему для оформления галереи, или имя чанка, содержащего css, или css код</a></h4>
		</div>
		<div id="collapse487" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets/maxigallery/ css/default.css <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&css=`MaxigalleryCss`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="488"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse488"><span class="text-bold">&debug</span> - Показывает некоторую отладочную информацию на странице MaxiGallery</a></h4>
		</div>
		<div id="collapse488" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> функция до конца не реализована<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&debug=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="489"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse489"><span class="text-bold">&disable_js_libs</span> - Отключение библиотек MooTools, Prototype или Scriptaculous javascript</a></h4>
		</div>
		<div id="collapse489" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> Используется когда MooTools, Prototype или Scriptaculous javascript библиотеки вызваны в заголовке шаблона сайта и вы хотите чтобы MaxiGallery не подгружал свои копии этих библиотек.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&disable_js_libs=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="490"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse490"><span class="text-bold">&disable_rightclick</span> - Включает javascript отключающий 'правый клик', чтобы не было возможности сохранять картинки.</a></h4>
		</div>
		<div id="collapse490" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&disable_rightclick=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="491"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse491"><span class="text-bold">&display</span> - Выбор типа галереи</a></h4>
		</div>
		<div id="collapse491" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> normal | embedded | childgalleries | pictureview<br>
				<span class="text-bold">Значение по умолчанию:</span> normal<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&display=`pictureview`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="492"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse492"><span class="text-bold">&draggableTpl</span> - Шаблон для попап окна ручной сортировки (перетаскивания мышью) фотографий альбома.</a></h4>
		</div>
		<div id="collapse492" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:assets/snippets /maxigallery/templates /draggabletpl.html <br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;
				<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&draggableTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="493"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse493"><span class="text-bold">&embedtype</span> - Тип просмотра галереи</a></h4>
		</div>
		<div id="collapse493" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> slidebox | lightboxv2 | slimbox | smoothgallery | popup | external<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> Если в display указан параметр "embedded", этим параметром можно регулировать эффекты. "External" откроет картинку на другой странице.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&embedtype=`external`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="494"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse494"><span class="text-bold">&ftp_base_dir</span> - Путь для FTP до корня установленного MODx. </a></h4>
		</div>
		<div id="collapse494" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> /<br>
				<span class="text-bold">Примечание:</span> Например, если корневой каталог для FTP /home/username/ и MODx установлен в папке /home/username/public_html/modx/ то в качестве значения парметра ftp_base_dir укажите /public_html/modx/<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&ftp_base_dir=`/public_html/modx/`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="495"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse495"><span class="text-bold">&ftp_pass</span> - Пароль учетной записи FTP</a></h4>
		</div>
		<div id="collapse495" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> пароль<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&ftp_pass=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="496"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse496"><span class="text-bold">&ftp_port</span> - Номер порта для службы FTP.</a></h4>
		</div>
		<div id="collapse496" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 21<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&ftp_port=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="497"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse497"><span class="text-bold">&ftp_server</span> - FTP-адрес сервера под управлением MODx.</a></h4>
		</div>
		<div id="collapse497" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> FTP-адрес<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&ftp_server=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="498"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse498"><span class="text-bold">&ftp_user</span> - Имя пользователя учетной записи FTP</a></h4>
		</div>
		<div id="collapse498" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> имя пользователя<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&ftp_user=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="499"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse499"><span class="text-bold">&gal_query_ids</span> - Идентификаторы документов, из которых вы хотите получить фотографии.</a></h4>
		</div>
		<div id="collapse499" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ID документов, через запятую | all<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>Список ID документов, разделенный запятыми
				<br>"all" - все документы<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&gal_query_ids=`all`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="500"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse500"><span class="text-bold">&galleryOuterTpl</span> - Внешний шаблон для краткого обзора галереи</a></h4>
		</div>
		<div id="collapse500" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /galleryoutertpl.html<br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;
				<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&galleryOuterTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="501"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse501"><span class="text-bold">&galleryPictureTpl</span> - Шаблон для каждого изображения (эскиза) при обзоре галереи.</a></h4>
		</div>
		<div id="collapse501" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /gallerypicturetpl.html <br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&galleryPictureTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="502"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse502"><span class="text-bold">&gtable</span> - Название таблицы базы данных для галереи</a></h4>
		</div>
		<div id="collapse502" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> строка<br>
				<span class="text-bold">Значение по умолчанию:</span> maxigallery <br>
				<span class="text-bold">Примечание:</span> К таблице MODx добавляется префикс<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&gtable=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="503"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse503"><span class="text-bold">&is_target</span> - Determines if the document is to be the target for picture browsing mode or picture manager mode. </a></h4>
		</div>
		<div id="collapse503" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&is_target=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="504"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse504"><span class="text-bold">&js</span> - Ссылка на дополнительный javascript</a></h4>
		</div>
		<div id="collapse504" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&js=`&lt;scripttype="text/javascript"&gt; alert(hello);&lt;/script&gt;`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="505"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse505"><span class="text-bold">&keep_bigimg</span> - Сохранять оригинал изображения.</a></h4>
		</div>
		<div id="collapse505" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&keep_bigimg=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="506"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse506"><span class="text-bold">&keep_date</span> - При изменении названия изображения или описания, сохранить первоначальную дату загрузки.</a></h4>
		</div>
		<div id="collapse506" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 1<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&keep_date=`0`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="507"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse507"><span class="text-bold">&lang</span> - Устанавливает язык галереи</a></h4>
		</div>
		<div id="collapse507" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> en | fi <br>
				<span class="text-bold">Значение по умолчанию:</span> en<br>
				<span class="text-bold">Примечание:</span> Языковые файлы не полностью реализованы. Не стесняйтесь добавлять собственные языки. (См. lang_en.php для примера.)<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&lang=`ru`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="508"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse508"><span class="text-bold">&limit</span> - Максимальное количество строк для запроса.</a></h4>
		</div>
		<div id="collapse508" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 9999999<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&limit=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="509"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse509"><span class="text-bold">&manage_gallery</span> - Идентификатор галереи, подлежащей обработке.</a></h4>
		</div>
		<div id="collapse509" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ID документа<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manage_gallery=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="510"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse510"><span class="text-bold">&manage_target</span> - Идентификатор документа, который будет использоваться для управления картинками</a></h4>
		</div>
		<div id="collapse510" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ID документа<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manage_target=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="511"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse511"><span class="text-bold">&manageOuterTpl</span> - Внешний шаблон для управления галереей</a></h4>
		</div>
		<div id="collapse511" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /manageoutertpl.html<br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manageOuterTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="512"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse512"><span class="text-bold">&managePictureTpl</span> - Шаблон для одного элемента изображения в управлении галереей.</a></h4>
		</div>
		<div id="collapse512" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /managepicturetpl.html<br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&managePictureTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="513"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse513"><span class="text-bold">&manager_webgroups</span> - Разделенный запятыми список веб-групп, которые могут размещать фотографии в эту галерею</a></h4>
		</div>
		<div id="collapse513" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> список веб-групп пользователей через запятую<br>
				<span class="text-bold">Значение по умолчанию:</span> <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manager_webgroups=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="514"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse514"><span class="text-bold">&manager_webusers</span> - Веб-пользователи, которым разрешено редактировать галлерею</a></h4>
		</div>
		<div id="collapse514" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Разделённые запятой имена веб-пользователей 	<br>
				<span class="text-bold">Значение по умолчанию:</span> <br>
				<span class="text-bold">Примечание:</span> Разделённые запятой имена веб-пользователей<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manager_webusers=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="515"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse515"><span class="text-bold">&manageButtonTpl</span> - Шаблон для кнопки управления фотографиями.</a></h4>
		</div>
		<div id="collapse515" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /managebuttontpl.html <br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manageButtonTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="516"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse516"><span class="text-bold">&manageUploadTpl</span> - Шаблон для загрузки файла в управлении галереей</a></h4>
		</div>
		<div id="collapse516" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь | имя чанка | строка<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /manageuploadtpl.html<br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&manageUploadTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="517"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse517"><span class="text-bold">&max_big_size</span> - Размер большого изображения</a></h4>
		</div>
		<div id="collapse517" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px) | WidthxHeight (px) (например 200x400) | 0<br>
				<span class="text-bold">Значение по умолчанию:</span> 1024<br>
				<span class="text-bold">Примечание:</span> Желаемый размер изображения в пикселях, или ноль для использования оригинального размера изображения<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&max_big_size=`200x400`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="518"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse518"><span class="text-bold">&max_pic_number</span> - Максимальное количество изображений разрешенных в этой галерее</a></h4>
		</div>
		<div id="collapse518" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число | 0<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> 0 - неограниченное количество изображений<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&max_pic_number=`25`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="519"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse519"><span class="text-bold">&max_pic_size</span> - Размер среднего (нормального) изображения</a></h4>
		</div>
		<div id="collapse519" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px) | WidthxHeight (px) (например 200x400) | 0<br>
				<span class="text-bold">Значение по умолчанию:</span> 450<br>
				<span class="text-bold">Примечание:</span> 0 - оригинальный размер изображения<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&max_pic_size=`0`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="520"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse520"><span class="text-bold">&max_thumb_size</span> - Размер маленького изображения (превью)</a></h4>
		</div>
		<div id="collapse520" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px) | WidthxHeight (px) (например 200x400) | 0<br>
				<span class="text-bold">Значение по умолчанию:</span> 130<br>
				<span class="text-bold">Примечание:</span> 0 - оригинальный размер изображения<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&max_thumb_size=`0`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="603"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse603"><span class="text-bold">&offset</span> - Offset value to use for the query result set. </a></h4>
		</div>
		<div id="collapse603" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> Количество строк, которые нужно пропустить<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&offset=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="604"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse604"><span class="text-bold">&order_by</span> - Имя поля базы данных, по которой сортируются изображения</a></h4>
		</div>
		<div id="collapse604" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> date, pos, filename, title, id, random <br>
				<span class="text-bold">Значение по умолчанию:</span> pos,date <br>
				<span class="text-bold">Примечание:</span> <br>date
				<br>pos
				<br>filename
				<br>title
				<br>id
				<br>random - случайный порядок<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&order_by=`random`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="605"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse605"><span class="text-bold">&order_direction</span> - Направление сортировки</a></h4>
		</div>
		<div id="collapse605" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ASC | DESC<br>
				<span class="text-bold">Значение по умолчанию:</span> DESC<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&order_direction=`ASC`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="606"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse606"><span class="text-bold">&pageNumberTpl</span> - Шаблон для показа номеров страниц в кратком обзоре галереи.</a></h4>
		</div>
		<div id="collapse606" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /pagenumbertpl.html <br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pageNumberTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="607"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse607"><span class="text-bold">&pic_mask_bgcolor</span> - Цвет фона для нормальной фотографии</a></h4>
		</div>
		<div id="collapse607" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal<br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF<br>
				<span class="text-bold">Примечание:</span> Должен быть того же цвета, как цвет фона страницы.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_mask_bgcolor=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="608"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse608"><span class="text-bold">&pic_mask_img</span> - Путь к изображению маски для обычных изображений</a></h4>
		</div>
		<div id="collapse608" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/imagemask /demomask-frame2.png <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_mask_img=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="609"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse609"><span class="text-bold">&pic_mask_position</span> - Положение маски</a></h4>
		</div>
		<div id="collapse609" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | topleft | topright | left | center | right | bottom | bottomleft | bottomright | resize<br>
				<span class="text-bold">Значение по умолчанию:</span> resize<br>
				<span class="text-bold">Примечание:</span> Положение resize растягивает изображение маски на всю картинку.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_mask_position=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="610"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse610"><span class="text-bold">&pic_query_ids</span> - Идентификаторы отдельных изображений для извлечения</a></h4>
		</div>
		<div id="collapse610" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> Разделенный запятыми список идентификаторов изображений<br>
				<span class="text-bold">Значение по умолчанию:</span> <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_query_ids=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="611"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse611"><span class="text-bold">&pic_shadow_bgcolor</span> - Цвет тени фона для нормальной фотографии</a></h4>
		</div>
		<div id="collapse611" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal<br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF<br>
				<span class="text-bold">Примечание:</span> Должен быть того же цвета, как и цвет фона страницы.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_shadow_bgcolor=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="612"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse612"><span class="text-bold">&pic_shadow_path</span> - Путь к изображению тени</a></h4>
		</div>
		<div id="collapse612" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/dropshadow/<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_shadow_path=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="613"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse613"><span class="text-bold">&pic_use_dropshadow</span> - Применить DropShadow к нормальной фотографии.</a></h4>
		</div>
		<div id="collapse613" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_use_dropshadow=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="614"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse614"><span class="text-bold">&pic_use_imagemask</span> - Параметр включающий использование Изображение- маску</a></h4>
		</div>
		<div id="collapse614" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_use_imagemask=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="615"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse615"><span class="text-bold">&pic_use_watermark</span> - Включить водяные знаки для нормального изображения.</a></h4>
		</div>
		<div id="collapse615" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_use_watermark=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="616"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse616"><span class="text-bold">&pic_watermark_font</span> - Размер шрифта для текстовых водяных знаков.</a></h4>
		</div>
		<div id="collapse616" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 1 | 2 | 3 | 4 | 5<br>
				<span class="text-bold">Значение по умолчанию:</span> 3<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_font=`4`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="617"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse617"><span class="text-bold">&pic_watermark_halign</span> - Горизонтальное выравнивание водяных знаков</a></h4>
		</div>
		<div id="collapse617" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> left | center | right<br>
				<span class="text-bold">Значение по умолчанию:</span> right<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_halign=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="618"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse618"><span class="text-bold">&pic_watermark_img</span> - Путь к изображению водяного знака</a></h4>
		</div>
		<div id="collapse618" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/watermark /watermark.png <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_img=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="619"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse619"><span class="text-bold">&pic_watermark_txt</span> - Текст, который будет применяться к изображениям как водяной знак</a></h4>
		</div>
		<div id="collapse619" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> строка<br>
				<span class="text-bold">Значение по умолчанию:</span> Copyright &lt;YEAR&gt; &lt;SITENAME&gt;<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_txt=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="620"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse620"><span class="text-bold">&pic_watermark_txt_color</span> - Цвет текста водяного знака</a></h4>
		</div>
		<div id="collapse620" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal <br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_txt_color=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="621"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse621"><span class="text-bold">&pic_watermark_txt_hmargin</span> - Горизонтальный отступ в пикселях текста водяного знака</a></h4>
		</div>
		<div id="collapse621" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 10<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_txt_hmargin=`5`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="622"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse622"><span class="text-bold">&pic_watermark_txt_vmargin</span> - Вертикальный отступ в пикселях текста водяного знака</a></h4>
		</div>
		<div id="collapse622" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 10<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_txt_vmargin=`5`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="623"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse623"><span class="text-bold">&pic_watermark_type</span> - Определяет тип водяного знака</a></h4>
		</div>
		<div id="collapse623" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> text | image<br>
				<span class="text-bold">Значение по умолчанию:</span> text<br>
				<span class="text-bold">Примечание:</span> <br>image
				<br>text <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_type=`image`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="624"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse624"><span class="text-bold">&pic_watermark_valign</span> - Вертикальное выравнивание водяных знаков.</a></h4>
		</div>
		<div id="collapse624" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | center | bottom<br>
				<span class="text-bold">Значение по умолчанию:</span> bottom<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pic_watermark_valign=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="625"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse625"><span class="text-bold">&pics_per_page</span> - Количество эскизов изображений на одной странице</a></h4>
		</div>
		<div id="collapse625" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> 0 - не ограничено<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pics_per_page=`25`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="626"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse626"><span class="text-bold">&pics_per_row</span> - Количество эскизов, умещаемых в одном ряду.</a></h4>
		</div>
		<div id="collapse626" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 4<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pics_per_row=`5`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="627"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse627"><span class="text-bold">&picture_target</span> - Идентификатор документа, который будет использоваться для просмотра фотографий</a></h4>
		</div>
		<div id="collapse627" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ID документа<br>
				<span class="text-bold">Значение по умолчанию:</span> Текущий документ<br>
				<span class="text-bold">Примечание:</span> Используйте тот же вызов сниппета в этом документе, и добавьте в его вызове параметр: &is_target=`1`<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&picture_target=`10`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="628"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse628"><span class="text-bold">&pictureTpl</span> - Шаблон для предпросмотра фотографии.</a></h4>
		</div>
		<div id="collapse628" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> имя чанка | @FILE | @CODE<br>
				<span class="text-bold">Значение по умолчанию:</span> @FILE:/assets/snippets /maxigallery/templates /picturetpl.html <br>
				<span class="text-bold">Примечание:</span> <br>Имя чанка
				<br>@FILE:&lt;path to a file&gt;
				<br>@CODE:&lt;template string&gt;<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pictureTpl=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="629"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse629"><span class="text-bold">&pictureview_start_id</span> - Идентификатор фотографии, с которой начинается просмотр</a></h4>
		</div>
		<div id="collapse629" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> идентификатор фотографии<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> При &display=`pictureview`<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pictureview_start_id=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="630"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse630"><span class="text-bold">&pictureview_start_pos</span> - Номер изображения, с которого начинается просмотр</a></h4>
		</div>
		<div id="collapse630" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 1<br>
				<span class="text-bold">Примечание:</span> При &display=`pictureview`<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&pictureview_start_pos=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="631"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse631"><span class="text-bold">&quality_big</span> - Качество большого изображения</a></h4>
		</div>
		<div id="collapse631" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (%)<br>
				<span class="text-bold">Значение по умолчанию:</span> 100<br>
				<span class="text-bold">Примечание:</span> Процент от 0-100 для больших изображений<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&quality_big=`90`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="632"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse632"><span class="text-bold">&quality_pic</span> - Качество нормального изображения</a></h4>
		</div>
		<div id="collapse632" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (%)<br>
				<span class="text-bold">Значение по умолчанию:</span> 70<br>
				<span class="text-bold">Примечание:</span> Процент от 0-100 для нормального изображения<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&quality_pic=`90`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="633"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse633"><span class="text-bold">&quality_thumb</span> - Качество эскизов</a></h4>
		</div>
		<div id="collapse633" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (%)<br>
				<span class="text-bold">Значение по умолчанию:</span> 70<br>
				<span class="text-bold">Примечание:</span> Качество в процентах между 0-100 для эскизов.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&quality_thumb=`60`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="634"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse634"><span class="text-bold">&query_level_limit</span> - Определяет количество уровней в глубину</a></h4>
		</div>
		<div id="collapse634" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 1<br>
				<span class="text-bold">Примечание:</span> Определяет, сколько уровней в глубину, чтобы перейти от родителя кдокументам, указанным в gal_query_ids<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&query_level_limit=`3`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="635"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse635"><span class="text-bold">&random_filenames</span> - Случайные имена у загруженных фотографий</a></h4>
		</div>
		<div id="collapse635" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> Если включено, будут применяться случайные имена у загруженных фотографий.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&random_filenames=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="636"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse636"><span class="text-bold">&smoothgallery_carouselMaximizedOpacity</span> - Значение непрозрачности для carousel, когда она развернута.</a></h4>
		</div>
		<div id="collapse636" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число от 0 до 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0.7<br>
				<span class="text-bold">Примечание:</span> Где:
				0 = прозрачный (не виден) и 1,0 = полностью непрозрачный
				<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_carouselMaximizedOpacity=`0.9`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="637"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse637"><span class="text-bold">&smoothgallery_carouselMinimizedHeight</span> - Высота carousel в свернутом виде (в пикселях).</a></h4>
		</div>
		<div id="collapse637" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 20<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_carouselMinimizedHeight=`25`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="638"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse638"><span class="text-bold">&smoothgallery_carouselMinimizedOpacity</span> - Значение непрозрачности для carousel, когда она свернута.</a></h4>
		</div>
		<div id="collapse638" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число от 0 до 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0.4<br>
				<span class="text-bold">Примечание:</span> Где:
				0 = прозрачный (не виден) и 1,0 = полностью непрозрачный<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_carouselMinimizedOpacity=`0.5`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="639"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse639"><span class="text-bold">&smoothgallery_delay</span> - Задержка в миллисекундах для изменения слайд-шоу.</a></h4>
		</div>
		<div id="collapse639" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (ms) <br>
				<span class="text-bold">Значение по умолчанию:</span> 9000<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_delay=`8000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="640"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse640"><span class="text-bold">&smoothgallery_embedLinks</span> - Открыть картинку, нажав на слайде</a></h4>
		</div>
		<div id="collapse640" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> true | false<br>
				<span class="text-bold">Значение по умолчанию:</span> true<br>
				<span class="text-bold">Примечание:</span> Если Вы удаляете этот параметр, также удаляйте ссылку из galleryPictureTpl<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_embedLinks=`false`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="641"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse641"><span class="text-bold">&smoothgallery_fadeDuration</span> - Продолжительность в миллисекундах эффект затухания.</a></h4>
		</div>
		<div id="collapse641" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (ms)<br>
				<span class="text-bold">Значение по умолчанию:</span> 500<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_fadeDuration=`1000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="642"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse642"><span class="text-bold">&smoothgallery_height</span> - Высота в пикселях для smoothgallery</a></h4>
		</div>
		<div id="collapse642" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> max_pic_size <br>
				<span class="text-bold">Примечание:</span> Переполнения будут скрыты, так что это должно быть высотой крупнейших изображений (например, как и max_pic_size).<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_height=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="643"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse643"><span class="text-bold">&smoothgallery_id</span> - Иидентификатор smoothgallery</a></h4>
		</div>
		<div id="collapse643" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> Это позволяет иметь несколько smoothgalleries на одной странице.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_id=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="644"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse644"><span class="text-bold">&smoothgallery_preloader</span> - Предварительная загрузка изображений.</a></h4>
		</div>
		<div id="collapse644" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> true | false<br>
				<span class="text-bold">Значение по умолчанию:</span> true<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_preloader=`false`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="645"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse645"><span class="text-bold">&smoothgallery_showArrows</span> - Показать вперед - назад стрелки на слайд-шоу.</a></h4>
		</div>
		<div id="collapse645" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> true | false<br>
				<span class="text-bold">Значение по умолчанию:</span> true<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_showArrows=`false`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="646"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse646"><span class="text-bold">&smoothgallery_showCarousel</span> - Показать эскизы изображения в карусели, используя слайд-шоу.</a></h4>
		</div>
		<div id="collapse646" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> true | false<br>
				<span class="text-bold">Значение по умолчанию:</span> true<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_showCarousel=`false`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="647"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse647"><span class="text-bold">&smoothgallery_showInfopane</span> - Показать информационную панель (название изображения и описание).</a></h4>
		</div>
		<div id="collapse647" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> true | false<br>
				<span class="text-bold">Значение по умолчанию:</span> true<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_showInfopane=`false`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="648"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse648"><span class="text-bold">&smoothgallery_slideInfoZoneOpacity</span> - Прозрачность информационной панели.</a></h4>
		</div>
		<div id="collapse648" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 0.7<br>
				<span class="text-bold">Примечание:</span> 0 = прозрачная (не видна) и 1,0 = полностью непрозрачная<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_slideInfoZoneOpacity=`0.9`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="649"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse649"><span class="text-bold">&smoothgallery_textShowCarousel</span> - Текст, который показан на карусели</a></h4>
		</div>
		<div id="collapse649" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> текст<br>
				<span class="text-bold">Значение по умолчанию:</span> "pictures" текст из файла языка lang<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_textShowCarousel=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="650"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse650"><span class="text-bold">&smoothgallery_thumbHeight</span> - Высота thumnails, в пикселях, в SmoothGallery карусели</a></h4>
		</div>
		<div id="collapse650" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 75<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_thumbHeight=`90`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="651"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse651"><span class="text-bold">&smoothgallery_thumbSpacing</span> - Отступ в пикселях между эскизами в SmoothGallery карусели.</a></h4>
		</div>
		<div id="collapse651" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 10<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_thumbSpacing=`15`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="652"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse652"><span class="text-bold">&smoothgallery_thumbWidth</span> - Ширина эскизов в пикселях в SmoothGallery карусели.</a></h4>
		</div>
		<div id="collapse652" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 100<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_thumbWidth=`150`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="653"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse653"><span class="text-bold">&smoothgallery_timed</span> - Изменение изображения в режиме слайд-шоу по времени.</a></h4>
		</div>
		<div id="collapse653" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> true | false<br>
				<span class="text-bold">Значение по умолчанию:</span> false<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_timed=`true`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="654"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse654"><span class="text-bold">&smoothgallery_width</span> - Ширина в пикселях для smoothgallery.</a></h4>
		</div>
		<div id="collapse654" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> max_pic_size<br>
				<span class="text-bold">Примечание:</span> Переполнения будут скрыты, так что это должно быть шириной крупнейших изображений (например, как и max_pic_size).<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&smoothgallery_width=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="655"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse655"><span class="text-bold">&thumb_mask_bgcolor</span> - Цвет фона маски для эскизов изображений.</a></h4>
		</div>
		<div id="collapse655" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal <br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF<br>
				<span class="text-bold">Примечание:</span> Должен быть таким же, как и цвет фона страницы.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_mask_bgcolor=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="656"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse656"><span class="text-bold">&thumb_mask_img</span> - Путь к изображению imagemask, которое должно быть применено к эскизам изображений.</a></h4>
		</div>
		<div id="collapse656" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/imagemask /demomask-frame1.png <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_mask_img=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="657"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse657"><span class="text-bold">&thumb_mask_position</span> - Позиция Imagemask.</a></h4>
		</div>
		<div id="collapse657" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | topleft | topright | left | center | right | bottom | bottomleft | bottomright | resize<br>
				<span class="text-bold">Значение по умолчанию:</span> resize<br>
				<span class="text-bold">Примечание:</span> Опция resize - подгоняет размер imagemask к размеру изображения.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_mask_position=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="658"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse658"><span class="text-bold">&thumb_shadow_bgcolor</span> - Цвет тени фона для эскиза.</a></h4>
		</div>
		<div id="collapse658" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal<br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF<br>
				<span class="text-bold">Примечание:</span> Должен быть того же цвета, как цвет фона страницы.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_shadow_bgcolor=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="659"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse659"><span class="text-bold">&thumb_shadow_path</span> - Путь к DropShadow изображений</a></h4>
		</div>
		<div id="collapse659" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/dropshadow/ <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_shadow_path=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="660"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse660"><span class="text-bold">&thumb_use_dropshadow</span> - Применить DropShadow к эскизам.</a></h4>
		</div>
		<div id="collapse660" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_use_dropshadow=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="661"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse661"><span class="text-bold">&thumb_use_imagemask</span> - Применить imagemask к эскизам.</a></h4>
		</div>
		<div id="collapse661" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_use_imagemask=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="662"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse662"><span class="text-bold">&thumb_use_watermark</span> - Применить водяные знаки к эскизам.</a></h4>
		</div>
		<div id="collapse662" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_use_watermark=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="663"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse663"><span class="text-bold">&thumb_watermark_font</span> - Размер шрифта водяного знака у эскизов.</a></h4>
		</div>
		<div id="collapse663" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 1 | 2 | 3 | 4 | 5<br>
				<span class="text-bold">Значение по умолчанию:</span> 1<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_font=`2`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="664"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse664"><span class="text-bold">&thumb_watermark_halign</span> - Горизонтальный выравнивание текста водяного знака у эскизов.</a></h4>
		</div>
		<div id="collapse664" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> left | center | right<br>
				<span class="text-bold">Значение по умолчанию:</span> right <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_halign=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="665"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse665"><span class="text-bold">&thumb_watermark_img</span> - Путь к изображению водяного знака.</a></h4>
		</div>
		<div id="collapse665" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> путь<br>
				<span class="text-bold">Значение по умолчанию:</span> assets/snippets /maxigallery/watermark /watermark.png <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_img=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="666"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse666"><span class="text-bold">&thumb_watermark_txt</span> - Текст водяного знака у эскизов.</a></h4>
		</div>
		<div id="collapse666" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> текст<br>
				<span class="text-bold">Значение по умолчанию:</span> Copyright &lt;YEAR&gt;<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_txt=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="667"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse667"><span class="text-bold">&thumb_watermark_txt_color</span> - Цвет водяного знака у эскизов.</a></h4>
		</div>
		<div id="collapse667" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> RGB Hexadecimal <br>
				<span class="text-bold">Значение по умолчанию:</span> FFFFFF <br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_txt_color=`000000`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="668"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse668"><span class="text-bold">&thumb_watermark_txt_hmargin</span> - Горизонтальный отступ текста водяного знака.</a></h4>
		</div>
		<div id="collapse668" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 2<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_txt_hmargin=`5`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="669"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse669"><span class="text-bold">&thumb_watermark_txt_vmargin</span> - Вертикальный отступ текста водяного знака.</a></h4>
		</div>
		<div id="collapse669" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число (px)<br>
				<span class="text-bold">Значение по умолчанию:</span> 2<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_txt_vmargin=`5`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="670"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse670"><span class="text-bold">&thumb_watermark_type</span> - Определяет тип используемого водного знака - текст или изображение.</a></h4>
		</div>
		<div id="collapse670" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> text | image<br>
				<span class="text-bold">Значение по умолчанию:</span> text<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_type=``</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="671"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse671"><span class="text-bold">&thumb_watermark_valign</span> - Вертикальное выравнивание водяного знака.</a></h4>
		</div>
		<div id="collapse671" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> top | center | bottom<br>
				<span class="text-bold">Значение по умолчанию:</span> bottom<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&thumb_watermark_valign=`center`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="672"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse672"><span class="text-bold">&upload_field_count</span> - Число полей для загрузки файлов видимое менеджеру.</a></h4>
		</div>
		<div id="collapse672" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> число<br>
				<span class="text-bold">Значение по умолчанию:</span> 10<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&upload_field_count=`15`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="673"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse673"><span class="text-bold">&use_ftp_commands</span> - Если включено, MaxiGallery использует PHP FTP команды для создания файловой системы папки для галереи изображений.</a></h4>
		</div>
		<div id="collapse673" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> 0 | 1<br>
				<span class="text-bold">Значение по умолчанию:</span> 0<br>
				<span class="text-bold">Примечание:</span> Это необходимо в определенных серверных средах.<br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&use_ftp_commands=`1`</pre>
			</div>
		</div>
	</div>
	
	<div class="panel panel-default">
		<div class="panel-heading">
			<h4 class="panel-title"><a id="674"></a><a class="accordion-toggle collapsed" data-toggle="collapse" data-parent="#accordion" href="#collapse674"><span class="text-bold">&view_gallery</span> - Показать childgallery из документа (стр.), кроме документа родителя галереи.</a></h4>
		</div>
		<div id="collapse674" class="panel-collapse collapse">
			<div class="panel-body">
				<span class="text-bold">Формат:</span> ID документа<br>
				<span class="text-bold">Значение по умолчанию:</span> нет<br>
				<span class="text-bold">Примечание:</span> <br>
				<span class="text-bold">Пример:</span>
				<pre class="brush: html;">&view_gallery=``</pre>
			</div>
		</div>
	</div>
</div>