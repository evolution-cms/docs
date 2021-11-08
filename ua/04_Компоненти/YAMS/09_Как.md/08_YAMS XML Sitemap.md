YAMS XML Sitemap
================

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

### How to create a single multilingual sitemap with YAMS

This creates a single XML sitemap listing all documents in all languages. It assumes that all web documents are multilingual. If the site will contain mono- and multilingual documents, then the DocLister call will need to be more sophisticated.

Two DocLister calls will be required. One DocLister call will loop over all documents that are associated with multilingual templates and one which loops over all documents associated with monolingual templates.

This can be achieved using DocLister's `&filter` parameter. The multilingual DocLister call will need to be placed in a chunk and repeated using the YAMS snippet call described below.

1.  Create a new template called XMLSitemap

2.  Include the following in your XMLSitemap template:


    <?xml version="1.0" encoding="[(modx_charset)]" ?>  
    <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">  
      [*content*]
    </urlset>

3.  Go to "Modules => YAMS => Multilingual Templates". Select "no" for XMLSitemap and submit.

4.  Create a new template variable.

    **Name:** UrlsetChangeFreq  
    **Caption:** Change Frequency  
    **Description:** Specify how often this page is likely to be updated. Be honest!  
    **Input type:** DropDown List Menu  
    **Input option values:** always||hourly||daily||weekly||monthly||yearly||never  
    **Default value:** yearly (or monthly, or whatever)

    Associate the template variable with all your templates except XMLSitemap.

5.  Create another new template variable

    **Name:** UrlsetPriority  
    **Caption:** Priority  
    **Description:** If it is more / less important that google scans this page than other pages, give it a value higher/lower than 0.5. (Range 0…1)  
    **Input type:** Number  
    **Input option values:** (leave blank)  
    **Default value:** 0.5

    Associate the template variable with all your templates except XMLSitemap.

6.  The snippet call might look something like this:


    [!DocLister?
      &parents=`0,5`
      &tpl=`UrlsetURL`
      &depth=`3`
      &dateSource=`pub_date`
      &dateFormat=`%Y-%m-%d`
      &addWhereList=`hidemenu=0`
      &addWhereList=`published=1`
      &orderBy=`menuindex ASC`
      &tvList=`UrlsetChangeFreq,UrlsetPriority`
      &filters=`id:isno:5,16,39,73,106`
    !]

where "UrlsetURL" is another chunk with the following contents

    <url>
    <loc>(yams_doc:[+id+])</loc>
    <lastmod>[+date+]</lastmod>
    <changefreq>[+UrlsetChangeFreq+]</changefreq>
    <priority>[+UrlsetPriority+]</priority>
    </url>

  This DocLister call specifies that there are maximum of 3 levels of folders - which can make the DocLister call significantly more efficient in my experience, and excludes weblinks and unsearchable documents from the sitemap.

7.  Create a new document with the alias "sitemap.xml" that lives outside your web root folder. Select the XMLSitemap template. Set the content type to text/xml. For the content, use


    [[YAMS?
        &get=`repeat`
        &repeattpl=`SitemapRepeatTpl`
    ]]
    

Hey presto - multilingual XML Sitemap. In addition, you can specify the change frequency and priority via the template variables attached to each document.
