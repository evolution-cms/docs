<p>The primary reason for setting up web users and groups is to be able to secure access to selected pages on the web. Users on the web are stored separately and apart from admin (back-end) users for security reasons. A web user cannot log into the back-end nor can a back-end user log into the web site (front-end). You would have to use separate accounts to do this. Here's how it works:</p>
<p>Back-end users are assigned to back-end user groups:</p>
<p><img src="assets/images/docs/y_users_1.gif" alt=""></p>
<p>Web users are assigned to web groups:</p>
<p><img src="assets/images/docs/y_users_2.gif" alt=""></p>
<p>Both "Back-end User Groups" and "Web User Groups" can be assigned to the same "Document Group".</p>
<p><img src="assets/images/docs/y_users_3.gif" alt=""></p>
<h2 id="WhyWebUsersandGroups-AnExample">An Example</h2>
<p>From the Web (Front-end):</p>
<p><img src="assets/images/docs/y_users_4.gif" alt=""></p>
<p>From the Admin (Back-end):</p>
<p><img src="assets/images/docs/y_users_5.gif" alt=""></p>
<div class="info"><strong>Note:</strong> A document is flagged as private whenever the document group that it belongs to is assigned or is linked to a user group. In other words if the document is assigned to a document group that is not yet linked to a user group then that document will be made public. Documents that are private to the admin users will not be private to web users if the document group is not assigned to a web user group and vice versa.</div>
