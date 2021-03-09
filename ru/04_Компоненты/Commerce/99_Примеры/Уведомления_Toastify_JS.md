# Пример вывода уведомлений Toastify JS при добавлении в корзину

```html
<link href="https://cdnjs.cloudflare.com/ajax/libs/toastify-js/1.9.3/toastify.min.css" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/toastify-js/1.9.3/toastify.min.js"></script>

<script>
    $(document).on('cart-add-complete.commerce', function (e, params) {
        if (params.response.status != 'success') {
            return;
        }

        var text, link;

        switch (params.data.instance) {
            case 'comparison':
                text = "Товар добавлен к сравнению";
                link = "/compare";
                break;
            case 'wishlist':
                text = "Товар добавлен в избранное";
                link = "/favorites";
                break;
            case 'products':
            default:    
                text = "Товар добавлен в корзину";
                link = "/cart";
                break;
        }

        Toastify({
            text: text,
            destination: link,
            close: true
        }).showToast();
    });
</script>
```
