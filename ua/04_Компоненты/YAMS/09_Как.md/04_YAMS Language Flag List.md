YAMS Language Flag List
=======================

> This is a user-contributed Extra. If you find issues or would like more info or help, please contact the author.

### How can I create a linked list of flags pointing to different language versions?

Use a YAMS repeat call to loop over all languages and output the flag list:

    [[YAMS?
        &get=`repeat`
        &beforetpl=`@CODE:<ul>`
        &repeattpl=`otherFlagItemTpl`
        &currenttpl=`currentFlagItemTpl`
        &aftertpl=`@CODE:</ul
    ]]

Here "otherFlagItemTpl" is a chunk that contains a linked flag image:

    <li class="yams_lang_(yams_id)">
      <a href="(yams_docr)" lang="(yams_tag)" xml:lang="(yams_tag)" dir="(yams_dir)" title="(yams_name_in_(yams_id+))">
        <img alt="(yams_name)" src="[(site_url)]assets/images/flags/(yams_id).png" />
      </a>
    </li>

and "currentFlagItemTpl" is a chunk that contains an unlinked flag image:

    <li class="yams_lang_(yams_id) yams_current">
      <img alt="(yams_name)" src="[(site_url)]assets/images/flags/(yams_id).png" />
    </li>

Flag images with the filename format (yams\_id).png should be placed in the directory "assets/images/flags/".
