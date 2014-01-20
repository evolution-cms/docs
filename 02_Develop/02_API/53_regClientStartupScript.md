Подключение скриптов JavaScript к документу или блока ‹script› в область ‹head›

string regClientStartupScript(string $src[, bool $plaintext]);

$src - путь до файла JavaScript
$plaintext - разместить в виде текста переданного в $src
true - размещение в виде текста
false - размещение в виде внешнего файла или блока <script>
По умолчанию: false
Пример 1

$src = "assets/js/prototype.js"; $modx->regClientStartupScript($src);
Это добавит в документ запись:

<script type="text/javascript" url="assets/js/prototype.js"></script>
Пример 2

Можно разместить также и блок с готовым скриптом:

$src2 = "<script type='text/javascript'> function getHTML() { var url = 'testing.php'; var pars = 'return=test'; var myAjax = new Ajax.Updater( {success: 'placeholder'}, url, {method: 'get', parameters: pars}); } </script>"; $modx->regClientStartupScript($src2);
Этот блок появится в том же виде.