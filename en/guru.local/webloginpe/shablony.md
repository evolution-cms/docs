
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>WebLoginPE: Шаблоны</h2>

<p>Every view that is presented to the user can be customized using MODx chunks.</p>
<p>The snippet changes between views based on a post-back system. It looks for the value of $_POST['service'] to determine which view to display. In the case of the default view for a logged in user, a form is presented with two submit buttons. The buttons each have the name attribute set to "service", but a different value</p>
<pre class="brush: html">
<button type="submit" id="wlpeLogoutButton" name="service" value="logout">Log Out</button> 
<button type="submit" id="wlpeProfileButton" name="service" value="profile">Profile</button>
</pre>
<p>If the "Log Out" button is pressed, the <code>$_POST['service']</code> value is "logout" and WebLoginPE executes the code in the case 'logout': block.</p>
<h4>The services in WebLoginPE are:</h3>
<div class="row">
	<div class="col-md-4">
		<a href="javascript:void(0)" class="widget">
			<div class="widget-content themed-background-flat text-light-op">
				<span class="text-bold">Simple</span>
			</div>
			<div class="widget-content text-dark">
				<ul>
					<li>login</li>
					<li>logout</li>
					<li>profile</li>
					<li>saveprofilesimple</li>
					<li>deleteprofilesimple</li>
					<li>confirmdeleteprofilesimple</li>
					<li>registernew</li>
					<li>register</li>
					<li>forgot</li>
					<li>resetpassword</li>
					<li>activate</li>
					<li>activated</li>
					<li>default <span class="text-muted">(display login form or welcome message if user is logged in)</span></li>
				</ul>
			</div>
		</a>
	</div>

	<div class="col-md-4">
		<a href="javascript:void(0)" class="widget">
			<div class="widget-content themed-background-flat text-light-op">
				<span class="text-bold">Register</span>
			</div>
			<div class="widget-content text-dark">
				<ul>
					<li>register</li>
					<li>cancel</li>
					<li>login</li>
					<li>logout</li>
					<li>default <span class="text-muted">(display registration form)</span></li>
				</ul>
			</div>
		</a>
	</div>

	<div class="col-md-4">
		<a href="javascript:void(0)" class="widget">
			<div class="widget-content themed-background-flat text-light-op">
				<span class="text-bold">Profile</span>
			</div>
			<div class="widget-content text-dark">
				<ul>
					<li>saveprofile</li>
					<li>cancel</li>
					<li>logout</li>
					<li>deleteprofile</li>
					<li>confirmdeleteprofile</li>
					<li>default <span class="text-muted">(display your profile for editing)</span></li>
				</ul>
			</div>
		</a>
	</div>
</div>

<div class="row">
	<div class="col-md-4">
		<a href="javascript:void(0)" class="widget">
			<div class="widget-content themed-background-flat text-light-op">
				<span class="text-bold">Manager</span>
			</div>
			<div class="widget-content text-dark">
				<ul>
					<li>editprofile</li>
					<li>saveuserprofile</li>
					<li>messageuser</li>
					<li>deleteuser</li>
					<li>confirmdeleteuser</li>
					<li>default <span class="text-muted">(display a list of all the site users)</span></li>
				</ul>
			</div>
		</a>
	</div>

	<div class="col-md-4">
		<a href="javascript:void(0)" class="widget">
			<div class="widget-content themed-background-flat text-light-op">
				<span class="text-bold">Users</span>
			</div>
			<div class="widget-content text-dark">
				<ul>
					<li>viewprofile</li>
					<li>messageuser</li>
					<li>default <span class="text-muted">(display all users)</span></li>
				</ul>
			</div>
		</a>
	</div>

	<div class="col-md-4">
		<a href="javascript:void(0)" class="widget">
			<div class="widget-content themed-background-flat text-light-op">
				<span class="text-bold">Taconite</span>
			</div>
			<div class="widget-content text-dark">
				<ul>
					<li>login</li>
					<li>logout</li>
					<li>register</li>
					<li>resetpassword</li>
					<li>activated</li>
				</ul>
			</div>
		</a>
	</div>
</div>



<h3 class="sub-header text-bold"><span class="text-bold">&amp;messageTpl</span></h3>
<p>WebLoginPE will display many messages, either confirmations or errors. The message will be placed in a placeholder ([+wlpe.message+]) which you can put anywhere in your custom form or anywhere on the page.</p>
<p>When creating the chunk for &amp;messageTpl you should place "[+wlpe.message.text+]" wherever you want the actual message to show up in the template.</p>
<h4>Default:</h4>
<pre class="brush: html">
&lt;div&gt;&lt;p&gt;[+wlpe.message.text+]&lt;/p&gt;&lt;/div&gt;
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;loginFormTpl</span></h3>
<p>The view presented to the user asking for their "username" and "password". Required form field names are "username" and "password". Optional inputs are a checkbox named "rememberme" which sets a 5 year cookie, or a select named "stayloggedin" which sets a cookie for the number of seconds specified in each options value. The cookie name is "WebLoginPE" and the value is a MD5 hash of the username and password (usernames and passwords should never be set in the open because cookies are saved in plain text. That is why WebLoginPE converts them to a hash). When the user returns to your site, WebLoginPE grabs the cookie, uses an algorithm to decode the username and password, then automatically logs the user in.</p>
<h4>Default: defaultLoginFormTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeLogin">
	<form id="wlpeLoginForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeLoginFieldset">
			<legend id="wlpeLegend">Web User Login Form</legend>
			<label id="wlpeUsernameLabel" for="wlpeUsername">Username
				<input id="wlpeUsername" type="text" name="username">
			</label>
			
			<label id="wlpePasswordLabel" for="wlpePassword">Password
				<input id="wlpePassword" type="password" name="password">
			</label>
			
			<label id="wlpeStayLoggedInLabel" for="wlpeStayLoggedIn">Stay Logged In
				<select id="wlpeStayLoggedIn" name="stayloggedin">
					<option value="">No</option>
					<option value="3600">1 Hour</option>
					<option value="86400">1 Day</option>
					<option value="604800">1 Week</option>
					<option value="2678400">1 Month</option>
					<option value="315569260">Forever</option>
				</select>
			</label>
		</fieldset>
		
		<fieldset id="wlpeLoginButtons">
			<button type="submit" id="wlpeLoginButton" name="service" value="login">Login</button>
			<button type="submit" id="wlpeReminderButton" name="service" value="forgot">Forgot Password</button>
			<button type="submit" id="wlpeRegisterButton" name="service" value="registernew">Register</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;successTpl</span></h3>
<p>The view presented to the user asking for their "username" and "password". Required form field names are "username" and "password". Optional inputs are a checkbox named "rememberme" which sets a 5 year cookie, or a select named "stayloggedin" which sets a cookie for the number of seconds specified in each options value. The cookie name is "WebLoginPE" and the value is a MD5 hash of the username and password (usernames and passwords should never be set in the open because cookies are saved in plain text. That is why WebLoginPE converts them to a hash). When the user returns to your site, WebLoginPE grabs the cookie, uses an algorythm to decode the username and password, then automatically logs the user in.</p>
<h4>Default: defaultLoginSuccessTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeUser">
	<div id="wlpeUserInfo">
		<div id="wlpeWelcome">
			&lt;img id="wlpeMyProfileImg" src="[+user.photo+]" alt="[+user.username+]" title="[+user.username+]" height="30" width="30"&gt;
			<p id="wlpeWelcomeParagraph">Welcome back [+user.username+]!</p>
		</div>
		<p id="wlpeLoginCount">You have logged into [(site_name)] [+user.logincount+] times now.<br>
		Your last login was [+user.lastlogin+]</p>
		<blockquote>
			[+user.comment+]
		</blockquote>
	</div>
	<form id="wlpeUserForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeUserButtons">
			<button type="submit" id="wlpeLogoutButton" name="service" value="logout">Log Out</button>
			<button type="submit" id="wlpeProfileButton" name="service" value="profile">Profile</button>
		</fieldset>
	</form>
</div>
</pre>


<h3 class="sub-header text-bold"><span class="text-bold">&amp;registerTpl</span></h3>
<p>The view presented to the user to register for a new account. You can have a form input for every field in the database table "web_user_attributes" and all the fields set in <span class="text-bold">&amp;customFields</span><span>*</span>. When setting up your form, the input name attribute should be the same as the field name in the table. For example, the form input asking for the users mobile phone number (table field "mobilephone") should be:</p>
<pre class="brush: html">&lt;input type="text" name="mobilephone" value="[+post.mobilephone+]" /&gt;</pre>
<p>Placeholders for values in the <span class="text-bold">$_POST array</span> are available for use in your forms so that if there is an error, all the information that the user entered in your form is not lost. As you can see in the example for "mobilephone" above, the placeholder "<span class="text-bold">[+post.<em>inputname</em>+]</span>" is set for each input name attribute.</p>
<p>If you specified form fields in <span class="text-bold">&amp;inputHandler</span>, you could also use the <span class="text-bold">[+form.<em>fieldname</em>+]</span> placeholder here.</p>
<p><span class="text-bold">*</span>It is advised against providing inputs for id, internalKey, role, blocked, blockedunitl, blockedafter, failedlogincount, and sessionid as that can SERIOUSLY corrupt your entire MODx installation. Those fields should only be edited by the web master from the back end.</p>
<h4>Default Instant: defaultRegisterInstantFormTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeNewUser">
	<form id="wlpeUserRegisterForm" action="%5B~%5B*id*%5D~%5D.html" method="POST" enctype="multipart/form-data">
		<fieldset id="wlpeUserRegisterInput">
			<div id="wlpeNewUserInfo">
				<p id="wlpeRegisterInfo">Use this form to register for a new user account.<br>
					<span class="info">Filds marked with <span class="required">*</span> are required.</span>
				</p>
			</div>
			<legend>Register for a new user account</legend>
			<label for="wlpeUserRegisterEmail"><span class="required">*</span> Email
			<input id="wlpeUserRegisterEmail" type="text" name="email" value="[+post.email+]">
			</label>

			<label for="wlpeUserRegisterUserName"><span class="required">*</span> Desired User Name
			<input id="wlpeUserRegisterUserName" type="text" name="username" value="[+post.username+]">
			</label>

			<label for="wlpeUserRegisterFullName"><span class="required">*</span> Full Name
			<input id="wlpeUserRegisterFullName" type="text" name="fullname" value="[+post.fullname+]">
			</label>

			<label for="wlpeUserRegisterPassword"><span class="required">*</span> Password
			<input id="wlpeUserRegisterPassword" type="password" name="password" value="[+post.password+]">
			</label>

			<label for="wlpeUserRegisterPasswordConfirm"><span class="required">*</span> Password (confirm)
			<input id="wlpeUserRegisterPasswordConfirm" type="password" name="passwordconfirm" value="[+post.passwordconfirm+]">
			</label>

			<label for="wlpeUserRegisterPhone">Phone number
			<input id="wlpeUserRegisterPhone" type="text" name="phone">
			</label>

			<label for="wlpeUserRegisterMobile">Mobile number
			<input id="wlpeUserRegisterMobile" type="text" name="mobilephone" value="[+post.mobilephone+]">
			</label>

			<label for="wlpeUserRegisterFax">Fax number
			<input id="wlpeUserRegisterFax" type="text" name="fax" value="[+post.fax+]">
			</label>

			<label for="wlpeUserRegisterState">State
			<input id="wlpeUserRegisterState" type="text" name="state" value="[+post.state+]">
			</label>

			<label for="wlpeUserRegisterZip">Zip Code
			<input id="wlpeUserRegisterZip" type="text" name="zip" value="[+post.zip+]">
			</label>

			[+form.country+]

			<label for="wlpeUserRegisterDob">Date of birth <span class="info">(DD-MM-YYYY)</span>
			<input id="wlpeUserRegisterDob" type="text" name="dob" value="[+post.dob+]">
			</label>

			[+form.gender+]
			
			&lt;img id="wlpeUserDefaultImage" src="[+user.defaultphoto+]" alt="Default User Image" title="Default User Image" height="100" width="100"&gt;
			
			<label for="wlpeUserProfilePhoto" id="photolabel">User Photo
			<input id="wlpeUserProfilePhoto" type="file" name="photo">
			</label>
			<p id="wlpeUserProfilePhotoInfo" class="info">No bigger than 100kb. will be resized to 100 x 100.</p>
			
			<label for="wlpeUserRegisterComment">Comment/Signature
			<textarea id="wlpeUserRegisterComment" name="comment">[+post.comment+]</textarea>
			</label>
			
			&lt;img id="wlpeCaptchaImage" src="[+form.captcha+]" width="148" height="60" alt="If you have trouble reading the code, click on the code itself to generate a new random code."&gt;
			
			<label for="wlpeUserRegisterCaptcha" id="wlpeCaptchaLabel"><span class="required">*</span>Please enter the code in the image.
			<input type="text" id="wlpeUserRegisterCaptcha" name="formcode">
			</label>
			
			<p id="wlpeTermsOfServiceLabel">Terms of Service/Privacy Policy</p>
			<div id="wlpeTermsOfService">[+tos+]</div>
			
			<label for="wlpeTosCheckbox" id="wlpeTosCheckboxLabel"><span class="required">*</span>I accept the Terms of Service
				<input type="checkbox" id="wlpeTosCheckbox" name="tos">
			</label>
		</fieldset>
		
		<fieldset id="wlpeUserRegisterButtons">
			<button type="submit" id="wlpeSaveRegisterButton" name="service" value="register">Register</button>
			<button type="submit" id="wlpeCancelRegisterButton" name="service" value="cancel">Cancel</button>
		</fieldset>
	</form>
</div>
</pre>
<h4>Default Verify: defaultRegisterVerifyFormTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeRegister">
	<form id="wlpeRegisterForm" name="wlpeRegisterForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeRegisterFieldset">
			<p class="wlpeRegisterInfo">Enter your email address, your name, and your desired username in the fields below.</p>
			<p class="wlpeRegisterInfo">A password will be emailed to you with instructions on how to activate Your account.</p>
			
			<label for="wlpeRegisterEmail">Your Email Address
			<input type="text" id="wlpeRegisterEmail" name="email">
			</label>
			
			<label for="wlpeRegisterFullName">Your Full Name
			<input type="text" id="wlpeRegisterFullName" name="fullname">
			</label>
			
			<label for="wlpeRegisterUserName">Your desired username
			<input type="text" id="wlpeRegisterUserName" name="username">
			</label>
			
		</fieldset>
		<fieldset id="wlpeRegisterButtonFieldset">
			<button type="submit" id="wlpeRegisterButton" name="service" value="register">Register</button>
			<button type="submit" id="wlpeRegisterCancelButton" name="service" value="cancel">Cancel</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;registerSuccessTpl</span></h3>
<p>The view presented to the user to after successfully registering for a new account. If you want this custom view to be displayed after registration, DO NOT put the <span class="text-bold">&amp;regSuccessId</span> parameter in your call. The default is the whatever is specified in <span class="text-bold">&amp;loginFormTpl</span> so the user can log in after registering.</p>
<h4>Default: defaultLoginFormTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeLogin">
	<form id="wlpeLoginForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeLoginFieldset">
			<legend id="wlpeLegend">Web User Login Form</legend>
			<label id="wlpeUsernameLabel" for="wlpeUsername">Username
				<input id="wlpeUsername" type="text" name="username">
			</label>
			
			<label id="wlpePasswordLabel" for="wlpePassword">Password
				<input id="wlpePassword" type="password" name="password">
			</label>
			
			<label id="wlpeStayLoggedInLabel" for="wlpeStayLoggedIn">Stay Logged In
				<select id="wlpeStayLoggedIn" name="stayloggedin">
					<option value="">No</option>
					<option value="3600">1 Hour</option>
					<option value="86400">1 Day</option>
					<option value="604800">1 Week</option>
					<option value="2678400">1 Month</option>
					<option value="315569260">Forever</option>
				</select>
			</label>
		</fieldset>
		
		<fieldset id="wlpeLoginButtons">
			<button type="submit" id="wlpeLoginButton" name="service" value="login">Login</button>
			<button type="submit" id="wlpeReminderButton" name="service" value="forgot">Forgot Password</button>
			<button type="submit" id="wlpeRegisterButton" name="service" value="registernew">Register</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;tosChunk</span></h3>
<p>In your registration form, you may want your users to agree to your "<span class="text-bold">Terms Of Service / Privacy Policy</span>" before you accept their registration. You specify your terms of service chunk with this parameter, then in your registration form, use the placeholder <span class="text-bold">[+tos+]</span> (which is set by WebLoginPE to hold your tosChunk) where you want your Terms of Service to be displayed and put a checkbox with the name attribute set to "<span class="text-bold">tos</span>". You should also specify "<span class="text-bold">tos</span>" in the <span class="text-bold">&amp;regRequired</span> parameter to make sure that if they don't check it (signifying that they agree) they will not be allowed to register.</p>
<pre class="brush: html">
<p>Terms of Service/Privacy Policy</p>
<div>[+tos+]</div>
<label for="wlpeTosCheckbox"><span>*</span>I accept the Terms of Service
	<input type="checkbox" name="tos" />
</label>
</pre>
<p>The default terms of service were generated by <span class="text-bold">Kinky Solution's</span> <a href="http://www.bennadel.com/blog/819-Terms-Of-Service-Privacy-Policy-Document-Generator.htm" rel="nofollow" target="_blank">Terms Of Service / Privacy Policy Document Generator</a>.</p>
<h4>Default: <a href="#tosChunk" data-toggle="modal">defaultTosTpl</a></h4>
<div id="tosChunk" class="modal fade" tabindex="-1" role="dialog" aria-hidden="true">
<div class="modal-dialog modal-lg">
<div class="modal-content">
<div class="modal-header">
<button type="button" class="close" data-dismiss="modal" aria-hidden="true">×</button>
<h3 class="modal-title"><span class="text-bold">tosChunk</span></h3>
</div>
<div class="modal-body">
<h2 class="page-header">Web Site Terms and Conditions of Use</h2>
<h3 class="sub-header text-bold">1. Terms</h3>
<p>By accessing this web site, you are agreeing to be bound by these web site Terms and Conditions of Use, all applicable laws and regulations, and agree that you are responsible for compliance with any applicable local laws. If you do not agree with any of these terms, you are prohibited from using or accessing this site. The materials contained in this web site are protected by applicable copyright and trade mark law.</p>
<h3 class="sub-header text-bold">2. Use License</h3>
<ol>
<li>Permission is granted to temporarily download one copy of the materials (information or software) on [MODX] Guru's web site for personal, non-commercial transitory viewing only. This is the grant of a license, not a transfer of title, and under this license you may not:
<ol>
<li>modify or copy the materials;</li>
<li>use the materials for any commercial purpose, or for any public display (commercial or non-commercial);</li>
<li>attempt to decompile or reverse engineer any software contained on [MODX] Guru's web site;</li>
<li>remove any copyright or other proprietary notations from the materials; or</li>
<li>transfer the materials to another person or "mirror" the materials on any other server.</li>
</ol>
</li>
<li>This license shall automatically terminate if you violate any of these restrictions and may be terminated by [MODX] Guru at any time. Upon terminating your viewing of these materials or upon the termination of this license, you must destroy any downloaded materials in your possession whether in electronic or printed format.</li>
</ol>
<h3 class="sub-header text-bold">3. Disclaimer</h3>
<ol>
<li>The materials on [MODX] Guru's web site are provided "as is". [MODX] Guru makes no warranties, expressed or implied, and hereby disclaims and negates all other warranties, including without limitation, implied warranties or conditions of merchantability, fitness for a particular purpose, or non-infringement of intellectual property or other violation of rights. Further, [MODX] Guru does not warrant or make any representations concerning the accuracy, likely results, or reliability of the use of the materials on its Internet web site or otherwise relating to such materials or on any sites linked to this site.</li>
</ol>
<h3 class="sub-header text-bold">4. Limitations</h3>
<p>In no event shall [MODX] Guru or its suppliers be liable for any damages (including, without limitation, damages for loss of data or profit, or due to business interruption,) arising out of the use or inability to use the materials on [MODX] Guru's Internet site, even if [MODX] Guru or a [MODX] Guru authorized representative has been notified orally or in writing of the possibility of such damage. Because some jurisdictions do not allow limitations on implied warranties, or limitations of liability for consequential or incidental damages, these limitations may not apply to you.</p>
<h3 class="sub-header text-bold">5. Revisions and Errata</h3>
<p>The materials appearing on [MODX] Guru's web site could include technical, typographical, or photographic errors. [MODX] Guru does not warrant that any of the materials on its web site are accurate, complete, or current. [MODX] Guru may make changes to the materials contained on its web site at any time without notice. [MODX] Guru does not, however, make any commitment to update the materials.</p>
<h3 class="sub-header text-bold">6. Links</h3>
<p>[MODX] Guru has not reviewed all of the sites linked to its Internet web site and is not responsible for the contents of any such linked site. The inclusion of any link does not imply endorsement by [MODX] Guru of the site. Use of any such linked web site is at the user\'s own risk.</p>
<h3 class="sub-header text-bold">7. Site Terms of Use Modifications</h3>
<p>[MODX] Guru may revise these terms of use for its web site at any time without notice. By using this web site you are agreeing to be bound by the then current version of these Terms and Conditions of Use.</p>
<h3 class="sub-header text-bold">8. Governing Law</h3>
<p>Any claim relating to [MODX] Guru's web site shall be governed by the laws of the State of New York without regard to its conflict of law provisions.</p>
<p>General Terms and Conditions applicable to Use of a Web Site.</p>
<h2 class="page-header">Privacy Policy</h2>
<p>Your privacy is very important to us. Accordingly, we have developed this Policy in order for you to understand how we collect, use, communicate and disclose and make use of personal information. The following outlines our privacy policy.</p>
<ul>
<li>Before or at the time of collecting personal information, we will identify the purposes for which information is being collected.</li>
<li>We will collect and use of personal information solely with the objective of fulfilling those purposes specified by us and for other compatible purposes, unless we obtain the consent of the individual concerned or as required by law.</li>
<li>We will only retain personal information as long as necessary for the fulfillment of those purposes.</li>
<li>We will collect personal information by lawful and fair means and, where appropriate, with the knowledge or consent of the individual concerned.</li>
<li>Personal data should be relevant to the purposes for which it is to be used, and, to the extent necessary for those purposes, should be accurate, complete, and up-to-date.</li>
<li>We will protect personal information by reasonable security safeguards against loss or theft, as well as unauthorized access, disclosure, copying, use or modification.</li>
<li>We will make readily available to customers information about our policies and practices relating to the management of personal information.</li>
</ul>
<p>We are committed to conducting our business in accordance with these principles in order to ensure that the confidentiality of personal information is protected and maintained.</p>
</div>
</div>
</div>
</div>


<h3 class="sub-header text-bold"><span class="text-bold">&amp;profileTpl</span></h3>
<p>The form presented to the user which allows them to modify their attributes stored in the databse. Like <span class="text-bold">&amp;registerTpl</span>, this form can contain as many or as few of the table fields from web_user_attributes AND the extended user attributes table as you want. The difference in this form is that you can set the value of the form fields to one of the placeholders. For example the "Full Name" input would look like:</p>
<pre class="brush: html">
<input type="text" name="fullname" value="[+user.fullname+]" />
</pre>
<p>If you specified form fields in <span class="text-bold">&amp;inputHandler</span>, you could also use the <span class="text-bold">[+form.<em>fieldname</em>+]</span> placeholder here and the users selections and checks would be remembered and pre-selected or pre-checked.</p>
<h4>Default: defaultProfileTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeUser">
	<form enctype="multipart/form-data" id="wlpeUserProfileForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeUserProfileInput">
			<div id="wlpeUserInfo">
				<h3 id="wlpeProfileWelcome">Hello [+user.fullname+] ([+user.username+])!</h3>
				<p id="wlpeProfileInfo" class="info">Use this form to update your profile information</p>
			</div>
		
			<legend>Your User Profile</legend>

			<label for="wlpeUserProfileFullName">Full Name
			<input id="wlpeUserProfileFullName" type="text" name="fullname" value="[+user.fullname+]">
			</label>

			<label for="wlpeUserProfileEmail">Email
			<input id="wlpeUserProfileEmail" type="text" name="email" value="[+user.email+]">
			</label>

			<label for="wlpeUserProfilePhone">Phone number
			<input id="wlpeUserProfilePhone" type="text" name="phone" value="[+user.phone+]">
			</label>

			<label for="wlpeUserProfileMobile">Mobile number
			<input id="wlpeUserProfileMobile" type="text" name="mobilephone" value="[+user.mobilephone+]">
			</label>

			<label for="wlpeUserProfileFax">Fax number
			<input id="wlpeUserProfileFax" type="text" name="fax" value="[+user.fax+]">
			</label>

			<label for="wlpeUserProfileState">State
			<input id="wlpeUserProfileState" type="text" name="state" value="[+user.state+]">
			</label>

			<label for="wlpeUserProfileZip">Zip Code
			<input id="wlpeUserProfileZip" type="text" name="zip" value="[+user.zip+]">
			</label>

			[+form.country+]

			<label for="wlpeUserProfileDob">Date of birth <span class="info">(DD-MM-YYYY)</span>
			<input id="wlpeUserProfileDob" type="text" name="dob" value="[+user.dob+]">
			</label>

			[+form.gender+]
			
			<label for="wlpeUserProfileComment">Comment/Signature
			<textarea id="wlpeUserProfileComment" name="comment">[+user.comment+]</textarea>
			</label>

			&lt;img id="wlpeUserProfilePhotoImg" src="[+user.photo+]" alt="[+user.username+]" title="[+user.fullname+]" height="100" width="100"&gt;

			<label for="wlpeUserProfilePhoto" id="wlpeUserPhotoLabel">User Photo
			<input type="hidden" id="wlpeUserHiddenPhoto" name="userphoto" value="[+user.photo+]">
			<input id="wlpeUserProfilePhoto" type="file" name="photo" value="">
			</label>

			<p id="wlpeUserProfilePhotoInfo" class="info">No bigger than 100kb. will be resized to 100 x 100.</p>
							
			<fieldset id="wlpeNewPasswordArea">
				<legend id="wlpeNewPasswordAreaLegend">Change your password</legend>
				<p id="wlpeNewPasswordInfo">Change your password <br><span class="info">(leave blank if you do not want a new password).</span></p>

				<label for="wlpeUserProfilePassword">New Password
				<input id="wlpeUserProfilePassword" type="password" name="password" value="">
				</label>

				<label for="wlpeUserProfilePasswordConfirm">New Password (confirm)
				<input id="wlpeUserProfilePasswordConfirm" type="password" name="password.confirm" value="">
				</label>
			</fieldset>
		</fieldset>
		
		<fieldset id="wlpeUserProfileButtons">
			<button type="submit" id="wlpeSaveProfileButton" name="service" value="saveprofile">Save</button>
			<button type="submit" id="wlpeProfileDoneButton" name="service" value="cancel">Done</button>
			<button type="submit" id="wlpeProfileLogoutButton" name="service" value="logout">Logout</button>
			<button type="submit" id="wlpeProfileDeleteButton" name="service" value="deleteprofile">Delete My Profile</button>
		</fieldset>
	</form>
</div>
</pre>



<h3 class="sub-header text-bold"><span class="text-bold">&amp;userOuterTpl</span></h3>
<p>The template that works as a "wrapper" for each of your lists in type=`users`.</p>
<h4>Default: defaultUserOuterTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div class="wlpeUsersList">
	<h3 class="sub-header text-bold">[+view.title+]</h3>
	[+view.list+]
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;usersTpl</span></h3>
<p>When you have called WebLoginPE with <span class="text-bold">&amp;type=`users`</span>, each user in the databases is listed and (in the default template) their user image and username are links to a separate area that can list more details about the user and give other users a form to contact that user. Since this view may contain privileged data, you may want to use "Access Permissions" on this page. The <span class="text-bold">&amp;usersTpl</span> paramter chunk should define the structure of the block for <span class="text-bold">EACH</span> user on this page. It will loop through each user, one at a time, exchange the placeholders for their info, add it to the que, then go to the next user. When it has finished looping over each user, it will return the entire que to the page. This view has access to the <span class="text-bold">[+user.age+]</span> placeholder that calculates the user's age based on their DOB.</p>
<p>If you specified form fields in <span class="text-bold">&amp;customFields</span> parameter for register and profile, you should also specify them here to make sure placeholders are set for them.</p>
<h4>Default: defaultUsersTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div class="wlpeUserPage">
	<div class="wlpeUserPagePhoto">
		&lt;a href="[~[*id*]~]?service=viewprofile&amp;username=[+view.username+]"&gt;
			&lt;img src="[+view.photo+]" alt="[+view.photo+]" title="[+view.username+]" height="100" width="100"&gt;
		&lt;/a&gt;
		&lt;a href="[~[*id*]~]?service=viewprofile&amp;username=[+view.username+]"&gt;
			<p class="wlpeUserPageUsername">[+view.username+]</p>
		&lt;/a&gt;
	</div>
	<div class="wlpeUserPageUserContent">
		<p class="wlpeUserPageAttrUsername">Username: [+view.username+]</p>
		<p class="wlpeUserPageAttrAge">Age: [+view.age+]</p>
		<p class="wlpeUserPageAttrLastLogin">Last Login: [+view.thislogin+]</p>
		<blockquote class="wlpeUserPageAttrComment">[+view.comment+]</blockquote>
	</div>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;viewProfileTpl</span></h3>
<p>When you have called WebLoginPE with <span class="text-bold">&amp;type=`users`</span>, each user in the databases is listed and (in the default template) their user image and username are links to a separate area that can list more details about the user and give other users a form to contact that user. As with <span class="text-bold">&amp;usersTpl</span>, this view may contain privileged data, you may want to use "Access Permissions" on the calling page. The <span class="text-bold">&amp;viewProfileTpl</span> paramter chunk should define the structure of this separate area to view more details on an individual user. This view has access to the <span class="text-bold">[+view.age+]</span> placeholder that calculates the user's age based on their DOB.</p>
<p>If you specified form fields in <span class="text-bold">&amp;customFields</span> parameter for register and profile, you should also specify them here to make sure placeholders are set for them.</p>
<h4>Default: defaultViewProfileTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<table id="wlpeViewProfileTable">
	<tbody>
		<tr>
			<td colspan="2" class="wlpeViewProfileHeader"><h3 class="sub-header text-bold">Viewing the profile of "[+view.username+]":</h3></td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Username:</td>
			<td class="wlpeViewAttributeValue">[+view.username+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Full Name:</td>
			<td class="wlpeViewAttributeValue">[+view.fullname+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Email:</td>
			<td class="wlpeViewAttributeValue">[+view.email+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Phone Number:</td>
			<td class="wlpeViewAttributeValue">[+view.phone+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Mobile Phone Number:</td>
			<td class="wlpeViewAttributeValue">[+view.mobilephone+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Fax Number:</td>
			<td class="wlpeViewAttributeValue">[+view.fax+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">State:</td>
			<td class="wlpeViewAttributeValue">[+view.state+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Country:</td>
			<td class="wlpeViewAttributeValue">[+view.country+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Age:</td>
			<td class="wlpeViewAttributeValue">[+view.age+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Gender:</td>
			<td class="wlpeViewAttributeValue">[+view.gender+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Signature:</td>
			<td class="wlpeViewAttributeValue">[+view.comment+]</td>
		</tr>
		<tr>
			<td class="wlpeViewAttribute">Photo:</td>
			<td class="wlpeViewAttributeValue">&lt;img src="[+view.photo+]" alt="[+view.photo+]" title="[+view.username+]"&gt;</td>
		</tr>
		<tr>
			<td colspan="2" class="wlpeViewContact">
				<form name="wlpeViewContactForm" method="post" action="%5B~%5B*id*%5D~%5D.html">
					<fieldset id="wlpeViewContactFormFieldset">
						<h4>Contact [+view.username+]</h4>
						<label for="wlpeviewcontactsubject" id="wlpeViewContactSubjectLabel">Subject:
							<input type="text" id="wlpeViewContactSubject" name="subject">
						</label>
						
						<label for="wlpeviewcontactmessage" id="wlpeViewContactMessageLabel">Message:
							<textarea id="wlpeViewContactMessage" name="message"></textarea>
						</label>
					</fieldset>
					<fieldset id="wlpeViewContactButtons">
						<button type="submit" id="wlpeContactSend" name="service" value="messageuser">Send Message to [+view.username+]</button>
					</fieldset>
				</form>
			</td>
		</tr>
	</tbody>
</table>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;profileDeleteTpl</span></h3>
<p>The form presented to the user to confirm that they actually want to delete their account. This is presented after the user has clicked the "<span class="text-bold">Delete My Profile</span>" button on the profile page. We want to make sure they didn't click it by accident!</p>
<h4>Default: defaultProfileDeleteTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeProfileDelete">
	<form id="wlpeProfileDeleteForm" name="profileDelteForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeProfileDeleteFieldset">
			<legend id="wlpeProfileDeleteFieldsetLegend">Delete Your Profile</legend>
			<h1 id="wlpeProfileDeleteWarning" class="warning">WARNING!</h1>
			<p>You are about to delete your profile. Are you sure you want to continue?</p>
		</fieldset>
		
		<fieldset id="wlpeProfileDeleteButtonsFieldset">
			<button type="submit" id="wlpeProfileDeleteButton" name="service" value="confirmdeleteprofile">YES! DELETE my profile</button>
			<button type="submit" id="wlpeProfileCancelButton" name="service" value="doNotDelete">NO! Keep my profile</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;manageOuterTpl</span></h3>
<p>The template that works as a "wrapper" for each of your lists in type=`manager`. The default is the same as the default &amp;userOuterTpl.</p>
<h4>Default: defaultUserOuterTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div class="wlpeUsersList">
	<h3 class="sub-header text-bold">[+view.title+]</h3>
	[+view.list+]
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;manageTpl</span></h3>
<p>The template (chunk) that will be applied to each user in type=`manager`.</p>
<h4>Default: defaultManageTpl</h4>
<pre class="brush: html">
<form class="wlpeManageUsersForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
	<div class="wlpeUserPage">
		<div class="wlpeUserPagePhoto">
			&lt;img src="[+view.photo+]" alt="[+view.photo+]" title="[+view.username+]" height="100" width="100"&gt;
			<p class="wlpeUserPageUsername">[+view.username+]</p>
			<!-- These hidden fields are IMPORTANT! -->
			<input type="hidden" name="internalKey" value="[+view.internalKey+]">
			<input type="hidden" name="username" value="[+view.username+]">
		</div>
		<div class="wlpeUserPageUserContent">           
			<p class="wlpeUserPageAttrUsername"><span class="wlpeViewUsersUsername">Username</span>: [+view.username+]</p>
			<p class="wlpeUserPageAttrAge"><span class="wlpeViewUsersAge">Age</span>: [+view.age+]</p>
			<p class="wlpeUserPageAttrLastLogin"><span class="wlpeViewUsersLastLogin">Current Status</span>: [+view.status+]</p>
			
			<div class="wlpeMangeUsersButtons">
				<button class="wlpeEditButton" name="service" value="editprofile">Edit [+view.username+]</button>
				<button class="wlpeDeleteButton" name="service" value="deleteuser">Delete [+view.username+]</button>
			</div>
		</div>
	</div>
</form>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;manageProfileTpl</span></h3>
<p>The Form (chunk) that will be displayed when editing a user's attributes in type=`manager`.</p>
<h4>Default: defaultManageProfileTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeUser">
	<form enctype="multipart/form-data" id="wlpeUserProfileForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeUserProfileInput">
			<div id="wlpeUserInfo">
				<h3 id="wlpeProfileWelcome">Editing the profile of [+view.username+] ([+view.fullname+])!</h3>
				<p id="wlpeProfileInfo" class="info">Use this form to edit [+view.username+]'s profile information</p>
			</div>

			<legend>[+view.username+]'s User Profile</legend>
			
			<!-- These hidden fields are IMPORTANT! -->
			<input type="hidden" name="internalKey" value="[+view.internalKey+]">
			<input type="hidden" name="username" value="[+view.username+]">
			
			<label for="wlpeUserProfileFullName">Full Name
			<input id="wlpeUserProfileFullName" type="text" name="fullname" value="[+view.fullname+]">
			</label>

			<label for="wlpeUserProfileEmail">Email
			<input id="wlpeUserProfileEmail" type="text" name="email" value="[+view.email+]">
			</label>

			<label for="wlpeUserProfilePhone">Phone number
			<input id="wlpeUserProfilePhone" type="text" name="phone" value="[+view.phone+]">
			</label>

			<label for="wlpeUserProfileMobile">Mobile number
			<input id="wlpeUserProfileMobile" type="text" name="mobilephone" value="[+view.mobilephone+]">
			</label>

			<label for="wlpeUserProfileFax">Fax number
			<input id="wlpeUserProfileFax" type="text" name="fax" value="[+view.fax+]">
			</label>

			<label for="wlpeUserProfileState">State
			<input id="wlpeUserProfileState" type="text" name="state" value="[+view.state+]">
			</label>

			<label for="wlpeUserProfileZip">Zip Code
			<input id="wlpeUserProfileZip" type="text" name="zip" value="[+view.zip+]">
			</label>

			[+form.country+]

			<label for="wlpeUserProfileDob">Date of birth <span class="info">(DD-MM-YYYY)</span>
			<input id="wlpeUserProfileDob" type="text" name="dob" value="[+view.dob+]">
			</label>

			[+form.gender+]

			<label for="wlpeUserProfileComment">Comment/Signature
			<textarea id="wlpeUserProfileComment" name="comment">[+view.comment+]</textarea>
			</label>

			&lt;img id="wlpeUserProfilePhotoImg" src="[+view.photo+]" alt="[+view.username+]" title="[+view.fullname+]" height="100" width="100"&gt;

			<label for="wlpeUserProfilePhoto" id="wlpeUserPhotoLabel">User Photo
			<input type="hidden" id="wlpeUserHiddenPhoto" name="userphoto" value="[+view.photo+]">
			<input id="wlpeUserProfilePhoto" type="file" name="photo" value="">
			</label>

			<p id="wlpeUserProfilePhotoInfo" class="info">No bigger than 100kb. will be resized to 100 x 100.</p>

			<fieldset id="wlpeNewPasswordArea">
				<legend id="wlpeNewPasswordAreaLegend">Change your password</legend>
				<p id="wlpeNewPasswordInfo">Change your password <br><span class="info">(leave blank if you do not want to set a new password for this user).</span></p>

				<label for="wlpeUserProfilePassword">New Password
				<input id="wlpeUserProfilePassword" type="password" name="password" value="">
				</label>

				<label for="wlpeUserProfilePasswordConfirm">New Password (confirm)
				<input id="wlpeUserProfilePasswordConfirm" type="password" name="password.confirm" value="">
				</label>
			</fieldset>
		</fieldset>
		
		<fieldset id="wlpeUserProfileButtons">
			<button type="submit" id="wlpeSaveProfileButton" name="service" value="saveuserprofile">Save</button>
			<button type="submit" id="wlpeProfileDoneButton" name="service" value="cancel">Done</button>
			<button type="submit" id="wlpeProfileDeleteButton" name="service" value="deleteuserprofile">Delete This Profile</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;manageDeleteTpl</span></h3>
<p>The Form (chunk) that will be displayed asking for confirmation of intention to delete after clicking the "Delete Profile" button for a user in type=`manager`.</p>
<h4>Default: defaultManageDeleteTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeProfileDelete">
	<form id="wlpeProfileDeleteForm" name="profileDelteForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeProfileDeleteFieldset">
			<legend id="wlpeProfileDeleteFieldsetLegend">Delete User Profile</legend>
			<h1 id="wlpeProfileDeleteWarning" class="warning">WARNING!</h1>
			<p>You are about to delete the profile of "[+post.username+]". Are you sure you want to continue?</p>
		</fieldset>
		
		<fieldset id="wlpeProfileDeleteButtonsFieldset">
			<button type="submit" id="wlpeProfileDeleteButton" name="service" value="confirmdeleteuser">YES! DELETE [+post.username+]'s profile</button>
			<button type="submit" id="wlpeProfileCancelButton" name="service" value="doNotDelete">NO! Keep this profile</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;resetTpl</span></h3>
<p>The form presented when a user clicks the "Forgot Password" button. This form has only one input ("email"). They enter their email address, WebLoginPE sets a random password and key in the <span class="text-bold">web_users</span> table's <span class="text-bold">cachepwd</span> field and sends them a link to the URL of the page that this was called from with the string "<span class="text-bold">?service=activate&amp;userid=3&amp;activationkey=kl3tW5rtDi</span> where "<span class="text-bold">3</span>" would be the users <span class="text-bold">internalKey</span> and "<span class="text-bold">kl3tW5rtDi</span>" would be the randomly generated activation key which is a 10 character string.</p>
<h4>Default: defaultResetFormTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeReset">
	<form id="wlpeResetForm" name="wlpeResetForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeResetFieldset">
			<h3 id="wlpeResetInfo">Don't Worry, it happens to everyone.</h3>
			<p>Enter your email address in the field below and we will set a temporary password for your account.</p>
			<p>This temporary password will be emailed to you with instructions on how to activate it.</p>
			<label for="wlpeResetEmail">Your Email Address
			<input type="text" id="wlpeResetEmail" name="email">
			</label>
		</fieldset>
		
		<fieldset id="wlpeResetButtonFieldset">
			<button type="submit" id="wlpeResetButton" name="service" value="resetpassword">Send Password</button>
			<button type="submit" id="wlpeResetCancelButton" name="service" value="cancel">Cancel</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;activateTpl</span></h3>
<p>This form is presented when the user clicks the link in the email that was sent from the <span class="text-bold">&amp;resetTpl</span> form. It is the view for <span class="text-bold">service=activate</span>. The user is asked for the temporary password that was emailed to them and they are given the option to set a new password. WebLoginPE then checks that the <span class="text-bold">temporary password</span> and the <span class="text-bold">activationkey</span> match what was stored in the <span class="text-bold">cachepwd</span> field for the <span class="text-bold">internalKey</span> in the <span class="text-bold">web_users</span> table. If everything checks out, the new password that the user entered is activated. The default form has three input fields with the name attributes "<span class="text-bold">activationpassword</span>", "<span class="text-bold">newpassword</span>", and "<span class="text-bold">newpassword.confirm</span>".</p>
<h4>Default: defaultActivationFormTpl</h4>
<pre class="brush: html">
[+wlpe.message+]
<div id="wlpeActivate">
	<form id="wlpeActivateForm" name="wlpeActivateForm" action="%5B~%5B*id*%5D~%5D.html" method="POST">
		<fieldset id="wlpeActivateFieldset">
			<input type="hidden" name="userid" value="[+request.userid+]">
			<input type="hidden" name="activationkey" value="[+request.activationkey+]">
			
			<label for="wlpeActivationPassword">Activation password
			<input type="text" id="wlpeActivationPassword" name="activationpassword">
			</label>
			<label for="wlpeNewPassword">New password
			<input type="password" id="wlpeNewPassword" name="newpassword">
			</label>
			<label for="wlpeNewPasswordConfirm">New password (Confirm)
			<input type="password" id="wlpeNewPasswordConfirm" name="newpassword.confirm">
			</label>
		</fieldset>
		
		<fieldset id="wlpeActivateButtonFieldset">
			<button type="submit" id="wlpeActivateButton" name="service" value="activated">Activate</button>
		</fieldset>
	</form>
</div>
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;notifyTpl</span></h3>
<p>This is not a view presented to the user, but a template format for the email message that will be sent to the addresses in <span class="text-bold">&amp;notify</span>. It uses all the placeholders that are available in the Tools &gt; Configuration &gt; User &gt; Web signup email template, with the addition of [+uem+] for the user's email address. The user's password will NOT be available in this template.</p>
<h4>Default: defaultNotifyTpl</h4>
<pre class="brush: html">
Hello, my name is [+ufn+] and I just signed up at [+sname+] as "[+uid+]" using WebLoginPE.
My email address is [+uem+].
P.S. This message was auto generated by WebLoginPE and PHPMailer.
</pre>

<h3 class="sub-header text-bold"><span class="text-bold">&amp;notifySubject</span></h3>
<p>This is also not a view presented to the user, but a definition of the subject line for the email message that will be sent to the addresses in <span class="text-bold">&amp;notify</span>.</p><h4>Default:</h4>
<p>New Web User for [(site_name)].</p>