# Using a template
A template in Evolution is the main part of the site page that determines its design. The template does not require special syntax and is a simple HTML code (and possibly XHTML or other) with the call of the necessary chunks, parameters and snippets.

The number of templates most often depends on the appearance and functionality of the site. As a rule, templates are created for various sections and pages of the site. For example, it will be logical to create different templates for the product and for the news and attach various TV parameters to them. This will allow the content manager to fill the site faster and more correctly. It will also greatly facilitate the work of a programmer if you need to make some news feeds or products.

It is also worth mentioning that there is a special blank template that does not contain any design and cannot be edited.

#### Example template:
<html>
    <head>
        <title>[*pagetitle*]</title>
        <link href="[(site_url)]/style.css" rel="stylesheet">
    </head>
    <body>
        <div class="menu">
            [[Wayfinder? &startId=`5` &level=`1`]]
        </div>
        <div class="outer">
            <div class="main">
            <h1>[*longtitle*]</h1>
                [*content*]
            </div>
        </div>
        {{footer}}
        {{Google}}
    </body>
</html>
As we can see - this is a completely understandable HTML-markup of the page in which special constructions are used. Among them:

Chunky - {{footer}}, {{Google}}

Parameters - [*pagetitle*], [*content*]

Placeholder - [(site_url)]

Snippet Call - [[Wayfinder? &startId=`5` &level=`1`]]

## Create and edit a template
All templates are located in the following location:

Resources → Resource Management → Template The list of templates is as follows:

To create a new template, you need to click on the "New template" link, and to edit an existing one, just click on the link with its name. When you create a template, you can also choose which TV settings it owns and sort them as needed.

### Creating a template in Evolution CMS
#### Assign fields
Template name - used in the template selection list. You may also need snippets, plugins, or modules for some operations. You can use both English or Russian, as well as a hyphen, an underscore, and a space.

**Description** - displayed next to the name of the template in the general list. Used only to describe the purpose of the template and not required.

**Create Category** - allows you to select an existing category in which the template will be placed. A category allows you to separate a template from the rest in the general list. If no category is selected, the template will fall into the general category "Uncategorized".

**New category** - if there is no suitable category in the list of existing categories, you can create it by simply writing the name in this field.

Restrict access to editing a template - if you enable the checkbox, no one except administrators will be able to edit this template.

**Template code (html)** - the content of the template itself is placed here.

### Conservation
**Save** - creates a new template

**Undo** - will return us to the list of templates without saving the result.

**Make a copy** - appears only in edit mode.

**Delete** - appears only in edit mode.

Evolution allows you to define a few more actions after saving the template:

**Create a new one** - immediately after saving the template, a form will open to create a new one. In this way, you can quickly create a series of templates.

**Continue editing** - after saving, the template will open again for editing. In this mode, it is convenient to make small changes and check the final result.

**Close** - after saving, we will return to the general list of templates.

## Create a copy of a template
Sometimes it is necessary to create a copy of an existing template. It's very easy to do. To do this, go to the editing of the desired template and click on the "Make a copy" button.

This opens a copy of the template for editing. The copy differs in that Duplicate of is added to its name. You just have to correct the name to a more appropriate one and make other necessary changes.

A copy is created immediately after confirmation, so if you click Cancel, a copy will still remain in the list of templates.

## Delete a template
To delete, you need to go into the editing mode of the corresponding template and click the "Delete" button.

**Attention! Templates are deleted completely and there is no way to restore them.**

## Default template
When you create a document, a default template is automatically suggested. To configure the default template, you must do the following:

Go to the management system settings: Tools → Configuration → Site Find the "Default Template" parameter and change to the desired one. Save the settings.

## FAQ
Are there any restrictions on website design templates?

Absolutely none. Evolution allows you to implement any design.

## Where can I get ready-made templates?
Evolution makes it easy to use any laid out HTML-layout, which can be ordered from specialists or found on specialized sites.
