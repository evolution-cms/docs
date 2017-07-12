Docmanager

Для операций с документами будем использовать специальную библиотеку docmanager. Устанавливаем ее в папкуassets/libs/docmanager.

Создаем форму

Форма создается с помощью стандартного сниппета eForm. В него встроены все необходимые проверки полей, а также возможность отправить нам письмо о добавлении нового материала.

Для примера сделаем такую форму в чанке Anketa:

<p class="error">[+validationmessage+]</p>
 <form action="[~[*id*]~]" method="post" enctype="multipart/form-data">
     <input type="hidden" name="formid" value="newArticle" />
     <p><label>Автор *</label><br>
     <input class="field" type="text" name="avtor" maxlength="60" eform="Имя автора:string:1:Имя автора нужно обязательно!" /></p>      <p><label>Email *</label><br>
     <input class="field" type="text" name="email" size="40" maxlength="40" eform="Адрес почты:email:0" /></p>      <p><label>Адрес сайта</label><br>
     <input class="field" type="text" name="link" size="40" maxlength="40" eform="Адрес сайта:string:0" /><br>
     <em style="color: #999">Правильно: "http://www.modx-cms.ru". Неправильно: "www.modx-cms.ru"</em></p>      Название *<br>
     <input name="pagetitle" type="text" eform="Краткое название:string:0:Название обязательно!" /><br>      Аннотация *<br>
     <textarea name="introtext" cols="40" rows="5" eform="Краткое описание:string:0:Краткое описание обязательно!"></textarea><br><br>      Текст статьи<br>
     <textarea name="content" cols="40" rows="10" eform="Расширенное описание:string:0"></textarea><br><br>
     <p><input type="submit" name="frmGo" value="Послать" /></p>
 </form>
Вызов формы на сайте

Для показа формы можно использовать следующий вызов:

[!eForm? &formid=`newArticle` &subject=`Посетители прислали новый файл` &tpl=`Anketa` !]
Важно! Параметр formid должен совпадать с одноименным скрытым полем формы.

Обработчик полученных данных

После того как мы получили все необходимые от пользователя данные нам необходимо их поместить в документ. Для это делаем новый сниппет с именем NewArticleEvent и в нем создаем свою функцию CreateNewArticle:

function CreateNewArticle(&$fields){
     // Массив $fields будет содержать данные всех полей формы
     // Создания документа с описанием.
     require_once('assets/libs/docmanager/document.class.inc.php');
     $doc = new Document(); // создаем документ
     $doc->Set('parent',60); // определяем в какую папку положить
     $doc->Set('template','Статья'); // задаем шаблон
     $doc->Set('pagetitle',$fields['pagetitle']); // краткое название
     $doc->Set('introtext',$fields['introtext']); // аннотацию
     $doc->Set('content',$fields['content']); // основное содержимое
     // Далее пойдут TV-параметры
     $doc->Set('tvAvtor',$fields['avtor']); // автор
     $doc->Set('tvEmail',$fields['email']); // e-mail
     $doc->Set('tvLink',$fields['link']); // ссылка
     $doc->Save(); // сохраняем
     return true; // Говорим eForm, что все в порядке. }
Вот такой простой код нам позволит полученные данные сохранить в документ. Названия сниппета и функции с обработчиком можно изменить при желании.

Важно! Для указания TV-параметров перед названием необходимо добавлять приставку tv, то есть  это не часть названия параметра.

Подключаем обработчик к нашей форме

eForm имеет несколько событий, которые мы можем перехватывать, но в данном случае нам нужно только eFormOnBeforeMailSent. Оно вызывается прямо перед отправкой формы и после того как все данные проверены на обязательность заполнения и формат. Изменяем немного вызов нашей формы и получаем следующий окончательный вид:

[!NewArticleEvent!]
 [!eForm? &formid=`newArticle` &subject=`Посетители прислали новый файл` &tpl=`Anketa` &eFormOnBeforeMailSent=`CreateNewArticle`!]
Важно! Чтобы событие eForm имело доступ к нашему обработчику необходимо сделать вызов сниппета с обработчиком сразу перед вызовом eForm. Название вызываемой функции задается в параметре вызова обработчика &eFormOnBeforeMailSent.

PS: Таким образом можно создавать формы любой сложности и даже организовать закачку файлов.

Визуальный редактор

Чтобы посетителям было удобнее создавать статьи, можно использовать визуальный редактор tinyMCE.  Для этого в страницу с формой нужно включить следующий код:

<script language="javascript" type="text/javascript" src="assets/plugins/tinymce212/jscripts/tiny_mce/tiny_mce.js"></script>
 <script language="javascript" type="text/javascript">
 tinyMCE.init({
 // Общие настройки
 language : 'ru',
 mode : "textareas",
 theme : "advanced",
 plugins : "emotions,preview,searchreplace,contextmenu,paste,fullscreen,visualchars",
 // Настройки темы
 theme_advanced_buttons1 : "code,|,undo,redo,|,bold,italic,underline,strikethrough,|,removeformat,cut,copy,paste,|,bullist,numlist,|,link,unlink,|,image,|,sub,sup,|,charmap,formatselect",
 theme_advanced_buttons2 : "",
 theme_advanced_toolbar_location : "top",
 theme_advanced_toolbar_align : "left",
 theme_advanced_statusbar_location : "bottom",
 theme_advanced_resizing : true,
 // Подключение нужного CSS стиля
 content_css : "assest/templates/me_template/style.css"
 });
 </script>
Редактор tinyMCE хорошо настраивается. поэтому вы можете добавить инструменты, которые необходимы в вашем случае.  А для того, чтобы eForm пропустил теги HTML необходимо добавить следующие параметры:

&allowhtml=`1` &sendAsHtml=`1`