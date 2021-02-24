## Удаление профиля пользователя

DeleteUser controller allows authorized users to delete their profiles. Password is required to confirm deletion. 

Extends Form controller.

All user data is available.

## Параметры
### model
Class to manage users.

Possible values - class name. Use Pathologic\EvolutionCMS\MODxAPI\modUsers model from pathologic/modxapi package in Evo 3.0.

Default value - \modUsers

### modelPath
Path to the class to manage users.

Possible values - relative file path.

Default value - assets/lib/MODxAPI/modUsers.php

### redirectTo
Redirects user after successful action.

Possible values - target page id or array.

Default value - none.

### exitTo
Redirects non-authorized user.

Possible values - target page id or array.

Default value - none.

### skipTpl
Template for non-authorized user.

Possible values - template name, according to DocLister templating rules.

Default value - lexicon entry with the key [%deleteUser.default_skipTpl%]

### successTpl
Success message template. 

Possible values - template name, according to DocLister templating rules.

Default value - empty.
