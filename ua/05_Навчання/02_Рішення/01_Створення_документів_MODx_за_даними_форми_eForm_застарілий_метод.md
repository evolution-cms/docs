**Це застарілий метод. Рекомендуємо для створення документів використовувати сніппет FormLister, або замінити в сніпеті виклики функцій на методи бібліотеки MODx Api. **

Однак, як приклад роботи з сниппетами і подіями eForm, це рішення дуже добре підходить.

Для операцій з документами будемо використовувати спеціальну бібліотеку docmanager. Встановлюємо її в папку `assets/libs/docmanager`.

### Створюємо форму

Форма створюється за допомогою стандартного сніппета eForm. У нього вбудовані всі необхідні перевірки полів, а також можливість відправити нам лист про додавання нового матеріалу.

Для прикладу зробимо таку форму в чанку Anketa:
```
<p class="error">[+validationmessage+]</p>
 <form action="[~[*id*]~]" method="post" enctype="multipart/form-data">
     <input type="hidden" name="formid" value="newArticle" />
     <p><label>Автор *</label><br>
     <input class="field" type="text" name="avtor" maxlength="60" eform="Ім'я автора:string:1:Ім'я автора потрібно обов'язково!" /></p>      <p><label>Email *</label><br>
     <input class="field" type="text" name="email" size="40" maxlength="40" eform="Адреса пошти:email:0" /></p>      <p><label>Адрес сайта</label><br>
     <input class="field" type="text" name="link" size="40" maxlength="40" eform="Адрес сайта:string:0" /><br>
     <em style="color: #999">Правильно: "http://www.modx-cms.ru". Неправильно: "www.modx-cms.ru"</em></p>      Назва *<br>
     <input name="pagetitle" type="text" eform="Коротка назва:string:0:Назва обов'язково!" /><br>      Аннотація *<br>
     <textarea name="introtext" cols="40" rows="5" eform="Короткий опис:string:0:Короткий опис обов'язково!"></textarea><br><br>      Текст статті<br>
     <textarea name="content" cols="40" rows="10" eform="Розширений опис:string:0"></textarea><br><br>
     <p><input type="submit" name="frmGo" value="Відіслати" /></p>
 </form>
 ```

### Виклик форми на сайті

Для показу форми можна використовувати наступний виклик:
```
[!eForm? &formid=`newArticle` &subject=`Відвідувачі надіслали новий файл` &tpl=`Anketa` !]
```
Важливо! Параметр formid повинен збігатися з однойменною прихованим полем форми.

### Оброблювач отриманих даних

Після того як ми отримали всі необхідні від користувача дані нам необхідно їх помістити в документ. Для цього робимо новий сніппет з ім'ям NewArticleEvent і в ньому створюємо свою функцію CreateNewArticle:
```
function CreateNewArticle(&$fields){
     // Масив $fields буде містити дані всіх полів форми
     // Створення документа з описом.
     require_once('assets/libs/docmanager/document.class.inc.php');
     $doc = new Document(); // створюємо документ
     $doc->Set('parent',60); // визначаємо в яку папку покласти
     $doc->Set('template','Статья'); // задаєм шаблон
     $doc->Set('pagetitle',$fields['pagetitle']); // коротка назва
     $doc->Set('introtext',$fields['introtext']); // аннотація
     $doc->Set('content',$fields['content']); // основний вміст
     // Далі підуть TV-параметри
     $doc->Set('tvAvtor',$fields['avtor']); // автор
     $doc->Set('tvEmail',$fields['email']); // e-mail
     $doc->Set('tvLink',$fields['link']); // посилання
     $doc->Save(); // зберігаємо
     return true; // Говоримо eForm, що все в гаразд. }
```

Ось такий простий код нам дозволить отримані дані зберегти в документ. Назви сніппета і функції з обробником можна змінити при бажанні.

Важливо! Для вказівки TV-параметрів перед назвою необхідно додавати приставку tv, тобто це не частина назви параметра.

### Підключаємо обробник до нашої форми

eForm має кілька подій, які ми можемо перехоплювати, але в даному випадку нам потрібно тільки eFormOnBeforeMailSent. Воно викликається прямо перед відправкою форми і після того як всі дані перевірені на обов'язковість заповнення і формат. Змінюємо трохи виклик нашої форми і отримуємо наступний остаточний вигляд:
```
[!NewArticleEvent!]
[!eForm? &formid=`newArticle` &subject=`Відвідувачі надіслали новий файл` &tpl=`Anketa` &eFormOnBeforeMailSent=`CreateNewArticle`!]
```
Важливо! Щоб подія eForm мала доступ до нашого обробника необхідно зробити виклик сніппета з обробником відразу перед викликом eForm. Назва функції, що викликається, задається в параметрі виклику обробника &eFormOnBeforeMailSent.

PS: Таким чином можна створювати форми будь-якої складності і навіть організувати закачування файлів.

### Візуальний редактор

Щоб відвідувачам було зручніше створювати статті, можна використовувати візуальний редактор tinyMCE. Для цього в сторінку з формою потрібно включити наступний код:
```
<script language="javascript" type="text/javascript" src="assets/plugins/tinymce212/jscripts/tiny_mce/tiny_mce.js"></script>
 <script language="javascript" type="text/javascript">
 tinyMCE.init({
 // Загальні налаштування
 language : 'ru',
 mode : "textareas",
 theme : "advanced",
 plugins : "emotions,preview,searchreplace,contextmenu,paste,fullscreen,visualchars",
 // Налаштування теми
 theme_advanced_buttons1 : "code,|,undo,redo,|,bold,italic,underline,strikethrough,|,removeformat,cut,copy,paste,|,bullist,numlist,|,link,unlink,|,image,|,sub,sup,|,charmap,formatselect",
 theme_advanced_buttons2 : "",
 theme_advanced_toolbar_location : "top",
 theme_advanced_toolbar_align : "left",
 theme_advanced_statusbar_location : "bottom",
 theme_advanced_resizing : true,
 // Підключення потрібного CSS стиля
 content_css : "assest/templates/me_template/style.css"
 });
 </script>
```
Редактор tinyMCE добре налаштовується, тому ви можете додати інструменти, які необхідні у вашому випадку. А для того, щоб eForm пропустив теги HTML необхідно додати наступні параметри:
```
&allowhtml=`1` &sendAsHtml=`1`
```
