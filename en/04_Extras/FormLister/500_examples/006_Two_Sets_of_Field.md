## Two Sets of Fields
Depending on the value of the type field, different validation rules and email templates can be used.
 
### FormLister Call
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
}
}`
&entRules=`{
"entname":{
	"required":"Be sure to enter a name"
},
"entemail":{
	"required":"Be sure to enter your email",
	"email":"Enter email correctly"
},
"entphone":{
	"required":"Be sure to enter your phone number",
	"phone":"Enter the number correctly"
},
"entaddress":{
	"required":"Be sure to enter the address"
}
}`
&formControls=`type`
&default='{"type":"Natural person"}'
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-8 col-md-offset-2">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="basic">
				<div class="form-group">
					<label class="radio-inline">
						<input type="radio" name="type" value="Natural person" [+c.type.Natural person+]> Natural person
					</label>
					<label class="radio-inline">
						<input type="radio" name="type" value="Legal entity" [+c.type.Legal entity+]> Legal entity
					</label>
				</div>
				<h3>To be filled in only by individuals</h3>
				<div class="form-group[+name.errorClass+][+name.requiredClass+]">
					<label for="name">* Name</label>

						<input type="text" class="form-control" id="name" placeholder="Name" name="name" value="[+name.value+]">
						[+name.error+]

				</div>
				<div class="row">
					<div class="col-md-6">
						<div class="form-group[+email.errorClass+][+email.requiredClass+]">
							<label for="email">* Email</label>

								<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
								[+email.error+]

						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group[+phone.errorClass+][+phone.requiredClass+]">
							<label for="phone">* Telephone</label>

								<input type="text" class="form-control" id="phone" placeholder="+375 29 123 45 67" name="phone" value="[+phone.value+]">
								[+phone.error+]

						</div>
					</div>
				</div>
				<h3>To be filled in only by legal entities</h3>
				<div class="form-group[+entname.errorClass+][+entname.requiredClass+]">
					<label for="name">* Name of the company</label>
						<input type="text" class="form-control" id="entname" placeholder="Name of the company" name="entname" value="[+entname.value+]">
						[+entname.error+]

				</div>
				<div class="row">
					<div class="col-md-6">
						<div class="form-group[+entemail.errorClass+][+entemail.requiredClass+]">
							<label for="entemail">* Email</label>
								<input type="text" class="form-control" id="entemail" placeholder="Email" name="entemail" value="[+entemail.value+]">
								[+entemail.error+]
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group[+entphone.errorClass+][+entphone.requiredClass+]">
							<label for="phone">* Telephone</label>
								<input type="text" class="form-control" id="entphone" placeholder="+375 29 123 45 67" name="entphone" value="[+entphone.value+]">
								[+entphone.error+]
						</div>
					</div>
				</div>
				<div class="form-group[+entaddress.errorClass+][+entaddress.requiredClass+]">
					<label for="name">* Legal address</label>
						<input type="text" class="form-control" id="entaddress" placeholder="Legal address" name="entaddress" value="[+entaddress.value+]">
						[+entaddress.error+]

				</div>
				[+form.messages+]
				<div class="form-group">
						<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-envelope"></i> Submit</button>
				</div>
			</form>
		</div>
	</div>
</div>`
&to=`test@test.com`
&subjectTpl=`@CODE:[+type.value+]`
&reportTpl=`@CODE:
<p>Имя: [+name.value+]</p>
<p>Телефон: [+phone.value+]</p>
<p>Email: <a href="mailto:[+email.value+]">[+email.value+]</a></p>
`
&reportEntTpl=`@CODE:
<p>Company name: [+entname.value+]</p>
<p>Phone: [+entphone.value+]</p>
<p>Email: <a href="mailto:[+entemail.value+]">[+entemail.value+]</a></p>
<p>Registered office: [+entaddress.value+]</p>
`
&prepare=`typeSelector`
&errorClass=` has-error`
&requiredClass=` has-warning`
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
!]
```
### Prepare-snippet typeSelector
```
if ($FormLister->getField('type') == 'Юридическое лицо') {
	$FormLister->config->setConfig(array(
		'rules'=>$FormLister->getCFGDef('entRules'),
		'reportTpl'=>$FormLister->getCFGDef('reportEntTpl')
	));
} else {
	$FormLister->setField('type','Natural person');
}
```
