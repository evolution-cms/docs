A chunk in Evolution is a small piece of HTML code or other information that can be reused multiple times in a template, another chunk, or a snippet.

## Using chunks

### Option 1
A chunk is created for any pieces of code that will be used multiple times.
For example, you can remove the header, footer, main menu, crumbs. Thanks to this, changes can be made in one chunk, and not in several templates. It's easier and doesn't have the risk of leaving a certain template without an important change.
### Option 2
The second most common use of a chunk is templates for snippets.
Due to this, control code and design are separated. Depending on the complexity of the snippet, the number of templates may vary.
For example, to create a feedback form, you may need 3 main templates - the form, the text about successful reception, the text of the letter to the administrator with the received information. In order for the chunk to be not only part of the HTML code, but work as a template, it is necessary to indicate the appropriate places where the snippet will write its information. Placeholders play the role of such places.

**Example chunk content with placeholders:**
```
<li [+wf.classes+]>[+wf.linktext+]</li>
```
This is the template used for menu items. Accordingly, [+wf.classes+] and [+wf.linktext+] are placeholders that will be replaced by the Wayfinder snippet with the used CSS class and the name of the menu item.

In addition to these two options, a chunk can be used to store some special information. For example, you can store a set of parameters for a snippet (eg a list of files), which can be generated manually or by other means.

### Creating and editing a chunk ###

All chunks are located in the following location:
```
Elements → Chunks
```
To create, you need to click on "New Chunk", and to edit an existing chunk, just click on the link with its name.

## Assignment of fields: ##

**Chunk Name** - used to call a chunk. You can use both English and Russian, as well as hyphens and underscores. You cannot use a space!

**Description** - displayed next to the chunk name in the general list. It is used only to describe the purpose of the chunk and is not mandatory.

**Create category** - allows you to select an existing category in which the chunk will be placed. The category allows you to separate a chunk from others in the general list. If no category is selected, the chunk falls into the general "Uncategorized" category.

**New Category** - if the list of existing categories does not have the required one, you can create one by simply writing the name in this field.

**Restrict access to chunk editing** - if you enable the checkbox, no one except administrators will be able to edit this chunk.

**Chunk code (html)** - here we place the chunk code.

**Editor** - enables the visual editor. It is disabled by default, but you can enable it if necessary. There are also editors that allow syntax highlighting.

### Savings ###

Everything is clear with the main buttons:

**Save** - will create a new chunk

**Cancel** - will return us to the list of chunks without saving the result.

**Make a copy** - appears only in edit mode.

**Remove** - appears only in edit mode.

Evolution allows you to define more actions after saving a chunk:

**Create new** - immediately after saving a chunk, a form for creating a new one will open. This way, you can quickly create a series of chunks.

**Continue editing** - after saving, the chunk will open again for editing. In this mode, it is convenient to make small changes and check the final result.

**Close** - after saving, we will return to the general list of chunks.

### Creating a copy of the chunk ###
Sometimes it is necessary to create a copy of an existing chunk. It's very easy to do. To do this, you need to go to edit the desired chunk and click the "Make a copy" button.

After that, a copy of the chunk will be opened for editing. A copy differs in that the line "Duplicate of..." is added to its name. All you have to do is correct the title to a more appropriate one and make other necessary edits.

A copy is created immediately after confirmation, so if you press cancel, the copy will still remain in the list of chunks.

### Deleting a chunk
To delete, you need to enter the editing mode of the corresponding chunk and press the Delete button.
WARNING! Chunks are deleted completely and there is no way to restore them.

### Summon a chunk
An existing chunk in a template (or another chunk) is called very simply. For this purpose, the structure is used in the form of the name of the chunk surrounded by curly brackets:

```
{{ChanName}}
```
### Call chunk with parameters

Starting with Evolution 1.4.0, parameters can be passed to chunks.
```
{{mychank? &firstparam=`value` &secondparam=`value2`}}
```
Inside the chunk, the transferred parameters can be obtained by calling the placeholder of the same name.
```
[+firstparam+] and [+secondparam+]
```

It is worth remembering that the name is case-sensitive (Mychank and myChank are different chanks fromsystem poison).

## Example of a template with a chunk call: ##
```
<html>
     <head>
         {{Head}}
     </head>
     <body>
         {{menu}}
         <div class="outer">
             <div class="main">
                 {{content}}
             </div>
         </div>
     {{footer}}
     </body>
</html>
```
This example template contains only chunks, but in practice it also contains TV parameters and snippets. Therefore, it should not be assumed that chunks must be used necessarily and in large quantities.

## API ##
The getChunk method is used to get the contents of a chunk through the API.

### Example of a call:
```
$chunk = $modx->getChunk('ChunkName');
```

## FAQ
I made a chunk but it doesn't work. Why could this be?

Check the name of the chunk. It should not contain spaces, and the case of letters when called should exactly match the name of the chunk.

Is it possible to call a chunk into a chunk?

Yes.