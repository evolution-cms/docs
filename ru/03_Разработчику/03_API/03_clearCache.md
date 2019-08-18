### Очистка кэша сайта ###

boolean clearCache(string $type, boolean $report);

**$type** - используем с значением *full* если нужно очистить весь кеш с учетом индексных файлов

***

### Пример ###

````php
//Очистит кэш сайта.
$modx->clearCache();

//Очистит кэш сайта с учетом индексных файлов(доступно с версии 1.0.13).
$modx->clearCache('full');
````
**Важно:** выполнение функции без параметра 'type' очищает не весь кэш. При использовании этой функции удаляются файлы с кэшем всех документов, но индексный файл кэша не изменяется.

Из-за этого документы, которые были созданы программным путем, могут на сайте отсутствовать.

### Исходный код функции ###
`Файл: /manager/includes/document.parser.class.inc.php`
```
/**
 * Clear the cache of MODX.
 *
 * @param string $type
 * @param bool $report
 * @return bool
 */
public function clearCache($type = '', $report = false)
{
	$cache_dir = MODX_BASE_PATH . $this->getCacheFolder();
	if (is_array($type)) {
		foreach ($type as $_) {
			$this->clearCache($_, $report);
		}
	} elseif ($type == 'full') {
		include_once(MODX_MANAGER_PATH . 'processors/cache_sync.class.processor.php');
		$sync = new synccache();
		$sync->setCachepath($cache_dir);
		$sync->setReport($report);
		$sync->emptyCache();
	} elseif (preg_match('@^[1-9][0-9]*$@', $type)) {
		$key = ($this->config['cache_type'] == 2) ? $this->makePageCacheKey($type) : $type;
		$file_name = "docid_" . $key . "_*.pageCache.php";
		$cache_path = $cache_dir . $file_name;
		$files = glob($cache_path);
		$files[] = $cache_dir . "docid_" . $key . ".pageCache.php";
		foreach ($files as $file) {
			if (!is_file($file)) {
				continue;
			}
			unlink($file);
		}
	} else {
		$files = glob($cache_dir . '*');
		foreach ($files as $file) {
			$name = basename($file);
			if (strpos($name, '.pageCache.php') === false) {
				continue;
			}
			if (!is_file($file)) {
				continue;
			}
			unlink($file);
		}
	}
}
```