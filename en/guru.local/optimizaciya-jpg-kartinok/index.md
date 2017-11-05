
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<h2>optimizeJPG</h2>

<p>Гуглосервис PageSpeed Insights рекомендует «проводить базовую и расширенную оптимизацию всех изображений… При расширенной оптимизации проводится сжатие файлов JPEG и PNG (без потерь).»</p>
<p>PNG, которые используются в верстке, я сжимаю сервисом tinypng, а вот про сжатие JPG как-то не задумывался. В PageSpeed по этому поводу написано: «Для файлов JPEG рекомендуется использовать jpegtran или jpegoptim (доступно только для Linux, выполнять с параметром --strip-all).»</p>
<p>На хостинге обнаружился jpegtran, и я быстренько сделал такой плагин:</p>
<pre class="brush: php;">
$e = &$modx->event;
if (!function_exists('optimizeJPG')) {
    function optimizeJPG($file) {
        $ext = strtolower(end(explode('.', $file)));
        if ($ext == 'jpeg' || $ext == 'jpg') {
            $cmd = '/usr/bin/jpegtran -optimize -progressive -copy none -outfile '.escapeshellarg($file.'_').' '.escapeshellarg($file);
            exec($cmd, $result, $return_var);
            @rename($file.'_',$file);   
        }
    }
}
if ($e->name == "OnFileBrowserUpload" || $e->name == "OnFileManagerUpload") {
    optimizeJPG($filepath.'/'.$filename);
}
if ($e->name == "OnSimpleGalleryRefresh") {
    optimizeJPG(MODX_BASE_PATH.$sg_image);
}
</pre>
<p>Для работы плагина нужно наличие на сервере jpegtran и права на выполнение функции exec.</p>
<p>Плагин выполняет оптимизацию при загрузке картинок через KCFinder, управление файлами, SimpleGallery (для нее можно также оптимизировать уже загруженные картинки).</p>