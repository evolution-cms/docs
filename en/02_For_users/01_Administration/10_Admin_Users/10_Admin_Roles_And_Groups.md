
<p>Using Admin Roles, Document Groups, and Admin User Groups you can control every aspect of the management of your Evo site.</p>
<h3 id="AdminRolesAndGroups-BeforeYouBegin">Before You Begin</h3>
<p>Make sure that "Use access permissions" is set to Yes in the User Settings tab of System Configuration.</p>
<p><img src="assets/images/docs/user-settings.jpg" alt=""></p>
<h3 id="AdminRolesAndGroups-ThePieces">The Pieces</h3>
<p>Permissions in Evo are composed of many parts that all work together. At first, it can be a little confusing as to what all the parts are, what they do, and how they interact. For that reason, each part will be explained below, followed by an example:</p>
<ul>
  <li><strong>Document</strong> - The fundamental element (a "page") in Evo. Each document is assigned to one or more document groups.</li>
  <li><strong>Document group</strong>- As it sounds. A group of documents that for some reason are placed in the same group. A common example of this would be the main sections of a site (such as Products, Portfolio, or Services). A document group can be connected with one or more user groups.</li>
  <li><strong>User</strong>- The user piece contains information about the specific user such as name, password, etc. The user piece does NOT define the permissions. Permissions are defined in the role. Each user can be assigned to one or more user groups, but can only be assigned to one role.</li>
  <li><strong>Role</strong> - As just mentioned, the role is the piece that defines the permission of any user who is assigned that role.</li>
  <li><strong>User group</strong>- A collection of users who will need access to the same document groups. A user group can be connected to one or more document groups.</li>
</ul>
<p>So how do all these work together? Roles determine what a user has permission to do, and user groups combined with document groups determine what documents a user can work with. An example will probably the be most effective way to demonstrate this.</p>
<p>Suppose you have a site to distribute the software your company writes. You also want to have a discussion and help forum. You decide that your site will look like this:</p>
<ul>
  <li>Home</li>
  <li>News</li>
  <li>Products
    <ul>
      <li>Games</li>
      <li>Graphics Utilities</li>
      <li>Project Management</li>
    </ul>
  </li>
  <li>Support
    <ul>
      <li>FAQ</li>
      <li>Forums</li>
      <li>Contact Us</li>
      <li>Live Support Chat</li>
    </ul>
  </li>
  <li>About Us
    <ul>
      <li>Our history</li>
      <li>Our philosophy</li>
      <li>Our people</li>
    </ul>
  </li>
</ul>
<h3 id="AdminRolesAndGroups-Roles">Roles</h3>
<p>First, you decide you will need these Roles:</p>
<ul>
  <li><strong>Site administrators</strong> - will manage users and general site configuration.</li>
  <li><strong>Developers</strong> - will create the code used in special applications, such as the Live Support Chat feature. Will handle modules, plug-ins, snippets, and TVs</li>
  <li><strong>Designers</strong> - will be responsible for the overall look and layout of the site's pages. Will work with templates, chunks, and CSS.</li>
  <li><strong>Content editors</strong> - will be responsible for the content of the pages. Will work with documents.</li>
  <li><strong>Proofreaders</strong> - will be able to edit, but not create or delete documents.</li>
</ul>
<p><img src="assets/images/docs/role3.jpg" alt=""><br>
  <img src="assets/images/docs/role5.jpg" alt=""></p>
<h3 id="AdminRolesAndGroups-DocumentGroups">Document Groups</h3>
<p>Next, consider how the documents in your site will be grouped.</p>
<ul>
  <li><strong>Corporate</strong> - pages referring to the company in general, such as the About Us pages and the Home page.</li>
  <li><strong>Product</strong> - pages dealing with individual products.</li>
  <li><strong>Support</strong> - pages that contain FAQ lists or company contact information.</li>
</ul>
<p><img src="assets/images/docs/access2.jpg" alt=""></p>
<h3 id="AdminRolesAndGroups-UserGroups">User Groups</h3>
<p>Then you begin to organize the User groups your content editor users will belong to.</p>
<ul>
  <li><strong>Marketing</strong> - will handle Corporate pages; anything that will effect the public's perception of the company and its products.</li>
  <li><strong>Products</strong> - will work with the pages relevant to the company's products.</li>
  <li><strong>Support</strong> - will take care of the support pages.</li>
  <li><strong>Proofreaders</strong> - will have access to all documents (but is limited in what he can do with them by the permissions granted by his Role).</li>
</ul>
<p><img src="assets/images/docs/access1.jpg" alt=""></p>
<p>Here is how the user groups and documents groups will interact.</p>
<p><img src="assets/images/docs/usermap.png" alt=""></p>
<h3 id="AdminRolesAndGroups-ImportantNote">Important Note</h3>
<p>A user can belong to any number of User Groups, but he can be assigned to only one Role. For example, if you want one of the Proofreader users to also be a Support document editor, you will have to create a different User for him to log in as, and assign that user to the Support user group.</p>
<p>Remember, Roles assign permissions - WHAT the user can do. User groups assign WHICH DOCUMENTS the user can work with, but he can only do what the role he was assigned to allows.</p>
<h3 id="AdminRolesAndGroups-Usergroups>Documentgroups">User groups-&gt;Document groups</h3>
<p>Now we need to connect the user groups to the document groups we want them to have access to. For example, the Proofreaders user groups will be connected to ALL of the document groups, since his job will be to correct errors in all documents. The Marketing user group should have access to the Corporate and the Support document groups. And of course the Product user group should be connected to the Product document group.</p>
<p><img src="assets/images/docs/access3.jpg" alt=""></p>
<p>Now, as documents are created, they need to be assigned to the proper Document groups. As users are created, they are assigned to a certain Role, then to their proper User Groups. Only users belonging to user groups connected to a given document's document group can have access to that document. Even if a user has access to a given document, he can only do with it what his individial Role assignment allows.</p>
<p>In this way, the Roles, User and Document Groups system allows a fine-grained control of individual document and admin user interaction.</p>
