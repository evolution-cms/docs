### Method to get a resource

string documentMethod

Possible Values:

**alias** - obtained using the passed alias

**id** - received using the passed identifier none - method not defined

Contains information about the method by which the page was retreived.  Even if an alias was used, after the resource identifier is determined, the method automatically changed to id.

#### Пример

    <?php  echo "Метод: " . $modx->documentMethod;  ?>
