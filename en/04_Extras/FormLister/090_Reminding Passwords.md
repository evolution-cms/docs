## Reminding passwords

Reminder controller allows users to restore their forgotten passwords. It extends Form controller.

Password restoration process:

- user enters username or email;
- the message with a special link to restore user password is sent;
- user follows a link and enters a new password (or it's generated automatically);
- the message with the new password is sent, success message is shown.

The "to" parameter is replaced with user email. The "resetTo" parameter is required.

## Parameters
### model
Class to manage users.

Possible values - class name. Use Pathologic\EvolutionCMS\MODxAPI\modUsers model from pathologic/modxapi package in Evo 3.0.

Default value - \modUsers

### modelPath
Path to the class to manage users.

Possible values - relative file path.

Default value - assets/lib/MODxAPI/modUsers.php

### hashField
The name of a field to store user hash.

Default value - hash.

### userField
The name of the form field to get username or email.

Default value - email.

### uidField
The name of the model field to identify user from the password restoration link.

Default value - id.

### exitTo
Redirects authorized user to the target page.

Possible values - target page id.

Default value  - none.

### resetTo
A page where the password restoration link will be pointed to. It's the required parameter.

Possible values - target page id.

Default value - id of the document, where snippet call is placed.

### redirectTo
Redirects user after successful password restoring.

Possible values - targe page id.

Default value  - none.

### skipTpl
Template for the authorized user.

Possible values - template name, according to DocLister templating rules.

Default value - lexicon entry with the key [+reminder.default_skipTpl+].

### formTpl
Template for the form to identify user.

Possible values - template name, according to DocLister templating rules.

Default value  - none.

### resetTpl
Template for the form to set a new password. The password will be created automatically if there's no "resetTpl" template.

The fields to enter passwords must be named as "password" and "repeatPassword". Hidden inputs with the names from the "uidField" and "hashField" parameters are needed. The value for the "hashField" field is set via [+user.hash+] placeholder.

Possible values - template name, according to DocLister templating rules.

Default value  - none.

### successTpl
Template for the message about successful sending of the link to restore the password. User data is available.

Possible values - template name, according to DocLister templating rules.

Default value  - lexicon entry with the key [%reminder.default_successTpl%].

### resetSuccessTpl
Template for the message about successful password change. User data is available, as well as the new password ("newpassword").

Possible values - template name, according to DocLister templating rules.

Default value  - lexicon entry with the key [%reminder.default_resetSuccessTpl%].

### reportTpl
Template for the message containing the link to restore the password. User data is available. The link to restore password is available via [+reset.url+] placeholder.

Possible values - template name, according to DocLister templating rules.

Default value  - lexicon entry with the key [%reminder.default_reportTpl%].

### resetReportTpl
Template for the message about successful password change. User data is available, as well as the new password ("newpassword"). The message will not be sent if this template is absent.

Possible values - template name, according to DocLister templating rules.

Default value  - none.

### rules
Validation rules for the form to identify user.

Possible values - see "Data validation".

Default value  - none.

### resetRules
Validation rules for the form to enter a new password. 
If there are validation rules for the "password" and for the "repeatPassword" fields, then the "equals" rule for the repeatPassword field will be changed to check if these fields are equal:
```
"repeatPassword":{
    "required":"Enter the password again",
    "equals":{
        "params" : "This will be corrected automatically",
        "message":"Passwords do not match"
    }
}
```
Possible values - see "Data validation".

Default value  - none.

### passwordLength
Password length (если создается автоматически).

Possible values - a number of characters greater than 6.

Default value - 6.
