## Account Activation
```
[!FormLister?
&controller=`Activate`
&formid=`activate`
&protectSubmit=`0`
&rules=`{
"email":{
	"rekired":"Be sure to enter an email",
	"email":"Enter the email correctly"
}
}`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-6 col-md-offset-3">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="activate">
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
&subject='Account Activation'
&reportTpl='@CODE:<p>To activate your account, go to <a href="[+activate.url+]">[+activate.url+]</a></p>'
&activateReportTpl='@CODE:<p>Hello, [+fullname.value+]!</p> <p>Your account has been successfully activated.</p> `
&activateSuccessTpl='@CODE:<div class="text-center">You account has been successfully activated!</div> `
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
&errorClass=` has-error`
&requiredClass=` has-warning`
!]
```
