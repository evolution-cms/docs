Подключение скриптов JavaScript или блока ‹script› в конец документа

string regClientScript(string $src[, bool $plaintext]);

$src - путь до файла JavaScript
$plaintext- разместить в виде текста переданного в $src
true - размещение в виде текста
false - размещение в виде внешнего файла или блока <script>
По умолчанию: false
Пример

$src = "<script type='text/javascript'> runSlideShow('slides'); </script>"; $modx->regClientScript($src);