YAMS Mime-type Dependent Alias Suffixes
=======================================

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

### How can I get YAMS to use the .xml suffix for xml documents, .rss for rss documents, etc.

There is an option to do this: set "Modules => YAMS => Other Params => URL Formatting => Use Mime-type dependent suffixes" to "yes", then clear the cache so that document URLs are regenerated.

The default mime-type => suffix mapping is as follows:

    $this->itsMimeSuffixMap = array(
      'application/xhtml+xml' => '.xhtml',
      'application/javascript' => '.js',
      'text/javascript' => '.js',
      'application/rss+xml' => '.rss',
      'application/xml' => '.xml',
      'text/xml' => '.xml',
      'text/css' => '.css',
      'text/html' => '.html',
      'text/plain' => '.txt'
    );

This can be changed by editing the "assets/modules/yams/yams.config.inc.php" file directly.

**WARNING:**  
It is not necessary to use the SEO Strict URLs plugin in combination with YAMS since YAMS has SEO friendly behaviour built in. Furthermore, the plugin is not compatible with YAMS.
