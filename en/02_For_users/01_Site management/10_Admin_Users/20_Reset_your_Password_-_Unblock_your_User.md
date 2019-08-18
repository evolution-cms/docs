<p>We all have it happen at one point in time or another… We forgot our admin interface username/password, and then trying the different options we get blocked!</p>
<h2>Database Editor to the Rescue</h2>
<p>The secret to regaining access, your database editor, usually PHPMyAdmin granted other editors will work just fine.</p>
<p>The first step is to open your database editor and browse to your Evo database.</p>
<h3>Forgotten Password</h3>
<ol>
  <li>
    <p>Open the <strong>(PREFIX)_manager_users</strong> table (where (PREFIX) is your table prefix)</p>
  </li>
  <li>
    <p>Edit the record for your username</p>
  </li>
  <li>
    <p>Change the password filed to: e10adc3949ba59abbe56e057f20f883e (Your password will be: 123456)</p>
  </li>
  <li>
    <p>Save the change</p>
  </li>
  <li>
    <p>If you aren't blocked attempt to login with the new password</p>
  </li>
  <li>
    <p>Change the password after you login!</p>
    <div class="note"><strong>Advanced Tip</strong><br>
      You can set any password by changing the drop down field type to MD5. Just enter the desired password instead of the above hash.</div>
  </li>
</ol>
<h3>Block Too</h3>
<ol>
  <li>Open the <strong>(PREFIX)_user_attributes</strong> table (where (PREFIX) is your table prefix)</li>
  <li>Edit the record for your user (The admin user is typically id 1)</li>
  <li>Change the blocked column value from 1 to 0</li>
  <li>Save the change</li>
  <li>Attempt to login using your username and password (or newly set password from above)</li>
</ol>
<h2>Limited Access</h2>
<p>In some cases you may not have access to a database editor readily available, in those cases it is still possible to restore admin interface access.  You will need to upload your own database editor, such as <a target="_blank" rel="nofollow" href="//www.phpmyedit.org/">phmyedit</a>.</p>
<p>You only need basic functionality, so a smaller editor will save you some time.  Once uploaded you can copy the database information from the Evo config file (manager/includes/config.inc.php).</p>
<p>This can be helpful should the client be abandon by their prior developer, their hosting company not provide access to a database editor, or you are in a pinch and only have FTP access.</p>
<h2>Add a user via MySQL</h2>
<p>It is possible to add a new admin user without going through the Admin Interface, if possible you should always use the admin interface.</p>
<p>You will need to add two records to different tables, your database may not have the default prefix, if this is the case look for the same table name without the default prefix.</p>
<ol>
  <li>Open the <strong>(PREFIX)_manager_users</strong> table</li>
  <li>Create a new record with the desired username and password (see forgot password for a hash to use)</li>
  <li>If you are able to run SQL commands you may optionally run:</li>
</ol>
<div><div id="highlighter_913734" class="syntaxhighlighter  php"><div class="toolbar"><span><a href="#" class="toolbar_item command_help help">?</a></span></div><table border="0" cellpadding="0" cellspacing="0"><tbody><tr><td class="gutter"><div class="line number1 index0 alt2">1</div></td><td class="code"><div class="container"><div class="line number1 index0 alt2"><code class="php plain">INSERT INTO manager_users (username,password) VALUES (</code><code class="php string">'yourname'</code><code class="php plain">,</code><code class="php string">'e10adc3949ba59abbe56e057f20f883e'</code><code class="php plain">);</code></div></div></td></tr></tbody></table></div></div>
<ol>
  <li>After adding the user make note of the ID number for your user, you will need it in a moment.</li>
  <li>Open the <strong>(PREFIX)_user_attributes</strong> table</li>
  <li>Create a new record with an InternalKey of your user ID (the number you just forgot from before), and a role of 1</li>
  <li>If you are able to run SQL commands you may optionally run (substitute the 4 with your user id):</li>
</ol>
<div><div id="highlighter_989176" class="syntaxhighlighter  php"><div class="toolbar"><span><a href="#" class="toolbar_item command_help help">?</a></span></div><table border="0" cellpadding="0" cellspacing="0"><tbody><tr><td class="gutter"><div class="line number1 index0 alt2">1</div></td><td class="code"><div class="container"><div class="line number1 index0 alt2"><code class="php plain">INSERT INTO user_attributes (InternalKey,role) VALUES (</code><code class="php string">'4'</code><code class="php plain">,</code><code class="php string">'1'</code><code class="php plain">);</code></div></div></td></tr></tbody></table></div></div>
<p>Once you have created both records you should be able to login to the manager using the username and password set in step 2.  Once logged in make sure to change your password!</p>