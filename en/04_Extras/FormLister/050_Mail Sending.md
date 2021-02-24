## Sending e-mail

Form controller allows to send form data via e-mail.

## Mailer parameters
### parseMailerParams
Allows to use form data in mail sending parameters  (&to=\`[+user.email.value+]\` etc.).

Possible values - 1, 0.

Default value - 0.

### isHtml
Allows to send e-mail in html format.

Possible values - 1, 0.

Default value - 1.

### to
Receiver's address. If it's not set then the mail is not sent, but form procession is finished successfully.

Possible values - e-mail address.

Default value - none.

### from
Sender's address.

Possible values - e-mail address.

Default value - the "emailsender" configuration parameter value.

### fromName
Sender's name.

Possible values - string.

Default value - the "site_name" configuration parameter value.

### replyTo
ReplyTo header.

Possible values - e-mail address.

Default value - none.

### cc
Cс header.

Possible values - e-mail address.

Default value - none.

### bcc
Bcc header.

Possible values - e-mail address.

Default value - none.

### noemail
If it's set, then the mail isn't sent, but supposed to be sent successfully.

Possible values - 1, 0.

Default value - 0.

### ignoreMailerResult
If it's set, the mail is sent and supposed to be sent successfully. 

Possible values - 1, 0.

Default value - 0.

### subject, ccSubject, autoSubject
Letter subject.

Possible values - string.

Default value - none.

### subjectTpl, ccSubjectTpl, autoSubjectTpl 
Letter subject template.

Possible values - template name, according to DocLister templating rules.

Default value - the "subject" parameter value ("ccSubject", "autoSubject").

### autosender
Address to send additional letter.

Possible values - e-mail address.

Default value - none.

### autosenderFromName
The name of the additional letter sender.

Possible values - string.

Default value - the "site_name" configuration parameter value.

### ccSender
If it's set then the receiver's address is defined by the value of form field.

Possible values - 1, 0.

Default value - 0.

### ccSenderField
Field name containing e-mail address.

Possible values - field name.

Default value - email.

### ccSenderFromName
Sender's name for the mail sent to the form field defined address.

Possible values - string.

Default value - none.

## ccMailConfig
Allows to redefine mail sending parameters for the letters to the address taken from the form field ((isHtml, from, fromName, subject, replyTo, cc, bcc, noemail)).

Possible values - json or php array.
 
Default value - none.

## autoMailConfig
Allows to redefine mail sending parameters for the additional letters (isHtml, from, fromName, subject, replyTo, cc, bcc, noemail). 

Possible values - json or php array.
 
Default value - none.

## Submit protection
### protectSubmit
Prevents submission of the form with the same data again.

Possible values - 1, 0 or fields list to check if the form is unique. Required fields are used by default.

Default value - 1.

### submitLimit
Prevents sending mail too often.

Possible values - number of seconds between form submits.

Default value - 60.

## Templates
### reportTpl
The main template of the letter. There's the [+attachments.value+] placeholder available in reportTpl template, it contains the list of attached files. To output particular file field use the [+field name.value+] placeholder. Files are sent only in letters with reportTpl template.

Possible values - template name, according to DocLister templating rules.

Default value - the list of fields and their values.

### automessageTpl
Template of the additional letter.

Possible values - template name, according to DocLister templating rules.

Default value - reportTpl parameter value.

### ccSenderTpl
Template of the letter sent to the user defined address.

Possible values - template name, according to DocLister templating rules.

Default value - reportTpl parameter value.

### successTpl
Success message template.

Possible values - template name, according to DocLister templating rules.

Default value - lexicon entry with "form.default_successTpl" key.

## Sending files
### attachments
Field names to store files. Single file fields (name="field" type="file") and multiple file fields as simple arrays (name="field[]" type="file" multiple) are supported. 

Default value - none.

### attachFiles
Allows to send any files. 

Possible values - array:
```
&attachFiles=`{
"field ":{
    "filepath":"assets/images/logo.png",
    "filename":"logo.png"
},
"field 2":[
    {
    "filepath":"assets/images/file1.jpg",
    "filename":"report.jpg"
    },
    {
    "filepath":"assets/images/file2.jpg",
    "filename":"report2.jpg"
    }
]
}`
```
### deleteAttachments
Allows to delete attachment files if the mail is sent successfully.

Possible values - 0 or 1.

Default value - 0.
