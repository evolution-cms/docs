## Callback-функції JS при роботі`eFilter`

Функції знаходяться в глобальному полі зору.
Наприклад, висновок повідомлення про завершення роботи фільтра може в шаблоні сайту виглядати так:
```
<script>
function afterFilterComplete() {
  console.log('Results filtered')
}
</script>
```

### afterFilterSend(msg)
...

### afterFilterComplete(_form)

Спрацьовує по завершенню роботи eFilter і оновленню результатів. 
Можна використовувати цю подію для стилізації елементів форми або результатів.

### beforeFilterSend(_form)
...

## Важливо! для работи `ajax`
Для роботи ajax форма і блок товарів не повинні бути в самому корені документа, тобто безпосередньо в <body>.

Не можна:`<body>[!eFilter!][+eFilter_form+][!eFilteResult!]</body>`

Можна: `<body><main>[!eFilter!][+eFilter_form+][!eFilteResult!]</main></body>`
