# Серверный API

### Корзины и списки товаров

Получить корзину товаров в своем коде довольно просто:
```php
// получить объект корзины:
$cart = $modx->commerce->getCart();
// или так:
$cart = ci()->carts->getCart('products');

// получить товары из корзины:
$items = $cart->getItems();
```

При создании корзины можно передать ее название вторым аргументом, и зарегистрированное хранилище - третьим:
```php
new Commerce\Carts\ProductsCart($modx, $instance = 'products', $store = 'session');
```

Commerce по-умолчанию использует корзину товаров и списки сравнения и избранного. Любой из них может быть заменен в момент инициализации, например:
```php
if ($modx->event->name == 'OnInitializeCommerce') {
    $cart = new Commerce\Carts\ProductsCart($modx);
    ci()->carts->addCart('products', $cart);
}
```

По умолчанию товары в корзине хранятся в сессии пользователя, списки сравнения и избранного - в cookies (только идентификаторы товаров). Способ хранения также может быть изменен при инициализации:
```php
if ($modx->event->name == 'OnInitializeCommerce') {
    class DatabaseCartStore extends Commerce\Carts\SessionCartStore {
        // ...
    }

    ci()->carts->registerStore('database', DatabaseCartStore::class);
    
    $cart = new Commerce\Carts\ProductsCart($modx, 'products', 'database');
    ci()->carts->addCart('products', $cart);
}
```

#### add - добавление товара в корзину
```php
$cart->add(array $item, $isMultiple = false);
```
В массиве `$item` передается информация о товаре, должны быть как минимум `id` и `count`. Параметр `isMultiple` означает множественное добавление, если равен `true`, в случае успеха не вызывается событие `OnCartChanged`.

#### addMultiple - пакетное добавление товаров в корзину
```php
$cart->addMultiple(array $items = []);
```

#### update - изменение товара в корзине
```php
$cart->update($row, array $attributes = [], $isAdded = false);
```
В параметре `$row` передается символьный идентификатор строки в корзине, в `$attributes` - поля, которые нужно изменить. `$isAdded` означает, было ли действие изначально <i>добавлением</i> товара или нет.

#### remove - удаление товара из корзины
```php
$cart->remove($row);
```
Удаляет товар из корзины по символьному идентификатору строки.

#### removeById - удаление товаров по идентификатору товара
```php
$cart->removeById($id);
```
Удаляет товары из корзины по уникальному идентификатору товара/ресурса в дереве.

#### clean - очистка корзины
```php
$cart->clean();
```

#### setTitleField - задание имени поля для использования в качестве названия товаров
```php
$cart->setTitleField($field);
```

#### setPriceField - задание имени поля для использования в качестве цены товаров
```php
$cart->setPriceField($field);
```

#### getSubtotals - расчет подитогов и итоговой стоимости товаров в корзине
```php
$cart->getSubtotals(array &$rows, &$total);
```
Вызывается событие `OnCollectSubtotals`, подитоги записываются в `$rows`, итоговая сумма - в `$total`.

### Обработчик заказа OrderProcessor

Для получения обработчика заказа в своем коде нужно вызвать специальный метод Commerce:
```php
$processor = $modx->commerce->loadProcessor();
```

#### createOrder
```php
$order = $processor->createOrder(array $items, array $fields);
```

#### addOrderHistory
```php
$processor->addOrderHistory($order_id, &$status_id, &$comment = '', &$notify = false);
```
#### changeStatus
```php
$processor->changeStatus($order_id, $status_id, $comment = '', $notify = false, $template = null);
```
#### updateOrder
```php
$processor->updateOrder($order_id, $data = []);
```
#### deleteOrder
```php
$processor->deleteOrder($order_id);
```
#### getOrder
```php
$processor->getOrder();
```
#### loadOrder
```php
$processor->loadOrder($order_id, $force = false);
```
#### loadOrderByHash
```php
$processor->loadOrderByHash($order_hash);
```
#### payOrderByHash
```php
$processor->payOrderByHash($hash);
```
#### loadPayment
```php
$processor->loadPayment($payment_id);
```
#### loadPaymentByHash
```php
$processor->loadPaymentByHash($hash);
```
#### createPayment
```php
$processor->createPayment($order_id, $amount);
```
#### savePayment
```php
$processor->savePayment($payment);
```
#### getOrderPaymentsAmount
```php
$processor->getOrderPaymentsAmount($order_id);
```
#### isOrderStarted
```php
$processor->isOrderStarted();
```
#### updateRawData
```php
$processor->updateRawData($data);
```
#### getCurrentDelivery
```php
$processor->getCurrentDelivery();
```
#### getCurrentPayment
```php
$processor->getCurrentPayment();
```
