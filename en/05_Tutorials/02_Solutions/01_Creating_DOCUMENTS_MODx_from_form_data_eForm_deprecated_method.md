## Creating MODx Documents from eForm Form Data Deprecated Method

**This is an outdated method. We recommend that you use the FormLister snippet to create documents, or replace the function calls in the snippet with methods of the MODx Api library.**

However, as an example of working with eForm snippets and events, this solution fits very well.

For operations with documents we will use a special library docmanager. Install it in the .assets/libs/docmanager

### Create a form
The form is created using the standard eForm snippet. It has built-in all the necessary field checks, as well as the ability to send us a letter about adding new material.

For example, let's make this form in an Anketa chunk:
```html
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
```
### To call a form on a site
You can use the following call to display the form:
```php
[!eForm? &formid=`newArticle` &subject=`Посетители прислали новый файл` &tpl=`Anketa` !]
```
Importantly! The formid parameter must match the formid field of the same name.

### Processor of received data
Once we have received all the necessary data from the user, we need to put them in the document. To do this, make a new snippet named NewArticleEvent and in it create your function CreateNewArticle:
```php
function CreateNewArticle(&$fields){
     // the $fields array will contain the data of all the form fields
     // Create a document with a description.
     require_once('assets/libs/docmanager/document.class.inc.php');
     $doc = new Document(); // Create a Document
     $doc->Set('parent',60); // determine in which folder to put
     $doc->Set('template','Article'); // choose an existing template
     $doc->Set('pagetitle',$fields['pagetitle']); // set the pagetitle
     $doc->Set('introtext',$fields['introtext']); // set the introtext
     $doc->Set('content',$fields['content']); // set the contents
     // Set any Tempalte Variables
     $doc->Set('tvAuthor',$fields['author']); // Set the Author TV
     $doc->Set('tvEmail',$fields['email']); // Set the Email TV
     $doc->Set('tvLink',$fields['link']); // Set an URL Link TV
     $doc->Save(); // Save the Document
     return true; // Tell eForm it's ok. 
}
```
Such a simple code will allow us to save the received data to a document. You can change the snippet names and functions with the handler if you want.

Importantly! To specify TV parameters, you must add the tv prefix before the name, that is, this is not part of the parameter name.

### Connecting the handler to our form
eForm has several events that we can catch, but in this case we only need eFormOnBeforeMailSent. It is called right before the form is submitted and after all data has been checked for mandatory and format. Change the call of our form a bit and get the following final view:
```php
[!NewArticleEvent!]
[!eForm? &formid=`newArticle` &subject=`Visitors sent a new file` &tpl=`questionnaire` &eFormOnBeforeMailSent=`CreateNewArticle`!]
```
Importantly! For the eForm event to access our handler, we need to make a snippet call to the handler immediately before calling eForm. The name of the function to be called is specified in the call parameter of the &eFormOnBeforeMailSent handler.

PS: Thus, you can create forms of any complexity and even organize file uploads.

### Visual Editor
To make it easier for visitors to create articles, you can use the visual editor tinyMCE. To do this, you must include the following code in the page with the form:
```html
<script language="javascript" type="text/javascript" src="assets/plugins/tinymce212/jscripts/tiny_mce/tiny_mce.js"></script>
 <script language="javascript" type="text/javascript">
 tinyMCE.init({
 // General Settings
 language : 'en',
 mode : "textareas",
 theme : "modern",
 plugins : "emoticons,preview,searchreplace,contextmenu,paste,fullscreen,visualchars",
 // Theme Settings
 theme_advanced_buttons1 : "code,|,undo,redo,|,bold,italic,underline,strikethrough,|,removeformat,cut,copy,paste,|,bullist,numlist,|,link,unlink,|,image,|,sub,sup,|,charmap,formatselect",
 theme_advanced_buttons2 : "",
 theme_advanced_toolbar_location : "top",
 theme_advanced_toolbar_align : "left",
 theme_advanced_statusbar_location : "bottom",
 theme_advanced_resizing : true,
 // Connect the desired CSS style
 content_css : "assest/templates/me_template/style.css"
 });
</script>
```
The tinyMCE editor is highly customizable. therefore, you can add the tools that are needed in your case. And in order for eForm to miss HTML tags, you need to add the following parameters:
```html
&allowhtml=`1` &sendAsHtml=`1`
```
