## Docmanager

For operations with documents we will use a special library docmanager. Install it in the folderassets/libs/docmanager.

### Create a form

The form is created using the standard eForm snippet. It has built-in all the necessary field checks, as well as the ability to send us a letter about adding new material.

For example, let's make this form in an Anketa chunk:

[+validationmessage+]

Author*
Email *
Site address

Correct: "http://www.modx-cms.ru. Incorrect: "www.modx-cms.ru"

Title *

Abstract *
<textarea name="introtext" cols="40" rows="5" eform="Short description:string:0:Brief description required!" ></textarea>

Article
text <textarea name="content" cols="40" rows="10" eform="Extended description:string:0"></textarea>

Call a form on a site
You can use the following call to display the form:

[!eForm? &formid= &subject= &tpl= !] Importantly! The formid parameter must match the formid field of the same name.newArticleПосетители прислали новый файлAnketa

### Processor of received data

Once we have received all the necessary data from the user, we need to put them in the document. To do this, make a new snippet named NewArticleEvent and in it create your function CreateNewArticle:

```php
function CreateNewArticle(&$fields){ 
 // the $fields array will contain the data of all the form fields Create a document with a description. 
 require_once('assets/libs/docmanager/document.class.inc.php'); 
 $doc = new Document(); 
 //create a document 
 $doc->Set('parent',60); 
 // determine in which folder to put 
 $doc->Set('template', 'Article'); 
 // set a template 
 $doc->Set('pagetitle', $fields['pagetitle']); 
 // short name 
 $doc->Set('introtext', $fields['introtext']); 
 // Annotation 
 $doc->Set('content', $fields['content']); 
 // main content Next, the TV settings will go 
 $doc->Set('tvAvtor', $fields['avtor']); 
 //author 
 $doc->Set('tvEmail', $fields['email']); 
 // e-mail 
 $doc->Set('tvLink',$fields['link']); 
 // reference 
 $doc->Save(); 
 // Save return true; 
 // We tell eForm that it's okay. 
 }```
 
Such a simple code will allow us to save the received data to a document. You can change the snippet names and functions with the handler if you want.

Importantly! To specify TV parameters, you must add the tv prefix before the name, that is, this is not part of the parameter name.

### Connecting the handler to our form

eForm has several events that we can catch, but in this case we only need eFormOnBeforeMailSent. It is called right before the form is submitted and after all data has been checked for mandatory and format. Change the call of our form a bit and get the following final view:

[! NewArticleEvent!] 
[!eForm? &formid= &subject= &tpl= &eFormOnBeforeMailSent=!] 

Importantly! For the eForm event to access our handler, we need to make a snippet call to the handler immediately before calling eForm. The name of the function to be called is specified in the call parameter of the &eFormOnBeforeMailSent handler.newArticleПосетители прислали новый файлAnketaCreateNewArticle

PS: Thus, you can create forms of any complexity and even organize file uploads.

### Visual Editor

To make it easier for visitors to create articles, you can use the visual editor tinyMCE. To do this, you must include the following code in the page with the form:

```html
<script language="javascript" type="text/javascript" src="assets/plugins/tinymce212/jscripts/tiny_mce/tiny_mce.js"></script>
<script language="javascript" type="text/javascript"> 
tinyMCE.init({ 
 General Settings language : 'ru',
 mode : "textareas", 
 theme : "advanced", 
 plugins : "emotions,preview,searchreplace,contextmenu,paste,fullscreen,visualchars", 
 //Theme settings 
 theme_advanced_buttons1 : "code,|,undo,redo,|,bold,italic,underline,strikethrough,|,removeformat,cut,copy,paste,|,bullist,numlist,|,link,unlink,|,image,|,sub,sup,|,charmap,formatselect", theme_advanced_buttons2 : "", 
 theme_advanced_toolbar_location : "top", 
 theme_advanced_toolbar_align : "left", 
 theme_advanced_statusbar_location : "bottom", 
 theme_advanced_resizing : true, 
 // Connect the desired CSS style 
 content_css : "assest/templates/me_template/style.css" }); 
</script>```

The tinyMCE editor is highly customizable. therefore, you can add the tools that are needed in your case. And in order for eForm to miss HTML tags, you need to add the following parameters:

&allowhtml= &sendAsHtml=1
