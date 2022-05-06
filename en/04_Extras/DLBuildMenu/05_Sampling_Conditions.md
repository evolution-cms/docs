## DLBuildMenu: Sampling Condition Settings
Parameters of DLBuildMenu snippet selection criteria - to display the site menu on Evolution CMS.
### &addWhereList
Document selection criteria for all levels.

Possible values: set as in DocLister (according to MySQL rules for the WHERE condition).

The default value is: c.hidemenu = 0

### &addWhereListN
The sampling criteria for N-th level documents for the corresponding levels &addWhereListN takes precedence over &addWhereList.

Possible values: Specified by MySQL rules for the WHERE condition.

Default value: None

Note: If &addWhereListN is not specified, &addWhereList is used for all tiers.
