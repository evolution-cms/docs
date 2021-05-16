JotX - покращений та доповнений Jot
-----------------------------------

### Конфігурація з файлу. 
Всі параметри і шаблони можна прописувати в одному файлі.

```php
    [!JotX? &config=`faq` !] - Запитання-відповідь
    [!JotX? &config=`tree` !] - деревовидні коментарі
    [!JotX? &config=`tree-ajax` !] - деревовидні коментарі з аякс
```

### Режими винесені в файли.

```php
    [!JotX? &action=`lastcomments` !] - Останні коментарі
```

### Нові параметри.

* **notifyEmails** -   підписка на певні адреси
* **subjectEmails** - заголовок листів для цієї розсилки
* **subscriber** - ім'я отримувача для цієї розсилки, якщо не вказано (за замовчуванням "підписник")
* **tplNotifyEmails** - шаблон для цієї розсилки

    ```php
    [!JotX? &notifyEmails=`user1@site.ua:Підписник 1,user2@site.ua:Підписник 2,user3@site.ua` !]

* **docids** - список docid, можна вказувати діапазони
* **tagids** - список tagid, через кому
* **userids** - список id користувачів, через кому. Для веб-користувачів - негативні.
* **limit** - обмеження кількості коментарів

    ```php
    [!JotX? &action=`lastcomments` &limit=`10` !] - 10 останніх коментарів зі всього сайту
    [!JotX? &docids=`*` &sortby=`rand()` &limit=`1` !] - випадковий коментар зі всього сайту
    [!JotX? &docids=`1,2,5-10,20*,30-35,40**,` !] - так теж можна :)

Параметри docids і tagids використовують для виводу даних, docid і tagid - для вводу поточних, тому вони розділені

* **depth** - глибина деревовидних коментарів (за замовчуванням 10)
* **upc** - як рахувати userpostcount (0 - не рахувати, 1(за замовчуванням) - рахувати для всього сайту , 2 - рахувати для поточної сторінки)

* **js і jsFile** - аналоги css і cssFile

Посторінкова навігація

* **tplNavPage** - шаблон для оформлення номеру сторінки
* **tplNavPageCur** - шаблон для оформлення номеру поточної сторінки
* **tplNavPageSpl** - розділювач номерів сторінок
* **tplNavPageDots** - розрив пагінації (за замовчуванням три крапки)
* **pageAdjacents** - кількість сторінок до і після поточної (за замовчуванням 2)

### Події. 
В кожному з двох класів свої.

onBeforeConfiguration,onBeforeRunActions,onRunActions,onConfiguration,onBeforeFirstRun,
onFirstRun,onSubscriptionCheck,onDeleteComment,onGetCommentFields,onBeforeSaveComment,
onSaveComment,onGetSubscriptions,onBeforeGetSubscriptions,onBeforeGetUserInfo,
onBeforeNotify,onBeforeSubscribe,onBeforeUnsubscribe,onBeforeValidateFormField,
onValidateFormFieldFail,onBeforePOSTProcess,onProcessForm,onBeforeProcessPassiveActions,
onProcessPassiveActions,onBeforeGetCommentCount,onBeforeGetComments,onGetComments,
onReturnOutput,onSetDefaultOutput,onBeforeGetUserPostCount,onSetFormOutput,onSetCommentsOutput

### Плагіни на події.
Їх можна довантажувати як з сніпетів, так і з файлів. Можна прописувати через кому.

```php
    [!JotX? &onBeforeValidateFormField=`nolink,onlyrus` !]
```

До складу входять плагіни:

* **subscribe** (події: onBeforeFirstRun,onSaveComment,onBeforeRunActions,onBeforeProcessPassiveActions,onGetSubscriptions,onBeforeGetUserInfo,onBeforeNotify) - 
підписка гостей сайту на сповіщення про нові коментарі. Також необхідно 2 виправлення в шаблонах: чекбокс і текст про відписку, див. приклад в tree.config.php
* **ajax** (події: onSetCommentsOutput,onSetFormOutput,onReturnOutput) - завантаження всього через аякс
* **antispam** (події: onBeforePOSTProcess,onSetFormOutput) - боротьба з ботами шляхом додавання прихованого поля-пастки
* **nolink** (події: onBeforeValidateFormField) - заборонити посилання в коментарях
* **onlyrus** (події: onBeforeValidateFormField) - заборонити неросійський спам
* **notifyfaq** (події: onProcessForm,onBeforeNotify) - повідомлення користувачу про відповідь на питання в FAQ
* **rss** (події: onBeforeProcessPassiveActions,onSetCommentsOutput) - додає посилання на RSS-стрічку
* **rating** (події: onFirstRun,onReturnOutput) - додає голосування за коментар

Будуть і інші.

### Інші виправлення.

* Система повідомлень об'єднана і перероблена під PHPMailer
* Оптимізовано запити в базу, в тому числі і для userpostcount. Поля користувачів об'єднані з полями коментарів.
* Виправлені старі баги з видаленням / додаванням полів
* Посторінкова пагінація, в деревовидних коментарів вона теж працює, якщо включити
* Всякі дрібниці, типу граваторів

### Корисні посилання
[основний репозиторій](https://github.com/Temus/JotX)
[обговорення JotX в спільноті](http://community.modx-cms.ru/blog/addons/8080.html)
[сторінка в репозиторії](http://extras.evolution-cms.com/packages/users/jotx.html)
