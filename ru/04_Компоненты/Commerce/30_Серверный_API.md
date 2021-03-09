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

#### add
```php
$cart->add(array $item, $isMultiple = false);
```

#### addMultiple
```php
$cart->addMultiple(array $items = []);
```

#### update
```php
$cart->update($row, array $attributes = [], $isAdded = false);
```

#### remove
```php
$cart->remove($row);
```

#### removeById
```php
$cart->removeById($id);
```

#### clean
```php
$cart->clean();
```

#### setTitleField
```php
$cart->setTitleField($field);
```

#### setPriceField
```php
$cart->setPriceField($field);
```

#### getSubtotals
```php
$cart->getSubtotals(array &$rows, &$total);
```

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
