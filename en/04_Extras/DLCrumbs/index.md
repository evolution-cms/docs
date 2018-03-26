# DLCrumbs

A snippet to build breadcrumb navigation with DocLister. You may use any of DocLister parameters in DLCrumbs call.

## Parameters
### id
Id of the current page.

Default: the value of $modx->documentIdentifier

### hideMain
Set this parameter to 0 if you need to show the link to home page.

Default: 0.

### showCurrent
Set to 1 to include current page into the end of trail.

Default: 0.

### minDocs
This parameter determines the minimum number of elements to be shown.

Default: 0.

## Templates
### tpl
Template to output a crumb.

Default: 
```
@CODE:<li itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"><meta itemprop="position" content="[+iteration+]" /><a href="[+url+]" title="[+e.title+]"  itemprop="item"><span itemprop="name">[+title+]</span></a></li>
```

### tplCurrent
Template for the current page in the trail.

Default:
```
@CODE:<li class="active" itemprop="itemListElement" itemscope itemtype="http://schema.org/ListItem"><meta itemprop="position" content="[+iteration+]" /><span itemprop="item">[+title+]</span></li>
```
### ownerTPL
Template to wrap output.

Default:
```
@CODE:<nav class="breadcrumbs"><ul class="breadcrumb" itemscope itemtype="http://schema.org/BreadcrumbList">[+crumbs.wrap+]</ul></nav>
```


