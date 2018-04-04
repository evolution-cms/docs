## The Admin Interface ##

## Logging In to the admin interface ##
As of writing this documentation, the admin interface can be found in the directory called "manager". This folder / directory can be renamed to whatever you like after you have installed Evo.

### To login to your site's admin interface: ###
Go to your website, by entering your domain name then "/manager/" eg www.yourdomain.com/manager/
Enter your username and password to login to your website's administration page.

### To change your password: ###
After you have successfully logged in to the admin interface you can change your password.

### To logout: ###
In the Admin Menu in the upper right of the page click on Logout.

### To Change The Folder Name: ###
Via FTP / SFTP etc. go to your website server and change "manager" to your chosen name, once changed point your browser to the new name to login.
For example: OLD = www.yourdomain.com/manager/, NEW = www.yourdomain.com/xyz124*25/
Please note: after changing the folder name, do not view the front-end (e.g www.yourdomain.com) as you will get an error message - you have to login first.

## Introduction to the Admin Interface ##
The Admin Interface is divided into 3 areas

- Top: Main and Admin Menus
- Left: Resource tree
- Right: Main Admin Area

Additionally there is a floating panel with some action buttons. The type off buttons change according to the mode the admin interface is in (editing content, managing users and so on). The floating panel is always positioned at the top of the main admin area.

You can resize the left-hand area by dragging the middle bar (marked green in the screenshot) left or right. (The layout can also be configured differently by the site administrator)

### What is the resource tree? ###
This is a list of all the resources (e.g. pages, weblinks) in the website, arranged in a hierarchical order. This is where you select the resources you want to edit, move or delete.

The number in parentheses on the right of each resource's title is the document ID. There may be occasions when you will need to know a resource's ID. This is where you find it.

You can use the resource tree icons to perform actions on the tree. Hover your mouse cursor over the buttons for tooltips to explain their purpose.



### Are there any shortcuts? ###
Yes. You can right-click on a resource's name in the resource tree to access the contextual menu. The contextual menu gives you quick access to additional shortcuts. If you prefer left-clicks, you can open the same contextual menu by left-clicking the resource's icon wich is always shown left of the resource's name.



You can create resources and weblinks in an existing resource/container (a resource which has children is called "container" within Evo), by right-clicking on the resource/container and selecting one of the "Create ..." items in the list. This saves time moving the item from the first level after you have created it. If the container resource had no children before, it will automatically be changed to a container.
You can go directly to the Edit page of a document, without having to open the document first.

### Uploading content ###
You can upload content (e.g. PDF files and image files) using FTP or the Evo inbuilt File Manager. Images can also be uploaded using the Image icon on the document editor toolbar.


If you are using FTP, you should transfer files to the appropriate folder in the /assets folder. For example:

- Transfer images to the /assets/images folder.
- Transfer pdf and text files to the /assets/docs folder.

### Upload files and images with File Manager ###
To upload files and images:

Click on Manage Files in the Admin menu. The File manager will open.

Click on Browse to locate your file on your local PC, then click Upload file.

### Editing webpages ###
To update existing content on the site you need to:

Locate the web page (called a document) in the document tree.
Click on the document's name, or right-click and select "Edit document"
Open the page to edit.

Edit the page with the WYSIWYG editor.
Save the page.

Check in the Preview.
#### How do I preview on the live site? ####
Click on Preview on the Site main menu item.

Or keep a web page with the live site open in another window or browser tab. Then you can just refresh the page to view any changes. In Internet Explorer use CTRL + F5 if the menus don't appear correctly, or new content is not showing. If you are still having problems viewing new content, clear the server cache, by clicking on Clear Cache in the Site main menu item.