
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>MaxiGallery: Плейсхолдеры</h2>

<table class="table table-hover table-bordered table-condensed">
<tbody>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">manageButtonTpl - - Шаблон для кнопки управления фотографиями.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/managebuttontpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.urlaction+]</code></td>
<td>URL для обработчика формы</td>
</tr>
<tr>
<td><code>[+maxigallery.hiddenfields+]</code></td>
<td>Скрытые поля формы</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">manageOuterTpl - Внешний шаблон для управления галереей</h3>
Шаблон по умолчанию находится в файле: <em><code>assets/snippets/maxigallery/templates/manageoutertpl.html </code></em></td>
</tr>
<tr>
<td><code>[+maxigallery.messages+]</code></td>
<td>Сообщение об ошибке / уведомление в управлении изображениями (берется из языкового файла)</td>
</tr>
<tr>
<td><code>[+maxigallery.urlback+]</code></td>
<td>URL для ссылки "Вернуться в обычный просмотр"</td>
</tr>
<tr>
<td><code>[+maxigallery.urlaction+] </code></td>
<td>URL для обработчика формы</td>
</tr>
<tr>
<td><code>[+maxigallery.urldragsort+]</code></td>
<td>URL для ссылки "Сортировать изображения"</td>
</tr>
<tr>
<td><code>[+maxigallery.managepictures+]</code></td>
<td>Изображения (контент из managePictureTpl)</td>
</tr>
<tr>
<td><code>[+maxigallery.uploadpictures+]</code></td>
<td>Поле для загрузки изображений (контент из manageUploadTpl)</td>
</tr>
<tr>
<td><code>[+maxigallery.hiddenfields+]</code></td>
<td>Скрытое поле для формы Управление изображениями, которая должно быть в ней</td>
</tr>
<tr>
<td><code>[+maxigallery.pics_allowed_count+]</code></td>
<td>Количество изображений, разрешенных к загрузке</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.fieldname+]</code></td>
<td>Поле документа MODx, в котором находится галерея. "fieldname" может быть pagetitle, longtitle, pub_date и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">managePictureTpl - Шаблон для одного элемента изображения в управлении галереей</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/managepicturetpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.picture.fieldname+]</code></td>
<td>Содержание для области изображения MaxiGallery. "fieldname" может иметь значения id, gal_id, filename, title, date, descr, pos или own_id.</td>
</tr>
<tr>
<td><code>[+maxigallery.path_to_gal+]</code></td>
<td>Путь к текущему изображению галереи, например: <em><code>assets/galleries/120/</code></em></td>
</tr>
<tr>
<td><code>[+maxigallery.fieldnames.field+]</code></td>
<td>Названия полей ввода формы. "field" может быть delete, position, title, pictureid, modified и description. Посмотрите в шаблоне по умолчанию, как они используются.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">manageUploadTpl - Шаблон для загрузки файла в управлении галереей</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/manageuploadtpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.counter+]</code></td>
<td>Номер для текущей строки</td>
</tr>
<tr>
<td><code>[+maxigallery.fieldnames.file+]</code></td>
<td>Имя для поля формы</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">galleryOuterTpl - Внешний шаблон для краткого обзора галереи</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/galleryoutertpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.managebutton+]</code></td>
<td>Кнопка для управления изображениями</td>
</tr>
<tr>
<td><code>[+maxigallery.childgalleries+]</code></td>
<td>Дочерние галереи (содержимое childgalleryTpl)</td>
</tr>
<tr>
<td><code>[+maxigallery.childgallerycount+]</code></td>
<td>Количество дочерних галерей</td>
</tr>
<tr>
<td><code>[+maxigallery.currentpage+]</code></td>
<td>Номер текущей страницы</td>
</tr>
<tr>
<td><code>[+maxigallery.pagecount+]</code></td>
<td>Общее число страниц</td>
</tr>
<tr>
<td><code>[+maxigallery.previous_page_url+]</code></td>
<td>Ссылка на предыдущую страницу</td>
</tr>
<tr>
<td><code>[+maxigallery.next_page_url+]</code></td>
<td>Ссылка на следующую страницу</td>
</tr>
<tr>
<td><code>[+maxigallery.pagenumbers+]</code></td>
<td>Номера страниц (содержимое pageNumberTpl)</td>
</tr>
<tr>
<td><code>[+maxigallery.pictures+]</code></td>
<td>Галерея изображений (содержимое galleryPictureTpl)</td>
</tr>
<tr>
<td><code>[+maxigallery.picscount+]</code></td>
<td>Количество фотографий в галерее</td>
</tr>
<tr>
<td><code>[+maxigallery.embedtype+]</code></td>
<td>Выбранный embedtype</td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.fieldname+]</code></td>
<td>Поле документа MODx, в котором находится галерея. "fieldname" может быть pagetitle, longtitle, pub_date и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">galleryPictureTpl - Шаблон для каждого изображения (эскиза) при обзоре галереи.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/gallerypicturetpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.embedtype+]</code></td>
<td>Значение параметра embedtype конфигурации MaxiGallery</td>
</tr>
<tr>
<td><code>[+maxigallery.picture.fieldname+]</code></td>
<td>Содержание для области изображения MaxiGallery. "fieldname" может иметь значения id, gal_id, filename, title, date, descr, pos или own_id.</td>
</tr>
<tr>
<td><code>[+maxigallery.path_to_gal+]</code></td>
<td>Путь к текущему изображению галереи, например: <em><code>assets/galleries/120/</code></em></td>
</tr>
<tr>
<td><code>[+maxigallery.picture_link_url+]</code></td>
<td>URL для ссылки на изображение</td>
</tr>
<tr>
<td><code>[+maxigallery.big_pic_exists+]</code></td>
<td>Индикатор, отображающий существование большого изображения. 1 - да, 0 - нет</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_big+]</code></td>
<td>Высота большого изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_big+]</code></td>
<td>Ширина большого&nbsp; изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_normal+]</code></td>
<td>Высота нормального изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_normal+]</code></td>
<td>Ширина нормального изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_thumb+]</code></td>
<td>Высота эскиза</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_thumb+]</code></td>
<td>Ширина эскиза</td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.fieldname+]</code></td>
<td>Поле документа MODx, в котором находится галерея. "fieldname" может быть pagetitle, longtitle, pub_date и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td><code>[+maxigallery.rownumber+]</code></td>
<td>Номер строки для изображения (только для версии 0.6)</td>
</tr>
<tr>
<td><code>[+maxigallery.picrownumber+]</code></td>
<td>Количество изображений в строке (только для версии 0.6)</td>
</tr>
<tr>
<td><code>[+maxigallery.picpagenumber+]</code></td>
<td>Количество изображений на странице (только для версии 0.6)</td>
</tr>
<tr>
<td><code>[+maxigallery.picnumber+]</code></td>
<td>Количество изображений в галерее (только для версии 0.6)</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">childgalleryTpl - Шаблон для отображения дочерней галереи.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/childgallerytpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.picscount+]</code></td>
<td>Количество фотографий в галерее</td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.fieldname+]</code></td>
<td>Поле документа MODx, в котором находится галерея. "fieldname" может быть pagetitle, longtitle, pub_date и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.tv.tvname+]</code></td>
<td>Переменные шаблона из дочернего документа галереи. "tvname" - имя TV-параметра.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.picture.fieldname+]</code></td>
<td>Содержание для области изображения MaxiGallery (первое изображение в дочерней галереи). "fieldname" может иметь значения id, gal_id, filename, title, date, descr, pos или own_id.</td>
</tr>
<tr>
<td><code>[+maxigallery.childurl+]</code></td>
<td>URL к документу дочерней галереи</td>
</tr>
<tr>
<td><code>[+maxigallery.path_to_gal+]</code></td>
<td>Путь к текущему изображению галереи, например: <em><code>assets/galleries/120/</code></em></td>
</tr>
<tr>
<td><code>[+maxigallery.big_pic_exists+]</code></td>
<td>Индикатор, отображающий существование большого изображения. 1 - да, 0 - нет</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_big+]</code></td>
<td>Высота большого изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_big+]</code></td>
<td>Ширина большого изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_normal+]</code></td>
<td>Высота нормального изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_normal+]</code></td>
<td>Ширина нормального изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_thumb+]</code></td>
<td>Высота эскиза</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_thumb+]</code></td>
<td>Ширина эскиза</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">pictureTpl - Шаблон для предпросмотра изображения.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/childgallerytpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.managebutton+]</code></td>
<td>Кнопка для управления изображениями</td>
</tr>
<tr>
<td><code>[+maxigallery.big_img_linkstyle+]</code></td>
<td>Значение параметра big_img_linkstyle</td>
</tr>
<tr>
<td><code>[+maxigallery.keep_bigimg+]</code></td>
<td>Значение параметра keep_bigimg</td>
</tr>
<tr>
<td><code>[+maxigallery.path_to_gal+]</code></td>
<td>Путь к текущему изображению галереи, например: <em><code>assets/galleries/120/</code></em></td>
</tr>
<tr>
<td><code>[+maxigallery.picture.fieldname+]</code></td>
<td>Содержание для области изображения MaxiGallery. "fieldname" может иметь значения id, gal_id, filename, title, date, descr, pos или own_id.</td>
</tr>
<tr>
<td><code>[+maxigallery.counter+]</code></td>
<td>Текущий номер изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.total_pics_count+]</code></td>
<td>Общее количество изображений в галерее</td>
</tr>
<tr>
<td><code>[+maxigallery.previous_pic_url+]</code></td>
<td>Ссылка на предыдущее изображение</td>
</tr>
<tr>
<td><code>[+maxigallery.next_pic_url+]</code></td>
<td>Ссылка на следующее изображение</td>
</tr>
<tr>
<td><code>[+maxigallery.index_url+]</code></td>
<td>Ссылка на краткий обзор галереи</td>
</tr>
<tr>
<td><code>[+maxigallery.big_pic_exists+]</code></td>
<td>Индикатор, отображающий существование большого изображения. 1 - да, 0 - нет</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_big+]</code></td>
<td>Высота большого изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_big+]</code></td>
<td>Ширина большого изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_normal+]</code></td>
<td>Высота нормального изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_normal+]</code></td>
<td>Ширина нормального изображения</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_height_thumb+]</code></td>
<td>Высота эскиза</td>
</tr>
<tr>
<td><code>[+maxigallery.picture_width_thumb+]</code></td>
<td>Ширина эскиза</td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.fieldname+]</code></td>
<td>Поле документа MODx, в котором находится галерея. "fieldname" может быть pagetitle, longtitle, pub_date и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">pageNumberTpl - Шаблон для показа номеров страниц в кратком обзоре галереи.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/pagenumbertpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.pageurl+]</code></td>
<td>URL к странице</td>
</tr>
<tr>
<td><code>[+maxigallery.pagenumber+]</code></td>
<td>Номер страницы</td>
</tr>
<tr>
<td><code>[+maxigallery.pagecount+]</code></td>
<td>Общее число страниц</td>
</tr>
<tr>
<td><code>[+maxigallery.currentpage+]</code></td>
<td>Номер текущей страницы</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">draggableTpl - Шаблон для ручной сортировки изображений галереи.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/draggabletpl.html</code></td>
</tr>
<tr>
<td><code>[+maxigallery.path+]</code></td>
<td>Путь к папке MaxiGallery</td>
</tr>
<tr>
<td><code>[+maxigallery.path_to_gal+]</code></td>
<td>Путь к текущему изображению галереи, например: <em><code>assets/galleries/120/</code></em></td>
</tr>
<tr>
<td><code>[+maxigallery.pageinfo.fieldname+]</code></td>
<td>Поле документа MODx, в котором находится галерея. "fieldname" может быть pagetitle, longtitle, pub_date и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.strings.keyname+]</code></td>
<td>Текст из языкового файла MaxiGallery. "keyname" может быть click_to_zoom, previous, next и т.д.</td>
</tr>
<tr>
<td><code>[+maxigallery.config.parameter+]</code></td>
<td>Значение параметра сниппета. "parameter" - любой из параметров сниппета.</td>
</tr>
<tr>
<td colspan="2">
<h3 class="sub-header text-bold">clearerTpl - Шаблон используемый при использовании параметра pics_per_row.</h3>
Шаблон по умолчанию находится в файле: <code>assets/snippets/maxigallery/templates/clearertpl.html</code></td>
</tr>
<tr>
<td colspan="2">Нет используемых плэйсхолдеров</td>
</tr>
</tbody>
</table>