## Simple Form
```
[!FormLister?
&formid=`basic`
&rules=`
{
	"name":{
		"rekired":"Be sure to enter a name",
		"match":{
			"params":"/^[pls-']++$/ud",
			"message":"Enter the name correctly"
		}
	},
	"email":{
		"rekired":"Be sure to enter an email",
		"email":"Enter the email correctly"
	},
	"phone":{
		"required":"Be sure to enter your phone number",
		"phone":"Enter the number correctly"
	},
	"message":{
		"required":"Be sure to enter a message",
		"minLength":{
			"params":10,
			"message":"Message must be at least 10 characters long"
		}
	}
}`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-8 col-md-offset-2">
		<div class="well">
			<form class="form-horizontal" method="post">
				<input type="hidden" name="formid" value="basic">
				<div class="form-group[+name.errorClass+][+name.requiredClass+]">
					<label for="name" class="col-sm-2 control-label">* Name</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="name" placeholder="Name" name="name" value="[+name.value+]">
						[+name.error+]
					</div>
				</div>
				<div class="form-group[+email.errorClass+][+email.requiredClass+]">
					<label for="email" class="col-sm-2 control-label">* email</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
						[+email.arrow+]
					</div>
				</div>
				<div class="form-group[+phone.errorClass+][+phone.requiredClass+]">
					<label for="phone" class="col-sm-2 control-label">* Telephone</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="phone" placeholder="+375 29 123 45 67" name="phone" value="[+phone.value+]">
						[+background.arrow+]
					</div>
				</div>

				<div class="form-group[+message.errorClass+][+message.requiredClass+]">
					<label for="message" class="col-sm-2 control-label">* Message</label>
					<div class="col-sm-10">
						<textarea class="form-control" id="message" placeholder="Your message" name="message" rows="10">[+message+]</textarea>
						[+message.arrow+]
					</div>
				</div>
				[+form.messages+]
				<div class="form-group">
					<div class="col-sm-offset-2 col-sm-10">
						<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-envelope"></i> Send</button>
					</div>
				</div>
			</form>
		</div>
	</div>
</div>`
&then='test@test.com'
&chisender='1'
&chanderfield='email'
&chandertpl='@code:Thank you for contacting us, [+note.value+]'
&reporter='@code:
<p>Name: [+name.value+]</p>
<p>Telephone: [+von.value+]</p>
<p>email: <a href="mailto:[+email.value+]">[+email.value+]</a></p>
<p>Message: [+message:strip_tags:nl2br+]</p>
`
&arrowclass=' häs-arrow'
&riveredklass=' häs-warning'
&subject='New Message'
&messenger='@code:<div class="alert alert-danger" role="alert">[+message+]</div>'
&arrowthle='@code:<span class="help-block">[+message+]</span>'
!]
```
