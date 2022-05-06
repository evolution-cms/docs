## DLBuildMenu: Collation
Sorting parameters of the DLBuildMenu snippet - to display the site menu on Evolution CMS.

### &orderBy
Sorting conditions for documents of all levels

Possible values: set as in DocLister (according to mySQL rules for ORDER BY).

Default value: menuindex ASC, id ASC

### &orderByN
Document sorting criteria of the Nth nesting level, for the corresponding levels & orderBy takes precedence over &orderBy.

The possible values are set according to the MySQL rules for ORDER BY.

Default value: None

Note: If &orderByN is not specified, &orderBy is used for all levels.
