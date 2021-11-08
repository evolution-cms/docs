# regClientScript
### Підключення JavaScript до документу

string regClientScript(string $src[, bool $plaintext]);

**$src** - шлях до файлу JavaScript або код JavaScript.

**$plaintext** - потрібно розмістити у наступному вигляді:
+ true: в $src переданий інлайн-код між `<script>`, його треба вставити перед `</body>`
+ false: в $src передане посилання на файл

За замовчуванням: **false**.

#### Приклад 1: $plaintext = true
```
$src = "<script type='text/javascript'> runSlideShow('slides'); </script>"; 
$modx->regClientScript($src, true);
```

Отримаємо:
```
...
<script type='text/javascript'> runSlideShow('slides'); </script>
</body>
```

#### Приклад 2: $plaintext = false
```
$src = "/assets/js/file.js"; 
$modx->regClientScript($src);
```

Отримаємо:
```
...
<script type="text/javascript" src="/assets/js/file.js"></script>
</body>
```
