## Selector - custom TV для складання списку документів в Evolution CMS. ##
Selector є заміною для mm_ddSelectDocuments.

На відміну від mm_ddSelectDocuments:
- приживається з SimpleGallery;
- завдяки DocLister дозволяє вибирати дані для списку як завгодно і звідки завгодно;
- список результатів пошуку можна оформляти по-різному (реалізовано за допомогою prepare в DocLister);
- код повністю відкритий.

Для работи необхідний DocLister.

Після встановлення доповнення з магазину додатків необхідно у потрібного TV параметра обрати тип вводу "selector".
Компонент потребує деякого налаштування під себе.

Припустимо, є tv-параметр з назвою `related`, для зберігання списку схожих товарів. Щоб його поведінка відрізнялася від базового, потрібко створити в файлі `assets/tvs/selector/lib/related.controller.class.php` клас:

```
<?php namespace Selector;
include_once(MODX_BASE_PATH.'assets/tvs/selector/lib/controller.class.php');
class RelatedController extends SelectorController {
... //перевизначаємо що потрібно
}
```
У більшості випадків буде достатньо змінити властивість dlParams, в якому зберігаються параметри за замовчуваням для запуску DocLister:
```
<?php namespace Selector;
include_once(MODX_BASE_PATH.'assets/tvs/selector/lib/controller.class.php');
class RelatedController extends SelectorController {
    public function __construct($modx) {
        parent::__construct($modx);
        $this->dlParams['parents'] = 5;
        $this->dlParams['addWhereList'] = 'c.published = 1';
    }
}
```

Слід звернути увагу, що параметр – `related`, назва файлу – `related.controller.class.php`, а назва класу – `RelatedController` (з великої букви).

Можна довантажувати потрібний клас вручну за допомогою плагіна на OnManagerPageInit. В цьому випадку значення має тільки правильну назву класа. 
**Важливо:** є обмеження на назву tv-параметру: допускаються тільки латинські букви і символ підкреслювання.
