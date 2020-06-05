YAMS Language Select Landing Page
=================================

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

### How can I make a language selection site start / landing page?

1.  Create a new template to use for the landing page.

2.  From within the YAMS Module, select that template as monolingual or multilingual as required. (If the landing page is multilingual then YAMS can be set-up to guess the language to display based on the user's browser settings. See the Other Params tab.)

3.  Modify the Evo site start document to use the landing page template

4.  Create a chunk containing the following template called "LandingPageRepeat", say:


    <li>
      <a href="(yams_docr:docId)" title="[[YAMS? &get=`data` &from=`pagetitle` &docid=`docId`]]">
        (yams_name)
      </a>
    </li>

 Replace "docId" by the identifier of the document that the user will to be redirected to from the landing page.

5.  Somewhere in the template, use the following code to include a hyperlinked list of all available languages:


    <ul>
      [[YAMS?
          &get=`repeat`  
          &repeattpl=`LandingPageRepeat`
      ]]
    </ul>
