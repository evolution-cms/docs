Using a template

The template in MODx is the main immutable part of the site page that determines its design. The template does not require special syntax and is a simple HTML code (and possibly XHTML or other) with the call of the necessary chunks, parameters and snippets.

The number of templates most often depends on the number of different types of design. Because each document in MODx has a binding to a specific template, which determines its final appearance.

It is also worth mentioning that there is a special blank template that does not contain any design and cannot be edited.

####Пример template:

<title>[*pagetitle*]</title>
[[Wayfinder? &startId=`5` &level=`1`]]
{{Search}}

[*longtitle*]
[*content*]
{{Basement}}

{{Google}}

As we can see - this is a completely understandable HTML-markup of the page in which special constructions are used. Among them:
Chunky - {{Search}}, {{Footer}}, {{Google}}

Параметры - [pagetitle], [longtitle], [content], [(site_url)]

Сниппет - [[Wayfinder? &startId= &level=51]]

Create and edit a template

All templates are located in the following location:

Resources → Resource Management → Template The list of templates is as follows:

List of MODX EVO templates

To create, you need to click on the New template link, and to edit an existing template, just click on the link with its name. The following form appears:

Creating a template in MODX EVO

Assign fields

Template name - used in the template selection list. You may also need snippets for some operations. You can use both English and Russian, as well as a hyphen (-), an underscore (_), and a space.

Description - displayed next to the name of the template in the general list. Used only to describe the purpose of the template and not required.

Create Category - allows you to select an existing category in which the template will be placed. A category allows you to separate a template from the rest in the general list. If no category is selected, the template will fall into the general category Without category.

New category - if there is no suitable category in the list of existing categories, you can create it simply by writing the name in this field.

Restrict access to editing a template - if you enable a checkbox, no one except administrators will be able to edit this template.

Template code (html) - the content of the template itself is placed here.

Conservation

Let's pay attention to the possibilities when saving. To do this, there are the following control buttons:

Template control buttons in MODX EVO

With the main buttons, everything is clear:

Save - creates a new template

Undo - will return us to the list of templates without saving the result.

Make a copy - appears only in edit mode. See Create a copy of the template.

Удалить - появляется только в режиме редактирования. Смотрите пункт Удаление шаблона.

Но MODx позволяет определить еще действие после сохранения шаблона:

Создать новый - сразу после сохранения шаблона откроется форма для создания нового. Таким образом можно быстро создать серию шаблонов.

Продолжить редактирование - после сохранения шаблон снова откроется для редактирования. В этом режиме удобно вносить небольшие правки и проверять конечный результат.

Закрыть - после сохранения мы вернемся в общий список шаблонов.

Создание копии шаблона

Иногда бывает необходимо создать копию существующего шаблона. Сделать это очень просто. Для этого необходимо зайти в редактирование нужного шаблона и нажать на кнопку Сделать копию.

Template control buttons in MODX EVO

Just in case, the system will ask you for confirmation:

Copy of template in MODX EVO

This opens a copy of the template for editing. The copy differs in that Duplicate of is added to its name. You just have to correct the name to a more appropriate one and make other necessary changes.

A copy is created immediately after confirmation, so if you click Cancel, a copy will still remain in the list of templates.

Delete a template

To delete, you need to go into the editing mode of the corresponding template and click the Delete button.

Template control buttons in MODX EVO

After that, the system will ask you for confirmation:

Deleting a template in MODX EVO

Attention! Templates are deleted completely and there is no way to restore them.

Default template

When you create a document, a default template is automatically offered (if the Inherit Parent Template plugin is disabled). It is most convenient when the template that is needed most often is offered. To configure the default template, you must do the following:

Go to the management system settings: Tools → Configuration → Site Find the Default Template parameter and change to the desired Save settings. FAQ

Are there any restrictions on website design templates?

Absolutely none. MODx allows you to implement any design.

Where can I get ready-made templates?

MODx makes it easy to use any well-established HTML-layout, which can be ordered from specialists or found on specialized sites. There are not so many ready-made templates for MODx, but they are there.
