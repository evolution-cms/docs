<p>To upgrade Evo you follow almost exactly the same steps as in the Installation Guide. With one big exception. You <em>do not erase or overwrite the config.inc.php</em> file on your server. Here are the steps:</p>
<ol>
  <li>
    <p>If you have modified any of the default snippets or plugins, either rename them in the resource manager or be sure to uncheck them when you get to the step in the installation wizard which asks you which snippets and plugins to install. The upgrade process overwrites all the default snippets to ensure you have the latest versions. (If you modify any of the core distribution snippets, it is recommended you save them with a new name to prevent this from happening.)</p>
  </li>
  <li>
    <p>Backup everything. Download all your files with your FTP client to your hard drive. Use phpMyAdmin or whatever database utility you have to "dump" your entire database to your hard drive.</p>
  </li>
  <li>
    <p>Make sure everything is backed up! No kidding!</p>
  </li>
  <li>
    <p>Download and unzip the newer version of Evo.</p>
  </li>
  <li>
    <p>Upload the contents of the extracted folder to your server. Simply overwrite all the old files. The Evo archive should not contain the config.inc.php file in /manager/includes/ directory, so it won't be overwritten. But it's still good to check before uploading that it's not there, and that you have a backup of your current config.inc.php. (Did you remember to backup the files before doing this?)</p>
  </li>
  <li>
    <p>Now fire up your web browser and load the index.php file found in the /install/ directory.</p>
  </li>
  <li>
    <p>Follow the online steps. This time, right after you accept the license agreement, be sure to select the <strong><em>Upgrade</em></strong> <strong>radio button</strong>.</p>
    <div class="info">NOTE: If your MySQL version is older than 4.1, select the Advanced Upgrade and use cp1251_koi8 as the Connection character set because the the only allowable value for charset_name is cp1251_koi8 before MySQL 4.1. It is possible to add new character set mappings by editing the sql/convert.cc file in the MySQL source distribution though, so you might be possible to use other charsets too.</div>
  </li>
  <li>
    <p>If you deleted your old files instead of overwriting them, you may have to CHMOD the files and folders that are described in the <a href="documentation/getting-started/basic-installation">Installation Guide</a> to make them writable by the server, but the upgrade wizard will tell you if you need to.</p>
  </li>
  <li>
    <p>Remember to uncheck any resources in the installation what you have modified yourself, if you have not changed their names.</p>
  </li>
  <li>
    <p>Once you get to a screen that has a checkbox offering to remove install directory, make sure it's checked (This prevents people from running the installation/upgrading process again and doing a hostile take over of your site).</p>
  </li>
  <li>
    <p>After the you have finished the upgrading wizard, go back to your FTP program and make sure that the "/install/" folder is deleted. If it's not, delete it manually.</p>
  </li>
  <li>
    <p>Finally, change the permissions of your <strong>config.inc.php</strong> file in "/manager/includes" folder back to read only. If you had written it down before, use that same CHMOD setting now, or try setting to "444". This is <em>really important</em>, and will help to prevent your site from being hacked.</p>
  </li>
  <li>
    <p>Finish the upgrading wizard.</p>
  </li>
  <li>
    <p>Once things are up and running again go to Evo admin interface and clean up your plugin and snippet names if you changed anything in step 1.</p>
  </li>
  <li>
    <p>That's it, you're done. You've just upgraded Evo.</p>
  </li>
</ol>
<h3>Alternate Method</h3>
<p>Uploading a new version of Evo over the top of an old one will leave you with old files that are no longer used. Evo team members each have different ways that they like to upgrade, but here's a method that will have the least downtime:</p>
<ol>
  <li>
    <p>Download everything from your site.</p>
  </li>
  <li>
    <p>Make a copy of your database.</p>
  </li>
  <li>
    <p>Basically, make sure you have all the old files backed up so that you can restore the old version if you need to.</p>
  </li>
  <li>
    <p>Create a new <strong>local</strong> directory called EvoNew (or whatever you prefer).</p>
  </li>
  <li>
    <p>Extract the new Evo files to that directory.</p>
  </li>
  <li>
    <p>From your backup, *copy* the config.inc.php file to manager/includes</p>
  </li>
  <li>
    <p>Copy any snippets, modules, plugins, etc., that you need or have modified into the appropriate parts of EvoNew.</p>
  </li>
  <li>
    <p>Copy any images, css, template files, documents, etc., into the appropriate parts of EvoNew.</p>
  </li>
  <li>
    <p>Rename the new folders/files to "index.php-new", "manager-new", "assets-new". Don't rename "install". Upload these folders (including the "install" folder) and the "index.php-new" file. This takes a while.</p>
  </li>
  <li>
    <p>Switch the names of the existing folders/files to "index.php-old", "manager-old", "assets-old".</p>
  </li>
  <li>
    <p>From this point, your site is not working.</p>
  </li>
  <li>
    <p>Change the names of the newfolders/files to "index.php", "manager", "assets".</p>
  </li>
  <li>
    <p>Run yoursite.com/install in your browser, being sure to select Upgrade. See <a href="documentation/getting-started/basic-installation">Installation Guide</a> for more information.</p>
    <div class="info">NOTE:If your MySQL version is older than 4.1, select the Advanced Upgrade and usecp1251_koi8 as the Connection character set because the the only allowable value for charset_name is cp1251_koi8 before MySQL 4.1. It is possible to add new character set mappings by editing the sql/convert.cc file in the MySQL source distribution though, so you might be possible to use other charsets too.</div>
  </li>
  <li>
    <p>From this point, your site should be working again. If it isn't, switch the folder names back!</p>
  </li>
  <li>
    <p>You should then be able to delete all the -old directories.</p>
  </li>
  <li>
    <p>You should also, as a result, have a local backup of the old site, and a local backup of the new site.</p>
  </li>
</ol>