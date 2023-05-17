## User Registration

When registering, the user is added to the opt group. Two letters are sent - to the manager and the user. The user must confirm the registration by clicking on the link from the letter (see Account Activation).
 
```
[!FormLister?
&formid=`register`
&controller=`Register`
&userGroups=`opt`
&checkActivation=`1`
&activateTo=`1514`
&rules=`{
"fullname":{
	"required":"Be sure to enter a name"
},
"email":{
	"required":"Be sure to enter your email",
	"email":"Enter email correctly"
},
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
},
"agree":{
	"required":"To register you must accept the rules"
}
}`
&allowedFields=`fullname`
&formControls=`agree`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-6 col-md-offset-3">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="register">
				<div class="form-group[+fullname.errorClass+][+fullname.requiredClass+]">
					<label for="fullname">* Name</label>
						<input type="text" class="form-control" id="fullname" placeholder="Name" name="fullname" value="[+fullname.value+]">
						[+fullname.error+]
				</div>
				<div class="form-group[+email.errorClass+][+email.requiredClass+]">
					<label for="email">* Email</label>
						<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
						[+email.error+]
				</div>
				<div class="row">
					<div class="col-md-6">
						<div class="form-group[+password.errorClass+][+password.requiredClass+]">
							<label for="password">* Password</label>
								<input type="password" class="form-control" id="password" placeholder="Password" name="password" value="">
								[+password.error+]
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group[+repeatPassword.errorClass+][+repeatPassword.requiredClass+]">
							<label for="repeatPassword">* Repeat password</label>
								<input type="password" class="form-control" id="repeatPassword" placeholder="Repeat password" name="repeatPassword" value="">
								[+repeatPassword.error+]
						</div>
					</div>
				</div>
				<div class="checkbox[+agree.requiredClass+]">
				  <label>
					<input type="checkbox" name="agree" value="Yes" [+c.agree.Yes+]>
					I agree with the rules
				  </label>
					[+agree.error+]
				</div>
				[+form.messages+]
				<div class="form-group">
					<button type="submit" class="btn btn-primary btn-block text-center"><i class="glyphicon glyphicon-user"></i> Зарегистрироваться</button>
				</div>
			</form>
		</div>
	</div>
</div>`
&to=`info@sitename.com`
&reportTpl='@CODE:New user [+fullname.value+] ([+id.value+])'
&ccSender=`1`
&ccSenderField=`email`
&ccSenderTpl='@CODE:Hello [+fullname.value+]. To activate your account, go to <a href="[+activate.url+]">[+activate.url+]</a>'
&subject='Registration on the site [(site_name)]'
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&successTpl='@CODE:<div>Congratulations on your successful registration, [+fullname.value+]! After activation, you can <a href="[~11~]">authorrect</a> on the site. If you have not received an email to activate your account, <a href="[~1514~]">requere again</a>.</div> `
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
&errorClass=` has-error`
&requiredClass=` has-warning`
!]
```
