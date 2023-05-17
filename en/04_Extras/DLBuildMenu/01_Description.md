## DLBuildMenu: 

### Brief Description
Brief description of the DLBuildMenu snippet - for displaying the site menu on Evolution CMS.

DLBuildMenu is a snippet for displaying the site menu on Evolution CMS. Built on the basis of DocLister, in fact it is a snippet wrapper with a call to DocLister inside - so it can use almost all the parameters and chips of the DocLister itself.

By applying prepare, we get unlimited possibilities of data preparation. And the developed template system of DocLister, supplemented in DLBuildMenu with new parameters, gives in my hands, in my opinion, even an excessively rich toolkit.

### Dependencies and requirements
* For DLBuildMenu to work, you must have DocLister installed (available in recent releases of MODx Evo by default).
* Requires PHP 5.3 or later.

### Installation
* DLBuildMenu is included by default in the new custom assembly MODx Evo 1.2.1-d9.1.2 from 21.03.2017.
* On older custom builds and on the official build, to install it, you need to install or reinstall the DockLister from Extras, while you need DLBuildMenu to be marked with a check mark in the list during installation.

### Files
* assets/snippets/DocLister/snippet. DLBuildMenu.php
* assets/snippets/DocLister/lib/DLFixedPrepare.class.php (buildMenu method)

### Advantages of DLBuildMenu
* it is possible to use prepare to process data before output.
* a wide range of ways to set templates, including inline templates.
* sorting by TV-parameters with conversion to the desired type.
* can filter by TV parameters.
* you can come up with and set your own parameters and process them in prepare.

In addition, DLBuildMenu has other chips from the DocLister arsenal, which I will not describe here, for this you need to study the DL itself.
