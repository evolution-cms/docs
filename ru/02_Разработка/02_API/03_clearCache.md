###Очистка кэша сайта

boolean clearCache([string $type]);

**$type** - используем с значением *full* если нужно очистить весь кеш с учетом индексных файлов

***

####Пример

````php
//Очистит кэш сайта.
$modx->clearCache();

//Очистит кэш сайта с учетом индексных файлов(доступно с версии 1.0.13).
$modx->clearCache('full');
````
*Замечание: Выполнение функции без параметра 'type' очищает не весь кэш. При использовании этой функции удаляются файлы с кэшем всех документов, но индексный файл кэша не изменяется. Из-за этого документы, которые были созданы программным путем, могут на сайте отсутствовать.*

***

####Полная очистка кэша для версий < 1.0.13

````php
function clearCache() {
    global $modx;
    $modx->clearCache();
    include_once MODX_MANAGER_PATH . 'processors/cache_sync.class.processor.php';
    $sync = new synccache();
    $sync->setCachepath(MODX_BASE_PATH . "assets/cache/");
    $sync->setReport(false);
    $sync->emptyCache();
}
````