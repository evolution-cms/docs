###Повертає інформацію про всі дочірні документи, которі є опублікованими та не видаленими

*Примітка: getActiveChildren() повертає інформацію про дочірні документи тідьки першого рівня.*

array getActiveChildren (mixed $id[, string $sort[, string $dir[, string $fields]]]);

**$id** - ідентифікатор батьківського документу

**$sort** - поле, по якому буде здійснюватись сортування
- за замовчуванням: menuindex

**$dir** - варіант сортування:
- ASC - за зростанням, DESC - за спаданням
- за замовчуванням: ASC

**$fields** - список необхідних полів
за замовчуванням: id, pagetitle, description, parent, alias, menutitle

***

####Формат даних результату:
````php
Array (
    [0] => Array (
        [id] => 50
        [pagetitle] => Документ 1
        [description] =>
        [parent] => 16
        [alias] =>
        [menutitle] =>
    )
    [1] => Array (
        [id] => 48
        [pagetitle] => Документ 2
        [description] =>
        [parent] => 16
        [alias] =>
        [menutitle] =>
    )
)
````

***

####Приклад

````php
/**Структура документів:

-Статті (1)
--Нерухомість (11)
---Економ(111)
---Елітна(112)
--Авто (12)

**/

$modx->getActiveChildren(1); //поверне информацію про документи 11 и 12

````

*Дивіться також: getAllChildren*