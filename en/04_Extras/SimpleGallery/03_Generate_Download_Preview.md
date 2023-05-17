## Generate download previews
It is implemented using a plugin system. In general terms, the plugin should handle the event when loading a picture, when deleting a picture and when updating a picture. This allows you to get rid of the use of the phpthumb snippet when displaying images, which speeds up the output and does not clog the cache.

Included as an example is the sgThumb plugin. For it to work, you need to mark the OnFileBrowserUpload, OnSimpleGalleryDelete and OnSimpleGalleryRefresh events, then create a customization
```
&tconfig=Thumbnails Configuration;textarea;
```
and add to it a list of preview descriptions in json format:
```
[
{"template":3,"options":"w=320&h=200&zc=1","folder":"thumb"},
{"template":6,"options":"w=384&h=384&far=C&bg=000000","folder":"384x384"},
{"rid":9,"options":"w=500&h=500&zc=C&bg=000000","folder":"500x500"},
{"template":6,"options":"w=500&h=500&zc=C&bg=000000","folder":"500x500"}
]
```
Each rule is described by an array:
```
{"template":id_шаблона,"options":"параметры_phpthumb","folder":"имя_папки"}
```
or:
```
{"rid":id_документа,"options":"параметры_phpthumb","folder":"имя_папки"}
```
The example will create a 320x320 picture for template 3, a 500x500 picture for document 9 and two pictures for template 6: 384x384 and 500x500.

When outputting, you need to use a snippet that gets the address of the image in the input parameter and some value to get a link to the preview (for the sgThumb snippet, this is the folder name from the sgThumb plugin settings) - in the options parameter. The snippet should be returned with a link to the preview.
