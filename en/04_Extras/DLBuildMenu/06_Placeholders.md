## DLBuildMenu: Placeholders
DLBuildMenu snippet placeholders - to display the site menu on Evolution CMS.
### Major placeholders
#### [+dl.wrap+]
With its help, the generated HTML code of the menu/submenu is substituted into the wrapper template for output.

Note: Used only for wrapper templates &TplMainOwner, &TplSubOwner and &TplOwnerN.

#### [+dl.submenu+]
The generated HTML code of the submenu is substituted here along with the wrapper template.

Note: Used for menu item templates, both current and current.

#### [+dl.currentDepth+]
The current nesting level (the current depth).

Note: Note that the current nesting level starts at 1.

#### [+dl.class+]
It works in the same way as in DocLister, automatically adding classes last, first, current, even, odd respectively for the last, first, current, even and odd points. It also adds a class from the &activeClass parameter to the current item and its parent elements at all levels.

Note: The last, first, current, even, odd, and active classes can be overridden in the &lastClass, &currentClass, &firstClass, &evenClass, &oddClass, and &activeClass parameters.

#### [+url+]
URL resource is similar to DocLister.

#### [+e.title+]
The escaped value of menutitle or pagetitle (if menutitle is empty) is similar to Docklister.

#### [+id+]
The resource ID is similar to DocLister.

### Other docLister placeholders
You can use other DockLister placeholders installed by the site_content controller and various extenders.

For example, placeholders of the form [+tvPrefix.tvName+], placeholders of escaped values of the form [+e.fieldName+] (where fieldName is the field name of the table site_content), [+date+] and others (see documentation for DocLister).
