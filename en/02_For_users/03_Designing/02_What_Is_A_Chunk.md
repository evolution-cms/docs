Use of Chunk

A chunk in MODx is a small piece of HTML code or other information that can be reused in a template, other chunk, or snippet.

As a rule, templates use several chunks that contain a matching appearance. For example, you can take out the header, basement, main menu, crumbs. Thanks to this, changes can be made in one chunk, and not several templates. This is both simpler and there is no risk of leaving some template without an important change.

The second most common use of chunk is snippet templates. Thanks to this, there is a separation of the control code and design. Depending on the complexity of the snippet, the number of templates may vary. For example, to create a feedback form, you may need 3 main templates - a form, a text about the successful acceptance of the form, the text of a letter to the administrator with the information received. In order for the chunk to be not just a piece of HTML code, but to work as a template, it is necessary to mark the appropriate places in it where the snippet will record its information. The role of such places is performed by placeholders.

####Пример chunk contents with placeholders:

[+wf.linktext+]
This is a template that is used for menu items in MODx-cms.ru. And respectively , [+wf.classes+] and [+wf.linktext+] are placeholders that will be replaced by the Wayfinder snippet on the CSS class used and the name of the menu item.
In addition to these two options, the chunk can be used to store some special information. For example, you can store a set of parameters for a snippet (for example, a list of files), which can be generated manually or by other MEANS of MODx.

Creating and Editing Chunk

All Chunks are located in the following location:

Resources → Resource Management → Chunky The chunk list looks something like this:

List of Chunks in MODX EVO

To create, you need to click on the New Chunk link, and to edit an existing Chunk, just click on the link with its name. The following form appears:

New chunk in MODX EVo

Assign fields:

The name chanka is used to invoke chunk. You can use both English and Russian, as well as a hyphen (-) and an underscore (_). You can't use a space!

Description - displayed next to the name of the chunk in the general list. Used only to describe the purpose of the chunk and for filling is optional.

Create Category - allows you to select an existing category in which the chunk will be placed. The category allows you to separate the chunk from the others in the general list. If no category is selected, the chunk will be placed in the general category Without category.

New category - if there is no suitable category in the list of existing categories, you can create it simply by writing the name in this field.

Restrict access to editing chunk - if you enable the check box, no one except administrators will be able to edit this chunk.

Chunk code (html) - this is where the chunk content itself is placed.

Editor - allows you to choose a visual editor. By default, it is disabled, but you can enable it if necessary. There are also editors that allow you to highlight the syntax.

Conservation

Let's pay attention to the possibilities when saving. To do this, there are the following control buttons:

Chunk control in MODX EVO

With the main buttons, everything is clear:

Save - create a new chunk

Cancellation - will return us to the list of chunks without saving the result.

Make a copy - appears only in edit mode. See Create a copy of the chunk.

Delete - appears only in edit mode. See Removing The Chunk.

But MODx allows you to determine another action after saving the chunk:

Create a new one - immediately after saving the chunk, a form will open to create a new one. In this way, you can quickly create a series of chunks.

Continue editing - after saving, the chunk will open for editing again. In this mode, it is convenient to make small changes to the chunk and check the final result.

Close - after saving, we will return to the general list of chunks.

Create a copy of the chunk

Sometimes it is necessary to create a copy of an existing chunk. It's very easy to do. To do this, go to the editing of the desired chunk and click on the Make a copy button.

Chunk control in MODX EVO

Just in case, the system will ask you for confirmation:

Copy of the chunk in MODX EVO

This will open a copy of the chunk for editing. The copy differs in that Duplicate of is added to its name. You just have to correct the name to a more appropriate one and make other necessary changes.

A copy is created immediately after confirmation, so if you click Cancel, a copy will still remain in the chunk list.

Chunk removal

To delete, you need to go into the editing mode of the corresponding chunk and click the Delete button.

Chunk control in MODX EVO

After that, the system will ask you for confirmation:

Attention! Chunks are removed completely and there is no way to restore them.

Chunk Call

In template and other chunk

An existing chunk in a template (or other chunk) is invoked very simply. To do this, use the construction in the form of the name of the chunk surrounded by curly brackets:

{{NameChanka}} It is worth remembering that the name is case sensitive (The name Chunka and the name Chunka are different Chunks in terms of MODx).

####Пример chunk template:

{{Head}}
{{Main Menu}} {{Search}}

{{Content}}
{{Basement}}

{{Google}}

This example template contains only chunks, but in practice it also contains TV parameters and snippets. Therefore, it is not necessary to assume that chunks must be used necessarily and in large quantities.
Via API

To retrieve chunk content through the API, use the getChunk method.

####Пример call:

$chunk = $modx->getChunk('НазваниеЧанка'); FAQ

I made a chunk, but it doesn't work. Why might that be?

Check the name of the chunk. It must not contain a space, and the case of the letters must match the name of the chunk when the precision is invoked.

Can I invoke a chunk in a chunk?

Yes I do.
