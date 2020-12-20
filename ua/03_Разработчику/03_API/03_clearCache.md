### Очистка кешу сайту ###

boolean clearCache(string $type, boolean $report);

**$type** - використовуємо зі значенням *full* якщо потрібно очистити весь кеш з врахуванням індексних файлів

***

### Приклад ###

````php
//Очистить кеш сайту.
$modx->clearCache();

//Очистить кеш сайту з врахуванням індексних файлів(доступно з версії 1.0.13).
$modx->clearCache('full');
````
**Важливо:** виконання функції без параметру 'type' очищає не весь кеш. При використанні цієї функції видаляються файли з кешем всіх документів, але індексний файл кешу не змінюється.

Через це документи, які були створені програмним шляхом, можуть бути відсутні на сайті.

### Початковий код функції ###
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