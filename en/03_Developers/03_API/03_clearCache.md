### Clear the site cache

boolean clearCache([string $type]);

$type - use with a value of full if you need to clear the entire cache taking into account index files

#### Example
```php
// Clears the site cache.
$modx->clearCache();

Clears the site cache based on index files (available since version 1.0.13).
$modx->clearCache('full');
```

Note: Running a function without the 'type' parameter does not clear the entire cache. When you use this feature, the files that contain the cache of all documents are deleted, but the index cache file is not modified. Because of this, documents that were created programmatically may not be available on the site.

### Full cache clear for < versions 1.0.13
```php
function clearCache() {
    global $modx;
    $modx->clearCache();
    include_once MODX_MANAGER_PATH . 'processors/cache_sync.class.processor.php';
    $sync = new synccache();
    $sync->setCachepath(MODX_BASE_PATH . "assets/cache/");
    $sync->setReport(false);
    $sync->emptyCache();
}
```