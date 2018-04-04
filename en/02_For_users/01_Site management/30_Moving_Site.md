<p>This tutorial is based on a typical scenario, which is developing locally (XAMPP on Win XP Pro) and deploying on a typical remote (LAMP-Linux Apache MySQL PHP) server environment.</p>
<p>The same steps will work for any source server with little or no modification, unless to the .htaccess file or the method of accessing your database.</p>
<ol>
  <li>
    <p>Install the site locally, renaming and editing the .htaccess file to indicate the subdirectory you are deploying your site into in the test environment, as in the following example with a local development copy of the Evo CMS site at /localhost/sitecms/:</p>
    <div><div id="highlighter_716192" class="syntaxhighlighter  php"><div class="toolbar"><span><a href="#" class="toolbar_item command_help help">?</a></span></div><table border="0" cellpadding="0" cellspacing="0"><tbody><tr><td class="gutter"><div class="line number1 index0 alt2">1</div><div class="line number2 index1 alt1">2</div><div class="line number3 index2 alt2">3</div><div class="line number4 index3 alt1">4</div><div class="line number5 index4 alt2">5</div><div class="line number6 index5 alt1">6</div><div class="line number7 index6 alt2">7</div></td><td class="code"><div class="container"><div class="line number1 index0 alt2"><code class="php plain">RewriteEngine On</code></div><div class="line number2 index1 alt1"><code class="php plain">RewriteCond %{REQUEST_FILENAME} !-f</code></div><div class="line number3 index2 alt2"><code class="php plain">RewriteCond %{REQUEST_FILENAME} !-d</code></div><div class="line number4 index3 alt1"><code class="php plain"># If your Evo installation is in a subdirectory, change the following line to</code></div><div class="line number5 index4 alt2"><code class="php plain"># match the physical path to the </code><code class="php string">"root"</code> <code class="php plain">of the site </code><code class="php keyword">as</code> <code class="php plain">follows:</code></div><div class="line number6 index5 alt1"><code class="php plain"># RewriteRule ^(.*)$ /path/to/subdirectory/index.php?q=</code><code class="php variable">$1</code> <code class="php plain">[L,QSA]</code></div><div class="line number7 index6 alt2"><code class="php plain">RewriteRule ^(.*)$ /Evo/index.php?q=</code><code class="php variable">$1</code> <code class="php plain">[L,QSA]</code></div></div></td></tr></tbody></table></div></div>
    <p>Rename the ht.access file in the /manager folder to .htaccess. This will turn off the RewriteEngine for that folder.</p>
  </li>
  <li>
    <p>After developing the site locally (using all relative paths from the site root, to keep it portable), make a copy of .htaccess and call it .htaccess.local, editing the path on the .htaccess file for the remote deployment location as appropriate (usually removing the subdirectory path). The .htaccess file in /manager should be left as it is.</p>
  </li>
  <li>
    <p>Then make a copy of manager/includes/config.inc.php as config.local.inc.php, and edit config.inc.php with the remote database connection settings for the deployment server (the remote db must be already created and ready to use)</p>
  </li>
  <li>
    <p>Copy the /manager, /assets, /index.php, and /.htaccess folders and files to the target LAMP server (you can optionally exclude *.local.*). If this is an upgrade and not a new installation, make sure to save your remote site's /assets folder first, then you can re-upload all of your existing content, such as images and templates, if the upload has overwritten any of it.</p>
  </li>
  <li>
    <p>Unless you are in an environment where the webserver runs as the same username with which file ownership is attributed on the target server, you will need to change permissions on the following directories/files to 777:</p>
    <ul>
      <li>/assets/cache (and all files ending with .php in this directory)</li>
      <li>/assets/images</li>
      <li>/assets/files</li>
      <li>/assets/flash</li>
      <li>/assets/media</li>
    </ul>
  </li>
  <li>
    <p>Dump (export) the local DB contents (use the Backup Manager, or any MySQL client such as phpMyAdmin). In phpMyAdmin, select SQL for the file type. Save to a file on your local machine and note the location. You will probably want to empty any log tables before backing them up, or else you'll have rows and rows of log data useless to your new server.Then go to the remote server and import the SQL dump you saved. In PhPMyAdmin, select the database and "import" the SQL file.</p>
  </li>
  <li>
    <p>Point your browser at "http://domain_of_your_new_site.com/manager". After logging in, go to Adminstration -&gt; System configuration and change the paths for the resource browser (Resource Path and Resource URL in System Settings -&gt; Interface &amp; Editor Settings tab) and the filemanager (File Manager Path at System Settings -&gt; Miscellaneous Settings tab)</p>
  </li>
  <li>
    <p>If you can't access the admin interface, you may have the wrong database settings in "manager/includes/config.inc.php". Try correcting them on the local machine and uploading the file again. If you still can't access the admin interface, try going to "http://domain_of_your_site.com/install" and doing a "custom install". There you can try different database settings and test them until you get a connection. As long as you haven't hacked any of the Evo code on the local machine, you can finish the install. Alternately, you can put the correct settings (now that you know them) in "manager/includes/config.inc.php" and upload it.</p>
  </li>
  <li>
    <p>Test the remote site. It should be working just the same as your local development site.</p>
  </li>
  <li>
    <p>If things still aren't right, try doing an upgrade install on the new site.</p>
  </li>
</ol>
