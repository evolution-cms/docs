Download the latest version of the system (at the time of writing this document it was version 1.4.23 or 3.1.15) 

Unzip the files to any folder on your local drive. For example, c:\temp\modx_1.4.23

If you are going to install MODx on a UNIX/Linux system, create an empty file named config.inc.php in the manager/includes/ folder. 
Now you need to upload the files from the specified directory to the root directory of your site. 

Note: here we mean the root directory for html documents (often they are called http, htdocs, html, etc.). 

If you do not want to install MODx in the root directory, you can install the system in any other directory - the installation process will be the same. For convenience, we will assume that you are installing MODx in the root directory of the site. So, connect to the site via FTP and copy all the files from the local directory (for example, we previously adopted c:\temp\modx_1.4.23) to the server. 

If the site is running UNIX operating systems (FreeBSD or Linux), then to start configuring the system directly, you need to fulfill these prerequisites: The following directories on your site must have access rights 0777: 

/assets/cache (and all files it contains) 
/assets/export
/assets/images 
/assets/modules (for installing modules)
/manager/includes/config.inc.php (must have read-only access later) 

(refer to the documentation of your ftp client to learn how to set the necessary access rights for the above directories). 

MODx uses the MySQL DBMS. You need to know the username and password to access the database (or create the database and user yourself) in order to install MODx on the site. If your user does not have the rights to create a database, then you need to take care of this in advance. Contact your hosting provider's support team or refer to the MySQL documentation if you are configuring the software yourself. 

Now that everything is ready to configure the system on the site, type www.your_site_name/install/ in the line of your browser. Instead of "your_site_name", enter the domain by which the site is accessible on the Internet. 

Remember that if you have uploaded the system files not to the root directory of the site, then you need to add the path to this directory to the "name of your_site". For example, if you have uploaded files to the modx folder on your site, then to configure the system you need to type in the browser line www.name_of_your_site/modx/install/index.php Follow the instructions of the installation wizard that appears on the screen. Immediately after the license agreement, make sure that the "Update" option is selected. When you see the "Delete /install folder" option, make sure it is enabled. (Deleting this folder will prevent malicious users from running the update/installation script.) After completing the installation wizard, use ftp to verify that the /install folder does not exist. If it is not, delete it manually. Finally, change the permissions of the config.inc.php file in the /manager/includes folder to read-only. 

Recommended installation via CHMOD -0444 (r--r--r--) - this will prevent your site from a possible attack. Note: On servers that are running IIS, you do not need to do this. Source: MODx - Wikibooks
