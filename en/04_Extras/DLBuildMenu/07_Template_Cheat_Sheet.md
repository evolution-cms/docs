## DLBuildMenu: Template Priority Cheat Sheet
Priorities of DLBuildMenu snippet templates - to display the site menu on Evolution CMS.
The DLBuildMenu template system is really very flexible, but it takes some getting used to. To simplify the task below I give cheatsheet (cheatsheet) for template priorities.

The left column lists the types of menu items, and to the right of each item are the templates applied to it in descending order of priority.

| Menu item type | Top Priority | Priority 1 | Priority 2 | Priority 3 | Priority 4 | Priority 5 |
| --- | --- | --- | --- | --- | --- | --- |
| Full menu wrapper (level 1) | &TplOwner1 | &TplMainOwner | default value &TplMainOwner |			
| Sub-menu wrapper (level N is 2 or more) | &TplOwnerN | &TplSubOwner |	default value &tplSubOwner |
| Not the current menu item with children (any level N) | &TplDepthN | &TplOneItem | default value &TplOneItem |
| Not the current menu item with no children (any level N) | &TplNoChildrenDepthN | &noChildrenRowTPL | &TplDepthN | &TplOneItem | default value &TplOneItem |
| Current menu item with children (any level N) | &TplCurrentN | &TplCurrent | &TplDepthN | &TplOneItem  | default value &TplOneItem |
| Current menu item with no children (any level N) | &TplCurrentNoChildrenN | &TplNoChildrenDepthN | &noChildrenRowTPL | &TplDepthN | &TplOneItem | default value &TplOneItem |
