# regClientScript
### Подключение скриптов JavaScript в документ

string regClientScript(string $src[, bool $plaintext]);

**$src** - путь к файлу JavaScript или код JavaScript

**$plaintext** - разместить в виде:
+ true: в $src передан инлайн-код между `<script>`, вставить его перед `</body>`
+ false: в $src передана ссылка на файл

По умолчанию: **false**

#### Пример 1: $plaintext = true
```
$src = "<script type='text/javascript'> runSlideShow('slides'); </script>"; 
$modx->regClientScript($src, true);
```

Будет:
```
...
<script type='text/javascript'> runSlideShow('slides'); </script>
</body>
```

#### Пример 2: $plaintext = false
```
$src = "/assets/js/file.js"; 
$modx->regClientScript($src);
```

Будет:
```
...
<script type="text/javascript" src="/assets/js/file.js"></script>
</body>
```
