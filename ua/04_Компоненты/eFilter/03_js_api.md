## Calback-функции JS при работе `eFilter`

Функции находятся в глобальной области видимости.
Например, вывод сообщения о завершении работы фильтра может в шаблоне сайта выглядеть так:
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

Срабатыает по завершению работы `eFilter` и обновлению результатов.
Можно использовать данное событие для стилизации элементов формы или результатов.

### beforeFilterSend(_form)
...

## Важно! для работы `ajax`
Для работы `ajax` форма и блок товаров не должны быть в самом корне документа, то есть непосредственно в `<body>`.

Нельзя:`<body>[!eFilter!][+eFilter_form+][!eFilteResult!]</body>`

Можно: `<body><main>[!eFilter!][+eFilter_form+][!eFilteResult!]</main></body>`
