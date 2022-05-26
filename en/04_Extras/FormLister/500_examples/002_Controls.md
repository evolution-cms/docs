## Form with Controls
```
[!FormLister?
&formid=`advanced`
&rules=`{
"name":{
	"required":"Be sure to enter a name"
},
"email":{
	"required":"Be sure to enter your email"
},
"phone":{
	"required":"Be sure to enter your phone number",
	"phone":"Enter the number correctly"
},
"message":{
	"required":"The case cannot be empty",
	"minLength":{
		"params":100,
		"message":"Must be at least 100 characters"
	}
},
"agree":{
	"required":"You cannot send a request if you do not agree with the rules"
},
"products":{
	"minCount":{
		"params": 2,
		"message": "Select at least 2 products"
	}
}
}`
&defaults=`{
"topic":"Complaint"
}`
&formControls=`topic,agree,department,products`
&formTpl=`@CODE:
<div class="row">
	<div class="col-md-8 col-md-offset-2">
		<div class="well">
			<form method="post">
				<input type="hidden" name="formid" value="advanced">
				<div class="form-group[+name.errorClass+][+name.requiredClass+]">
					<label for="name">* Name</label>
						<input type="text" class="form-control" id="name" placeholder="Name" name="name" value="[+name.value+]">
						[+name.error+]
				</div>
				<div class="row">
					<div class="col-md-6">
						<div class="form-group[+email.errorClass+][+email.requiredClass+]">
							<label for="email">* email</label>
								<input type="text" class="form-control" id="email" placeholder="Email" name="email" value="[+email.value+]">
								[+email.arrow+]
						</div>
					</div>
					<div class="col-md-6">
						<div class="form-group[+phone.errorClass+][+phone.requiredClass+]">
							<label for="phone">* Phone</label>
								<input type="text" class="form-control" id="phone" placeholder="+375 29 123 45 67" name="phone" value="[+phone.value+]">
								[+background.arrow+]
						</div>
					</div>
				</div>
				<div class="form-group">
					<label for="department">Service office</label>
					<select name="department" class="form-control">
					  <option value="1" [+s.department.1+]> Head Office</option>
					  <option value="2" [+s.department.2+]>Office in the Western Region</option>
					  <option value="3" [+s.department.3+]>Office in the suburbs</option>
					</select>
				</div>
				<div>
					<label for="topic">The topic of the appeal</label>
				</div>
				<div class="form-group">
					<label class="radio-inline">
						<input type="radio" name="topic" value="Complaint" [+c.topic.Complaint+]> Complaint
					</label>
					<label class="radio-inline">
						<input type="radio" name="topic" value="Offer" [+c.topic.Offer+]> Proposal
					</label>
				</div>
				<div class="form-group[+products.errorClass+]">
					<label for="products">Какими продуктами вы пользуетесь</label>
					<div class="checkbox">
						<label>
							<input type="checkbox" name="products[]" value="1" [+c.products.1+]>
							Product 1
						</label>
					</div>
					<div class="checkbox">
						<label>
							<input type="checkbox" name="products[]" value="2" [+c.products.2+]>
							Product 2
					  </label>
					</div>
					<div class="checkbox">
						<label>
							<input type="checkbox" name="products[]" value="3" [+c.products.3+]>
							Product 3
					  </label>
					</div>
					[+products.error+]
				</div>
				<div class="form-group[+message.errorClass+][+message.requiredClass+]">
					<label for="message">* Body text</label>
						<textarea class="form-control" id="message" placeholder="Message" name="message" rows="10">[+message.value+]</textarea>
						[+message.arrow+]
				</div>
				<div class="checkbox[+agree.requiredClass+]">
				  <label>
					<input type="checkbox" name="agree" value="Yes" [+c.agree.Yes+]>
					I agree with the rules for processing requests
				  </label>
					[+agree.error+]
				</div>
				[+form.messages+]
				<div class="form-group">
					<button type="submit" class="btn btn-primary"><i class="glyphicon glyphicon-envelope"></i> Send</button>
				</div>
			</form>
		</div>
	</div>
</div>`
&to=`test@test.com`
&subjectTpl=`@CODE: [+topic.value+] в [+department.value+]`
&reportTpl=`@CODE:
<p>Имя: [+name.value+]</p>
<p>Телефон: [+phone.value+]</p>
<p>Email: <a href="mailto:[+email.value+]">[+email.value+]</a></p>
<p>Продукты: [+products.value+]</p>
<p>Сообщение: [+message:strip_tags:nl2br+]</p>
`
&errorClass=` has-error`
&requiredClass=` has-warning`
&subject='New Message'
&messagesOuterTpl=`@CODE:<div class="alert alert-danger" role="alert">[+messages+]</div>`
&errorTpl=`@CODE:<span class="help-block">[+message+]</span>`
!]
```
