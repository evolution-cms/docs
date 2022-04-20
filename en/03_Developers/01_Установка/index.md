<ul>
<li>Download the latest version of the system.</li>

  <li>Unzip the files to any folder on your local drive.</li>

  <li>Connect to the site via FTP and copy all the files from the local directory to the server.</li>

<li>Evolution uses mySQL. You need to know the username and password to access the database, or create the database and the user yourself.</li>

<li>Type your_site_name/install/ in the line of your browser. Instead of "your_site_name", enter the domain by which the site is available on the Internet.</li>

<li>Follow the on-screen instructions in the Installation Wizard.
After you complete the Installation Wizard, verify that the install folder on the server no longer exists. If it is not, delete it manually.</li>

<li>Optional: check and change the permissions to the config.inc.php file in the /manager/includes folder to -0444 (r--r--r--) - this will prevent your site from a possible attack.</li>
</ul>
