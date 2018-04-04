<h2>Before You Begin</h2>
<p>Make sure that "Use access permissions" is set to Yes in the User tab of Tools -&gt; Configuration.</p>
<h3>Adding the User</h3>
<p>To add the web user, follow these steps:</p>
<ol>
  <li>
    <p>Log in to the Evo Admin Interface.</p>
  </li>
  <li>
    <p>Next, Click the "New web user" link.</p>
  </li>
  <li>
    <p>Fill out the necessary information in the fields provided. Username, Password, Full name and E-mail address are required fields.</p>
    <div class="info"><strong>Note:</strong> Passwords are not stored in plain text form, so make sure you take note of the password if you do not have it emailed to the new user!</div>
  </li>
  <li>
    <p>You can also set a login home page in the "User Settings" tab and enter the document ID (the document ID can easily be seen in the Document Tree panel to the right) in the field provided.</p>
  </li>
  <li>
    <p>Finally, select the user group(s) to which you want the user to be assigned.</p>
  </li>
  <li>
    <p>Click the Save button to save the user.</p>
  </li>
</ol>
<p>Now that we've successfully created our web user account and have assigned the user to a web user group, we can secure documents by assigning them to a corresponding document group.</p>
<h3>Setting up the login snippet</h3>
<p>In order for the web users to be able to access your secure pages you must provide them with a login screen. To do this you can use the [[WebLogin]] Snippet. See the WebLogin snippet for more information.</p>
<div class="info"><strong>Note:</strong> Pages with cache enabled will cache new menu items when a web user logs in. It's best to either not cache your restricted pages or use non-cacheable menu snippet tags ([!…!]).</div>