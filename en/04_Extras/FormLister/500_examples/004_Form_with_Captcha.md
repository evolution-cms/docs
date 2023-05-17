## Form with Captcha
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
"phone":{
	"required":"Be sure to enter your phone number",
	"phone":"Enter the number correctly"
},
"message":{
	"required":"Be sure to enter a message",
	"minLength":{
		"params":100,
		"message":"Message must be at least 100 characters"
	}
}
}`
&captcha=`modxCaptcha`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-8 col-md-offset-2">
		<div class="well">
			<form class="form-horizontal" method="post">
				<input type="hidden" name="formid" value="basic">
				<div class="form-group[+name.errorClass+][+name.requiredClass+]">
					<label for="name" class="col-sm-2 control-label">* Имя</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="name" placeholder="name" name="name" value="[+name.value+]">
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
				<div class="form-group[+phone.errorClass+][+phone.requiredClass+]">
					<label for="phone" class="col-sm-2 control-label">* Telephone</label>
					<div class="col-sm-10">
						<input type="text" class="form-control" id="phone" placeholder="+375 29 123 45 67" name="phone" value="[+phone.value+]">
						[+phone.error+]
					</div>
				</div>

				<div class="form-group[+message.errorClass+][+message.requiredClass+]">
					<label for="message" class="col-sm-2 control-label">* Message</label>
					<div class="col-sm-10">
						<textarea class="form-control" id="message" placeholder="Your Message" name="message" rows="10">[+message.value+]</textarea>
						[+message.error+]
					</div>
				</div>
				[+form.messages+]
				<div class="form-group[+vericode.errorClass+][+vericode.requiredClass+]">
					<label for="vericode" class="col-sm-2 control-label">* Enter the verification code</label>
					<div class="col-sm-10">
						<div><img src="[+captcha+]" alt="Enter a number"></div>
						<input type="text" class="form-control" id="vericode" name="vericode" value="">
						[+vericode.error+]
					</div>
				</div>
				<div class="form-group">
					<div class="col-sm-offset-2 col-sm-10">
						<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-envelope"></i> Submit</button>
					</div>
				</div>
			</form>
		</div>
	</div>
</div>`
&errorClass=` has-error`
&requiredClass=` has-warning`
&subject=`New Message`
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
!]
```
