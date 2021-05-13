## Опис ## 

Сніппет вивовить кошик замовлень двух типіп (розширений и простий). 

Сніппет можна викликати на сторінці декілька разів, але кошик виводиться тільки в місці першого виклика. Другий и наступні виклики игноруються. 

**Приклад:**
*Якщо кошик на сторінках каталогу товарів знаходиться в правій колонці шаблона, а на сторінці оформлення заказу виклик сніппета вставлений в контент сторінки, то на цій сторінці кошик буде виведений тільки в центральній колонці (в правій виклик сніппета можна не прибирати).*

## Параметри сніппета ##
<table border="1" cellpadding="5">
<tbody><tr>
  <th>Параметр</th>
  <th>Опис і значення</th>
  <th>Значення за замовчуванням</th>
  <th>Примітка</th>
</tr>
<tr>
  <td><b>&lang</b></td>
  <td>мова</td>
  <td>Мова системи керування</td>
  <td>В данний час доступні мови:<br> `russian`, `english`, `german`, `francais`</td>
</tr>
<tr>
  <td><b>&style</b></td>
  <td>стиль кошика</td>
  <td>default<br> (assets/snippets/shopkeeper/style/default/)</td>
  <td><b>&style=`0`</b> - якщо не потрібен окремий стильовий файл для кошика</td>
</tr>
<tr>
  <td><b>&cartType</b></td>
  <td>
    тип кошика<br>
    <b>full</b> - розширений,<br>
    <b>small</b> - простий,<br>
    <b>empty</b> - тільки очистка кошика без виведення на сторінці
  </td>
  <td>full</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&currency</b></td>
  <td>валюта</td>
  <td>руб.</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&priceTV</b></td>
  <td>ім'я TV-параметру, який використовується для ціни.</td>
  <td>price</td>
  <td>Якщо ваш TV для ціни має назву не "price", <b>обов'язково</b> вкажіть це ім'я в даному параметрі.</td>
</tr>
<tr>
  <td><b>&orderFormPage</b></td>
  <td>ID сторінки з формою замовлення</td>
  <td>1</td>
  <td>обов'язковий параметр</td>
</tr>
<tr>
  <td><b>&noJQuery=`1`</b></td>
  <td>якщо на сайті вже використовується бібліотека JQuery</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&noConflict=`1`</b></td>
  <td>если на сайті використовується інша JS-бібліотека (не JQuery), наприклад Mootools, Prototype.</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&noCounter</b></td>
  <td>приховувати (значення `1`) або ні (значення `0`) лічильник товарів при додаванні в кошик</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&linkAllow=`0`</b></td>
  <td>Виводить назви товарів в кошику без силок.</td>
  <td>1</td>
  <td>Якщо цей параметр вказаний (=`0`) на сторінці оформлення заказу, лист з складом замовлення і список товарів в модулі будуть без силок.</td>
</tr>
<tr>
  <td><b>&stuffCont</b></td>
  <td>CSS-селектор елемента, всередині якого знаходиться інформація про товар.</td>
  <td>div.shk-item</td>
  <td>Приклад чанка: chunk_shopStuff.tpl</td>
</tr>
<tr>
  <td><b>&debug=`1`</b></td>
  <td>запустити отладку JavaScript-функцій (виведення інформації)</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&tplPath</b></td>
  <td>путь до папки с чанками</td>
  <td>`assets/snippets/shopkeeper/chunks/ru/`</td>
  <td></td>
</tr>
<tr>
  <td><b>&cartTpl</b></td>
  <td>чанк с шаблоном корзины</td>
  <td>@FILE:chunk_shopCart.tpl</td>
  <td>Чанк содержит сразу 3 шаблона - для пустой, заполненной расширенной и простой корзины.<br> Если чанки хранятся в файлах, можно указать путь с командой "@FILE:". Если чанки созданы в системе управления, то указывается только имя чанка (например &cartTpl=`shopCart`)</td>
</tr>
<tr>
  <td><b>&cartRowTpl</b></td>
  <td>чанк шаблона строки с информацией товара в расширенной корзине</td>
  <td>@FILE:chunk_shopCartRow.tpl</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&cartHelperTpl</b></td>
  <td>чанк шаблона "хелпера" - блока, который появляется для подтверждения действий</td>
  <td>-</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&additDataTpl</b></td>
  <td>чанк для доп. параметров товаров в корзине ([+addit_data+])</td>
  <td>-</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&orderDataTpl</b></td>
  <td>чанк списка товаров в отчете о заказе ([+orderData+])</td>
  <td>-</td>
  <td>Используется в письме с отчетом о заказе (eForm &report) и в модуле.</td>
</tr>
<tr>
  <td><b>&flyToCart</b></td>
  <td>действие при добавлении товара в корзину.<br>
     <b>helper</b> - появляется блок со счетчиком кол-ва товаров и летит в корзину,<br>
     <b>image</b> - в корзину летит картинка товара<br>
     <b>nofly</b> - в корзину ничего не летит;
  </td>
  <td>`helper`</td>
  <td>При &flyToCart=`image` тег &lt;img&gt; должен иметь CSS-класс <b>"shk-image"</b></td>
</tr>
<tr>
  <td><b>&noLoader=`1`</b></td>
  <td>не паказывать прелоадер (анимационная картинка)</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&excepDigitGroup=`1`</b></td>
  <td>разделять числа цен в корзине на разряды</td>
  <td>1</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&changePrice=`1`</b></td>
  <td>при изменении параметров с ценой - изменяется цена товара, а индекс с плюсом не появляется</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&counterField=`1`</b></td>
  <td>добавить ко всем полям &lt;input name="shk-count"&gt; (кол-во товара) стрелки больше/меньше</td>
  <td>0</td>
  <td>&nbsp;</td>
</tr>
<tr>
  <td><b>&noJavaScript=`1`</b></td>
  <td>Работа без JavaScript.</td>
  <td>0</td>
  <td>Обратите внимание, что в чанке "shopCart" кнопка "Пересчитать" находится внутри тега "noscript". Если используется режим <b>&noJavaScript=`1`</b>, рекомендуется тег "noscript" удалить.</td>
</tr>
<tr>
  <td><b>&hideOn</b></td>
  <td>Отключить корзину на странице</td>
  <td>0</td>
  <td>Обычно используется в вызове сниппета краткого вида корзины. Указывается ID страницы с подробным видом корзины (оформление заказа). На этой странице краткий вид корзины будет отключен.</td>
</tr>
</tbody></table>

## Примеры ##

Простой вызов: 
```
[!Shopkeeper? &priceTV=`price` &orderFormPage=`10`!]
```

Расширенный вызов:
```
[!Shopkeeper? 
&cartType=`small`
&priceTV=`price`
&orderFormPage=`10`
&changePrice=`1` 
&counterField=`1` 
&flyToCart=`nofly`
!]
```


## Шаблоны (чанки) и плейсхолдеры ##

<table border="1" cellpadding="5">
<tbody><tr>
  <th>Параметр сниппета</th>
  <th>Описание</th>
  <th>Плейсхолдеры в шаблоне</th>
  <th>Примечание</th>
</tr>
<tr>
  <td><b>&cartTpl (&cartType=`full`)</b></td>
  <td>шаблон расширенной корзины</td>
  <td>
  <b>[+inner+]</b> - строка с информацией о товаре (cartRowTpl);<br>
  <b>[+price_total+]</b> - Общая сумма;<br>
  <b>[+this_page_url+]</b> - URL текущей страницы;<br>
  <b>[+empty_url+]</b> - URL для очистки корзины;<br>
  <b>[+order_page_url+]</b> - URL страницы оформления заказа;<br>
  <b>[+currency+]</b> - валюта;
  </td>
  <td rowspan="2">
    Пример: <b>chunk_shopCart.tpl</b>
    <br>(содержит 3 шаблона корзины)<br><br>
    &lt;!--tpl_separator--&gt; - разделитель шаблонов (удалять нельзя)
  </td>
</tr>
<tr>
  <td><b>&cartTpl (&cartType=`small`)</b></td>
  <td>шаблон упрощенной корзины</td>
  <td>
  <b>[+price_total+]</b> - Общая сумма;<br>
  <b>[+total_items+]</b> - Число выбранных товаров;<br>
  <b>[+plural+]</b> - слово "товар" во множественном числе в зависимости от числа выбранных товаров;<br>
  <b>[+this_page_url+]</b> - URL текущей страницы;<br>
  <b>[+empty_url+]</b> - URL для очистки корзины;<br>
  <b>[+order_page_url+]</b> - URL страницы оформления заказа;<br>
  <b>[+currency+]</b> - валюта
  </td>
</tr>
<tr>
  <td><b>&cartRowTpl</b></td>
  <td>шаблон строки с информацией товара в расширенной корзине</td>
  <td>
  <b>[+id+]</b> - ID товара (документа);<br>
  <b>[+name+]</b> - название товара;<br>
  <b>[+link+]</b> - ссылка на страницу товара;<br>
  <b>[+addit_data+]</b> - строка с информацией о доп. параметрах товара;<br>
  <b>[+price+]</b> - цена;<br>
  <b>[+price_total+]</b> - цена товара + доп. параметры;<br>
  <b>[+price_count+]</b> - цена товара * кол-во;<br>
  <b>[+currency+]</b> - валюта;<br>
  <b>[+count+]</b> - количество;<br>
  <b>[+this_page_url+]</b> - URL текущей страницы;<br>
  <b>[+index+]</b> - номер товара в корзине (от нуля);<br>
  <b>[+любой TV+]</b> - любой TV-параметр, например [+image+];<br>
  <b>[+shk_любой TV+]</b> - любой доп. параметр, выбранный при добавлении товара в корзину (из [+addit_data+]), например [+shk_param1+].
  </td>
  <td>Пример: <b>chunk_shopCartRow.tpl</b> и <b>chunk_shopCartRow2.tpl</b></td>
</tr>
<tr>
  <td><b>&additDataTpl</b></td>
  <td>шаблон для доп. параметров товаров в корзине ([+addit_data+])</td>
  <td>
    <b>[+param+]</b> - имя и цена параметра. Цена указывается в скобках. Если цена = 0, то пишется только название параметра (без скобок);<br>
    <b>[+name+]</b> - имя параметра;<br>
    <b>[+price+]</b> - цена параметра;
  </td>
  <td>Пример: <b>chunk_additDataTpl.tpl</b></td>
</tr>
<tr>
  <td><b>&orderDataTpl</b></td>
  <td>шаблон списка товаров в отчете о заказе ([+orderData+])</td>
  <td>
    <b>Все плейсхолдеры чанка &cartRowTpl</b><br><br>
    <b>[+loop+]</b>, <b>[+end_loop+]</b> - начало и конец строки данных товаров (цикл).
  </td>
  <td>Пример: <b>chunk_orderDataTpl.tpl</b></td>
</tr>
<tr>
  <td><b>&report</b> (eForm)</td>
  <td>шаблон текста письма с составом заказа</td>
  <td>
  <b>[+orderData+]</b> - состав заказа (список покупок);<br>
  <b>[+orderID+]</b> - номер заказа;
  </td>
  <td>Пример: <b>chunk_shopOrderReport.tpl</b> и <b>chunk_shopOrderReportWebUser.tpl</b></td>
</tr>
<tr>
  <td>Страница, на которой вызывается сниппет Shopkeeper</td>
  <td></td>
  <td>
  <b>[+totalItems+]</b> - кол-во товара в корзине;<br>
  <b>[+totalPrice+]</b> - общая цена товара в корзине;
  </td>
  <td></td>
</tr>
</tbody></table>



## Необходимые CSS-классы, Id и имена полей ## 
Для полноценной работы Shopkeeper необходимы следующие css-классы, id и имена полей:

<table border="1" cellpadding="5">
<tbody><tr>
  <th>Шаблон</th>
  <th>CSS-классы</th>
  <th>id HTML-элементов</th>
  <th>Имена полей и кнопок</th>
  <th>Примечание</th>
</tr>
<tr>
  <td>Шаблон вывода информации товара</td>
  <td>
    <b>shk-item</b> - класс "обертывающего" элемента блока с информацией о товаре;<br>
    <b>shk-image</b> - картинка товара (если используется &flyToCart=`image`);<br>
    <b>shk-price</b> -класс элемента с ценой товара.<br>
  </td>
  <td>—</td>
  <td>
    <b>shk-id</b> - имя скрытого поля с id товара;<br>
    <b>shk-count</b> - имя скрытого поля с кол-вом товара.
  </td>
  <td>Пример <b>chunk_shopStuff.tpl</b></td>
</tr>
<tr>
  <td>Шаблон корзины</td>
  <td>
    —
  </td>
  <td>
    <b>shopCart</b> - id "обертывающего" элемента блока корзины;<br>
    <b>butEmptyCart</b> - id кнопки-ссылки очистки корзины;<br>
    <b>butOrder</b> - id ссылки на страницу оформление товара.
  </td>
  <td>
    <b>shk_recount</b> - кнопка "Пересчитать".<br>
    
  </td>
  <td>Пример <b>chunk_shopCart.tpl</b></td>
</tr>
<tr>
  <td>Шаблон строки информации о товаре в корзине</td>
  <td>
    <b>shk-del</b> - кнопка-ссылка удаления товара.<br>
    
  </td>
  <td>
    —
  </td>
  <td>
    <b>count[]</b> - name полей с кол-вом товара.<br>
  </td>
  <td>Пример <b>chunk_shopCartRow.tpl</b></td>
</tr>
<tr>
  <td>Шаблон формы заказа</td>
  <td>
    —
  </td>
  <td>
    —
  </td>
  <td>
    <b>email</b> - поле "E-mail";<br>
    <b>phone</b> - поле "Телефон"
  </td>
  <td>Пример <b>chunk_shopOrderForm.tpl</b> и <b>chunk_shopOrderFormWebUser.tpl</b></td>
</tr>
</tbody></table>

CSS-классы (и id) используются в JS-функциях Shopkeeper'а.


## Советы ##
### Две и более цены для одного товара ##
Для этого нужно создать две или более формы (form) и в поле name="shk-id" после ID написать имя TV с ценой.

**Пример:**
```
<input type="hidden" name="shk-id" value="[+id+]__price2">
```

При submit формы в корзину добавится цена из TV-параметра с именем "price2".

### Добавление в корзину данных, не создавая TV-параметры ###

**Пример:**
```
<input type="text" name="test__[*id*]__add" value="дополнительные данные" />
```
В корзину добавится параметр, который можно выводить в месте вставки плейсхолдера `[+test+]` (выведется "дополнительные данные").


## События для плагинов ##

* OnSHKFrontendInit - инициализация сниппета Shopkeeper во внешней части.
* OnSHKChangeStatus - изменение статуса заказа.
* OnSHKOrderDescRender - вывод подробной информации о заказе в модуле.
* OnSHKMailApprovedForPayment - отправление письма при статусе "Принят к оплате". Плагин может добавлять в письмо доп. информацию `([+plugin+])`.
* OnSHKcartLoad - загрузка корзины (вывод информации в чанке `&cartTpl - [+plugin+]`).
* OnSHKstatusSendMail - отправка письма о смене статуса.
* OnSHKmodRenderTopLinks - вывод ссылок вверху в модуле Shopkeeper.
* OnSHKmodPagePrint - вывод страницы модуля. Можно использовать для создания своей страницы (см. пример OnSHKmodPagePrint_plugin_example.txt).
* OnSHKbeforeSendOrder - перед отправкой заказа. Можно использовать для изменения полей ($fields).
* OnSHKsaveOrder - сохранение заказа.
* OnSHKcalcTotalPrice - расчет общей стоимости.

В папке shopkeeper/docs/ есть примеры плагинов.


## "Сallback-функции" на JavaScript ## 
* setCartActionsCallback - перезагрузка корзины,
* fillCartCallback - добавление товара в корзину,
* emptyCartCallback - очищение корзины.

Просто создайте функции с такими именами и они будут вызываться при соответствующих действиях.


## Примеры чанков в папке install/examples/ ##

* chunk_shopCart.tpl - чанк корзины. Может быть использован как значение параметра &cartTpl при вызове Shopkeeper. Чанк содержит сразу 3 шаблона - для пустой, заполненной расширенной и заполненной простой корзины.
* chunk_shopCartRow.tpl - чанк шаблона строки с информацией товара в расширенной корзине.
* chunk_shopCartRow2.tpl - пример с картинкой (TV - image) и условием PHx.
* chunk_shopStuff.tpl - чанк краткой информации о товаре. Может быть использован как значение параметра &tpl при вызове Ditto.
* chunk_shopStuff_2.tpl - пример с двумя ценами для одного товара (продажа и прокат).
* chunk_shopToCart.tpl - может быть использован в шаблоне страницы подробного описания товара или можно вставлять вызов чанка `{{shopToCart}}` в визуальный редактор.
* chunk_shopCartHelper.tpl - чанк шаблона "хелпера" - блока, который появляется для подтверждения действий.
* chunk_additDataTpl.tpl - шаблон для доп. параметров товаров в корзине.
* chunk_shopOrderForm.tpl - чанк форма оформление заказа. Может быть использован как значение параметра &tpl при вызове eForm.
* chunk_shopOrderFormWebUser.tpl - чанк форма оформление заказа для зарегистрированных пользователей.
* chunk_shopOrderReport.tpl - чанк письма с информацией о заказе. Может быть использован как значение параметра &report при вызове eForm.
* chunk_shopOrderReportWebUser.tpl - чанк письма с информацией о заказе для зарегистрированных пользователей.
* chunk_FormSignup.tpl - пример чанка с шаблоном формы регистрации для сниппета WebSignup.
* chunk_weblogin.tpl - пример чанка с шаблоном формы авторизации сниппета WebLogin.
* chunk_orderDataTpl.tpl - шаблон списка товаров в отчете о заказе `([+orderData+])`
