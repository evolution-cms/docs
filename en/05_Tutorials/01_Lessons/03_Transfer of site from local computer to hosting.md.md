### Packing files

If you have access to the hosting via the SSH protocol and are allowed to use decompression of archives, then transferring files as an archive is easier and fastest. Also, the ability to unpack archives can be accessed from the hosting control panel.

All files from the site folder on the local computer are packed into a ZIP archive. In this case, it is better to make the file name simple and short.

If you do not have SSH access, decompression through the panel or decompression is prohibited by the hoster, then you will have to transfer all files in the usual way.

### Database dump

The easiest way to make a database dump is to use the phpMyAdmin program.

Choose the base of our site. Go to the "Export" section Select all tables to export You can check the box next to Add Delete Table to erase tables with old data. Check the "Send" checkbox to save the dump as a file. Transfer files to the server

Open any FTP-manager and transfer files, including database dump, to the folder of your site.

### Working with SSH

After logging in to the server console, type mc.

### Unzip the files

Go to the folder with our site (if not). Unpack the files from the archive (let's say that our archive is called www.zip):

unzip www.zip

All files will be unpacked into the folder where the archive is located.

Set write permissions

For the CMS to work correctly, you need to set write permissions for the following folders and files:

assets/cache assets/cache/siteCache.idx.php assets/cache/sitePublishing.idx.php assets/images assets/export Заливаем дамп в базу на хостинге

The easiest way is to use phpMyAdmin again.

If you don't have a database, you need to create one. If there is, then select your database and go to the SQL tab to execute the query. After the window for entering the request, it is possible to specify a file. That's what we're going to take advantage of. Click browse and select your file. It is important that the encoding of the dump file matches the specified encoding. Send a file with a request. Verify that the data is migrated correctly

To verify the correctness of the migrated data, open the _site_content table (prefix). This table contains all the documents, so you should see your Russian texts. If the text is crooked, your file may have been in the wrong encoding.

## Configure MODx

### Connection to the database.

Open the file manager/includes/config.inc.php (it is better to make a copy, not to overwrite the local version) and correct the following data:

$database_server = 'localhost'; Sometimes the database server is located separately on the hosting, so you may need to specify the direct address of the server $database_user = 'MyUser'; Specify the login to access the database $database_password = ' MyPassword '; accordingly password for access $database_connection_charset = 'utf8'; encoding of received data from the database We copy the file via FTP to the hosting.

### Configure file paths

Go to the MODx control system. In the menu, select Toolbox -> Configuration. There, select the HTML Settings tab - > of the editor and interface and correct the File Path setting (specify the direct path on the hosting).

Go to the Other tab and also change the path in the Path field for the file manager.

### Additional encoding check

To finally make sure that everything works correctly and the encodings are correct everywhere, open any document (for example, the main one, so as not to go far). There we write such a line and IshSH and save. Go to the site and see the result. If everything is shown correctly, then the transfer is done correctly.

### Site Upgrade

If you also captured the local cache during the migration (and you certainly captured it), it is better to clear the cache. To do this, select the item in the menu Site -> Update Site.
