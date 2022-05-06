## DLBuildMenu: 
### Basiic Parameters
Basic parameters of the DLBuildMenu snippet - to display the site menu on Evolution CMS.
#### &idType (hardcoded)
The sample type is similar to DocLister.

Possible values are: parents

Note: The value of the &idType parameter is hard-coded as parents.

#### &parents
The parent (start) folder.

The possible values are parent ID, or a comma-separated list of parent IDs.

The default value is: 0

Note: Note that in DLBuildMenu, the default value of &parents is 0, which means "output starting from the site root". This is different from the default value of the &parents parameter in DockLister.

#### &currentDepth
Initial nesting level (depth).

The possible values are an integer of 1 or greater.

The default value is: 1

#### &maxDepth
Max. depth

The possible values are an integer of 1 or greater.

The default value is: 5

#### &BeforePrepare and &AfterPrepare
Data processing through prepare is similar to DocLister.

Possible values: set according to The DockLister's rules. They can be a list of snippet names and method calls rather than loaded classes, or an anonymous function.

Note: For prepare, DLBuildMenu already has a built-in mandatory call to DLFixedPrepare::buildMenu. Handlers from &BeforePrepare are called before the built-in call, from &AfterPrepare after the built-in call.

#### &activeClass
The CSS class of the active (current) menu item and its parent elements of all levels.

Possible notations: The name of the CSS class, or multiple CSS class names specified as in the HTML tag (with a space).

Default value: active

Note: This CSS class and this parameter exist in addition to the first, last, odd, even, and current classes already in Docklister and their corresponding parameters (see the DocLIster documentation).
