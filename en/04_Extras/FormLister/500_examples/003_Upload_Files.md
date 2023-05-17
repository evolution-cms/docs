## Upload Files
```
[!FormLister?
&formid=`basic`
&rules=`{
"name":{
	"required":"Be sure to enter a name"
},
"email":{
	"required":"Be sure to enter your email",
	"email":"Enter email correctly"
},
"message":{
	"required":"Be sure to enter a message"
}
}`
&attachments=`first,second`
&attachFiles=`{"userfile":{"filepath":"assets/images/logo.png","filename":"logo.png"}}`
&fileRules=`{
"first":{
	"required":"Attach the document",
	"allowed":{
		"params": [ ["doc","docx","pdf"] ],
		"message": "Only Word and Pdf documents are allowed"
	},
	"maxSize" : {
		"params": 100,
		"message": "File size should not exceed 100 kb"
	}
},
"second":{
	"required":"Attach 2 pictures",
	"maxSize" : {
		"params": 1024,
		"message": "File size should not exceed 1 mb"
	},
	"allowed": {
		"params": [ ["jpg","jpeg","png","gif"] ],
		"message" : "Only images allowed"
	},
	"maxCount":{
		"params" : 4,
		"message" : "No more than 4 pictures"
	},
	"minCount":{
		"params" : 2,
		"message" : "At least 2 pictures"
	}
}
}`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-8 col-md-offset-2">
		<div class="well">
			<form class="form-horizontal" method="post" enctype="multipart/form-data">
				<input type="hidden" name="formid" value="basic">
				<div class="form-group[+name.errorClass+][+name.requiredClass+]">
					<label for="name" class="col-sm-2 control-label">* Имя</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="name" placeholder="Name" name="name" value="[+name.value+]">
						[+name.error+]
					</div>
				</div>
				<div class="form-group[+email.errorClass+][+email.requiredClass+]">
					<label for="email" class="col-sm-2 control-label">* Email</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
						[+email.error+]
					</div>
				</div>
				<div class="form-group[+message.errorClass+][+message.requiredClass+]">
					<label for="message" class="col-sm-2 control-label">* Message</label>
					<div class="col-sm-10">
						<textarea class="form-control" id="message" placeholder="Your Message" name="message" rows="10">[+message.value+]</textarea>
						[+message.error+]
					</div>
				</div>
				<div class="form-group[+first.errorClass+][+first.requiredClass+]">
					<label for="first" class="col-sm-2 control-label">* Attach a document (Word or Pdf)</label>
					<div class="col-sm-10">
						<input type="file" class="form-control" id="first" name="first">
						[+first.error+]
					</div>
				</div>
				<div class="form-group[+second.errorClass+][+second.requiredClass+]">
					<label for="second" class="col-sm-2 control-label">* Attach 2-4 pictures</label>
					<div class="col-sm-10">
						<input type="file" class="form-control" id="second" name="second[]" multiple>
						[+second.error+]
					</div>
				</div>
				[+form.messages+]
				<div class="form-group">
					<div class="col-sm-offset-2 col-sm-10">
						<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-envelope"></i> Submit</button>
					</div>
				</div>
			</form>
		</div>
	</div>
</div>`
&to=`test@test.com`
&reportTpl=`@CODE:
<p>Имя: [+name.value+]</p>
<p>Email: <a href="mailto:[+email.value+]">[+email.value+]</a></p>
<p>Сообщение: [+message:strip_tags:nl2br+]</p>
<p>Документы:[+first.value+]</p>
<p>Картинки:[+second.value+]</p>
<p>Доп.:[+userfile.value+]
<p>Вложения: [+attachments.value+]</p>
`
&errorClass=` has-error`
&requiredClass=` has-warning`
&subject=`New Message`
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
!]
```
