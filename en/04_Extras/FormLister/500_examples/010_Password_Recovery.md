## Password Recovery
### Option 1
The Password is generated automatically and sent via email.
```
[!FormLister?
&controller=`Reminder`
&formid=`remind`
&rules=`{
"email":{
	"required":"Be sure to enter an email",
	"email":"Enter the email correctly"
}
}`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-6 col-md-offset-3">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="remind">
				<div class="form-group[+email.errorClass+][+email.requiredClass+]">
					<label for="email">* Email</label>
						<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
						[+email.error+]
				</div>
				[+form.messages+]
				<div class="form-group">
					<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-ok-sign"></i> Далее</button>
				</div>
			</form>
		</div>
	</div>
</div>`
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&successTpl='@CODE:<div class="text-center">On the email you specified during registration, an email has been sent with further instructions!</div> `
&subject='Password Recovery'
&resetTo=`38`
&reportTpl='@CODE:<p>To recover your password, go to <a href="[+reset.url+]">[+reset.url+]</a></p>'
&resetReportTpl='@CODE:<p>Hello, [+fullname.value+]!</p> <p>Your new password: [+newpassword+]</p>'
&resetSuccessTpl='@CODE:<div class="text-center">A letter with a new password has been sent to the email you specified during registration!</div> `
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
&errorClass=` has-error`
&requiredClass=` has-warning`
!]
```

### Option 2
User selected password.
```
[!FormLister?
&controller=`Reminder`
&formid=`remind`
&rules=`{
"email":{
	"required":"Be sure to enter an email",
	"email":"Enter the email correctly"
}
}`
&resetRules=`{
"password":{
	"required":"Be sure to enter a password",
	"minLength":{
		"params":6,
		"message":"Password must be longer than 6 characters"
	}
},
"repeatPassword":{
	"required":"Repeat password",
	"equals":{
		"message":"Passwords do not match"
	}
}
}`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-6 col-md-offset-3">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="remind">
				<div class="form-group[+email.errorClass+][+email.requiredClass+]">
					<label for="email">* Email</label>
						<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
						[+email.error+]
				</div>
				[+form.messages+]
				<div class="form-group">
					<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-ok-sign"></i> Next</button>
				</div>
			</form>
		</div>
	</div>
</div>`
&resetTpl=`@CODE:
<div class="row">
	<div class="col-md-6 col-md-offset-3">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="remind">
				<input type="hidden" name="hash" value="[+user.hash+]">
				<input type="hidden" name="id" value="[+user.id+]">
				<div class="form-group[+password.errorClass+][+password.requiredClass+]">
					<label for="password">* New Password</label>
						<input type="password" class="form-control" id="password" placeholder="New Password" name="password" value="">
						[+password.error+]
				</div>
				<div class="form-group[+repeatPassword.errorClass+][+repeatPassword.requiredClass+]">
					<label for="password">* Repeat Password</label>
						<input type="password" class="form-control" id="password" placeholder="Repeat Password" name="repeatPassword" value="">
						[+repeatPassword.error+]
				</div>
				[+form.messages+]
				<div class="form-group">
					<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-floppy-disk"></i> Submit</button>
				</div>
			</form>
		</div>
	</div>
</div>
`
&uidName=`uid`
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&successTpl='@CODE:<div class="text-center">On the email you specified during registration, an email has been sent with further instructions!</div> `
&subject='Password Recovery'
&reportTpl='@CODE:<p>To recover your password, go to <a href="[+reset.url+]">[+reset.url+]</a></p>'
&resetReportTpl='@CODE:<p>Hello, [+fullname.value+]!</p> <p>Your new password: [+newpassword+]</p>'
&resetSuccessTpl='@CODE:Done!'
&resetTo=`12`
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
&errorClass=` has-error`
&requiredClass=` has-warning`
!]
```
