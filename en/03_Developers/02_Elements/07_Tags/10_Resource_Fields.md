This is a listing of all of the (currently) available document-specific resource fields. Each one is a field in the Evo site_content table. They are accessed with **[*resource-field-name*]** tags. These values can also usually be retrieved from the array.

```
$modx->documentObject['resource-field-name']
```

**id** - The document's ID. Can also be obtained with $modx->documentIdentifier.
**type** - Whether document, folder or weblink.
**contentType** - The content type, such as text/html.
**pagetitle** - The title of the page.
**longtitle** - The longtitle of the page.
**description** - The description of the page.
**alias** - The alias of the page. Used in creating Friendly URLs.
**link_attributes** - The Link Attributes of the page, eg. rel=, target= etc.
**published** - [0|1] Whether or not the document is published.
**pub_date**- Date the document is to be published. This is not a "normal" date, and must be processed by a script for meaningful output.

```
Example: strftime("%d/%m/%y %H:%M:%S", $value)
```

**unpub_date** - Date the document is to be unpublished. See 'pub_date'.
**parent** - The ID of the document's parent.
**isfolder** - [0|1] Whether or not the document is a folder.
**introtext** - The summary of the document.
**content** - The content of the document.
**richtext** - [0|1] Whether or not a RichText Editor is to be used when editing the document.
**template** - The ID of the template to used for the document.
**menuindex** - The order in which the document is to be listed in the menu.
**searchable** - [0|1] Whether or not the document is to be searchable.
**cacheable** - [0|1] Whether or not the document is to be cached.
**createdby** - The user ID of the creator of the document.
**createdon** - The date the document was created. See pub_date.
**editedby** - The ID of the user who last edited the document.
**editedon** - The date the document was last edited. See pub_date.
**deleted** - [0|1] Whether or not the document has been deleted (but not yet completely removed from the database by emptying the trash).
**deletedon** - The date the document was deleted. See pub_date.
**deletedby** - The ID of the user who deleted the document.
**menutitle** - The title to be shown in the menu. If empty, the pagetitle is used.
**donthit** - [0|1] Disable page hit count for the document.
**haskeywords** - [0|1] Whether or not the document has links to keywords.
**hasmetatags** - [0|1] Whether or not the document has links to meta tags
**privateweb** - [0|1] Whether or not this document has been assigned to a private web document group.
**privatemgr** - [0|1] Whether or not this document has been assigned to a private admin document group.
**content_dispo** - [0|1] Whether the document's content-disposition is attachment or inline.
**hidemenu** - [0|1] Whether or not the document is to be hidden in the menu

http://www.evolution-docs.com/documentation/designing/adding-tags/resource-fields
need copy this. Done.

Is it the same as this page: https://github.com/BBloke/docs/blob/master/en/03_Developers/02_Elements/06_Template_Variables/index.md
