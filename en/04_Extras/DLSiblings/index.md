## 	DLSiblings: Output neighboring resources with templating
Output of adjacent resources with templating (multiple ring linking).
Output adjacent resources with templating (multiple ring linking)

Author: https://github.com/Aharito/DLSiblings Aharito

### Snippet parameters:
#### &idType, &parents, &documents, &ignoreEmpty
- As in DocLister.

#### &Qty
(whole), the number of previous and next neighbors. Takes precedence over &prevQty and &nextQty.

If &Qty='3', then the total number will be 6 - that is, 3 before and 3 after.

The default value is 2.

#### &prevQty
Number of predecessor neighbors. Priority less than $Qty

Default value:default 2

#### &nextQty
Number of neighbors-followers. Priority less than $Qty

Default value: 2

You can also use those inherited from DocLister (the same as its): fetch conditions &addWhereList and &filters, sort conditions &orderBy, sample depth &depth, prepare, and many other parameters.

You just need to understand whether these parameters make sense in the call. For example, if you set &idType='documents' and &documents='1,2,3' (3 documents in total), and set &Qty as 6, then these 3 documents will always be displayed - this makes no sense.

### Exclusion parameters:
* api mode is forcibly set to 1 (it makes no sense to set in the snippet)
* the debug mode is set to 0 (there is also no point in setting it).
* the &display parameter is forcibly set to &display='0' because the &Qty, &prevQty, and &nextQty parameters are responsible for the count.

### Snippet Templates
* &ownerTPL, the wrapper template is similar to DocLister, but the placeholder is NOT [+dl.wrap+], but [+wrap+]. The default value is null (the output does not turn into ownerTPL).
* &tpl, &tplOdd and &tplEven, &tplIdN, &tplFirst and &tplLast Item templates as in DocLister in ascending order of priority.
* &noneTPL Template with information that there is nothing like in DocLister. The default is empty.
* &noneWrapOuter As in DocLister, whether to wrap the noneTPL template into the ownerTPL wrapper. The &noneWrapOuter parameter makes sense only if nothing is found and the ownerTPL is specified.
No other DL templates are used.

## ATTENTION:
!!! In snippet templates, TV parameter holders are recorded NOT through a period, but through an underscore. That is, it will not be [+tv.h1+], but [+tv_h1+]. The same applies to extenders, such as extender e: instead of [+e.title+], we write [+e_title+].

In general, in template placeholders (only in them!), all points are changed to underline (see examples of snippet calls below).

### EXAMPLES
#### Example 1: A simple snippet call.
```
[[DLSiblings?
    &idType=`parents`
    &parents=`152`
    &tpl=`@CODE: <a href="[+url+]">[+tv_h1+]</a><br>`
    &Qty=`2`
    &tvList=`h1`
]]
```

#### Example 2: A more complex example with prepare and FastImage previews
```
[[DLSiblings?
    &idType=`parents`
    &parents=`152`
    &thumbSnippet=`sgThumb`
    &thumbOptions=`{"tv.article_intro_img":{"small":"280x160","medium":"700x400"}}`   // There is NO need to change the period to underlining here (this is not a template)
    &ownerTPL=`@CODE:<div class="row latest-news inline-showcase">[+wrap+]</div><hr>`                                       
    &tpl=`@CODE:
    <div class="column col-1-1-2-4-4 margin-bottom-30">   // And here everywhere needs to be changed (this is a template)           
        <div class="article-announce-img">
            <img class="img-responsive" src="[+tv_article_intro_img_medium+]" alt="[+e_title+] | [(cfg_company_brand_name)]">               
        </div>
        <div class="article-announce-content">
            <div class="article-announce-header">
                <a href="[+url+]">[+tv_h1+]</a>
            </div>
        </div>
        <a href="[+url+]" class="wrapper-link"></a>
    </div>`
    &Qty=`2`
    &tvList=`article_intro_img,h1`
    &prepare=`FastImagePreviews`
]]
```
Note: These are examples only. In order for them to work on your site, you must have the same TVs and the same prepare-snippets.

#### Output of Example 2
![siblings_demo_1](https://cloud.githubusercontent.com/assets/6253807/24569757/ea66affa-1691-11e7-8320-aa726ffd3dbc.png)

#### Speed of work
1) Number of requests, etc. when caching a snippet on a cached resource on a micro-site, sampling 4 out of 8 articles with sorting
```
&orderBy=`if(pub_date=0,createdon,pub_date) DESC`
```
¬[siblings_requests](https://cloud.githubusercontent.com/assets/6253807/24569985/4e7dedd6-1693-11e7-955c-95574150e8de.png)

2) Number of requests, etc. in case of uncushed snippet call on a cached resource on a micro-site, sampling 4 out of 8 articles with sorting
```
&orderBy=`if(pub_date=0,createdon,pub_date) DESC`
```
¬[siblings_requests_nocache](https://cloud.githubusercontent.com/assets/6253807/24570665/e1272e60-1696-11e7-8b7d-832009a2be07.png)

### Disadvantages
* Long JSON string containing all fields, including content (memory consumption)
* Formation of an additional index array $ids (time)
* As a result, the snippet is suitable for not very large samples (up to 1-2 thousand resources), for large sites a different solution is required.
