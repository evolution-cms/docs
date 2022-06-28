## SimpleFiles - attach files to the page

### SimpleFiles - attach Evolution CMS files to the page.

Another addition based on DocLister and EasyUI. This time, files are attached to the page and edited in a table - as in MultiFiles, but a little more convenient (especially if we are talking about a large number of files) (:

To work, you need a https://github.com/AgelxNash/DocLister, as well as PHP at least 5.6.

Download here: https://github.com/Pathologic/SimpleFiles

## Plugin settings
- Tab name – Tab Name;
- Controller class – controller class other than standard;
- Templates – the id of the templates with which the plugin works is mandatory;
- Documents – the same, but for individual resources;
- Ignore Documents – excluded ID resources;
- Roles – Allowed Roles;
- Storage folder – the folder where the files are stored, by default assets/storage/;
- Icons folder – the folder where the icons of files are stored, by default assets/snippets/simplefiles/icons/;
- Allowed files – extensions of files allowed for download, separated by commas; if you do not specify, the system setting will be used;
- Maximum file size – file size limit, in megabytes.

Icons should be named as _file_extension_lowercase.png_

The file.png icon is substituted if there is no suitable one.

## Display records
According to the output of the entries, we read about [SimpleGallery]:https://github.com/BBloke/docs/blob/master/en/04_Extras/SimpleFile/simplegallery/index.html [SimpleGallery].

When withdrawing through snippets-wrappers, sfLister and sfController additional virtual placeholders are available:

- [+icon+] – icon;
- [+fSize+] – formatted size value;
- [+mime+] – MIME-type of the file;
- [+ext+] – file extension;
- [+filename+] – file name without extension;
- [+basename+] – file name with extension;
- [+e.sf_title+] – the name of the file with character shielding;
- [+e.sf_description+] – description of the file with character escape.

## Fields in the _sf_files_ table

- sf_id – File id (idField);
- sf_index – position in the list;
- sf_title – file name;
- sf_description – file description;
- sf_file – link to the file;
- sf_size – file size;
- sf_isactive – checkbox to hide some files from output;
- sf_rid – the id of the resource to which the file belongs (parentField);
- sf_createdon is the date the file was added.
