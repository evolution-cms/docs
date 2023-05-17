## DLBuildMenu: Templates
DLBuildMenu snippet templates - to display the site menu on Evolution CMS.
DLBuildMenu templates are defined according to the rules of DL, that is, they can be both inline templates and chunk names, or loaded from a file, from a MODx document, from a config, from a global placeholder.

### Wrapper templates
#### &TplMainOwner
The main wrapper template (for depth level 1).

The default value is:
```
@CODE:<ul id="nav" class="menu level-1">[+dl.wrap+]</ul>
```
Note: You must have the &TplMainOwner or &TplOwner1 template set, otherwise the default value of the &TplMainOwner template will be used.

#### &TplSubOwner
Wrapper template for nested levels (for submenus).

The default value is:
```
@CODE:<ul class="sub-menu level-[+dl.currentDepth+]">[+dl.wrap+]</ul>
```
Note: To display the N-level menu, you must have at least &TplSubOwner and/or &TplOwnerN templates set in addition to the main wrapper. Otherwise, the default value of &TplSubOwner will be used.

#### &TplOwnerN
The wrapper template for the Nth nesting level submenu, for the corresponding levels &TplOwnerN takes precedence over &TplMainOwner and &TplSubOwner (see Note).

Default value: None

Note: If both &TplOwner1 and &TplMainOwner are specified, &TplOwner1 will be used. If both &TplOwner2 and &TplSubOwner are specified, &TplOwner2 will be used for level 2, and &TplSubOwner will be used for levels 3.

### Menu item templates
#### &TplOneItem
Basic template for each menu item of all levels.

The default value is:
````
@CODE:<li id="menu-item-[+id+]" class="menu-item [+dl.class+]">
 <a href="[+url+]" title="[+e.title+]">[+title+]</a>
 [+dl.submenu+]
</li>
````
Note: You must have all the menu item templates you need set, at least &TplOneItem. Otherwise, for items where you have not defined a template, the default value &TplOneItem will be used.

#### &TplDepthN
The nesting menu item template N, for the corresponding levels &TplDepthN, takes precedence over &TplOneItem.

Default value: None

Note: For example, if &TplDepth2 is specified, it will replace the &TplOneItem template at the 3rd nesting level.

### Item templates without child elements
#### &noChildrenRowTPL
The main menu item template with no child elements for all levels.

Default value: None

#### &TplNoChildrenDepthN
The menu item template without child nesting elements N. For the corresponding levels, &TplNoChildrenDepthN takes precedence over &noChildrenRowTpl.

Default value: None

Note: If neither &noChildrenRowTPL nor &TplNoChildrenDepthN is specified for a menu item, the template you specified in the other parameters (&TplOneItem or &TplDepthN) will be used as the template for the "childless" items.

### Current item templates
#### &TplCurrent
The current menu item template with children takes precedence over all menu item templates except &TplCurrentN.

Default value: None

#### &TplCurrentN
The template of the current nesting menu item N with children, for the Nth level, the &TplCurrentN template takes precedence over all child menu item templates, including &TplCurrent.

The default value is None.

#### &TplCurrentNoChildrenN
The template of the current menu item without child elements, where N is the nesting level number. For level N, it takes precedence over any other "childless" menu item templates.

The default value is None.
