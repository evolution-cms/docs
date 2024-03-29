Синтаксис:
```
@SELECT sql_query
```
Зв'язує ТВ з запитом до бази даних. Повертає набір записів.

Приклад:
```
@SELECT id,pagetitle FROM [+PREFIX+]site_content LIMIT 10
```

В результаті ви отримаєте список з 10 перших документів вашого сайту.

*Не забудьте додати префікс до імені таблиці. Наприклад, `evo_site_content`, де `evo_` - префікс таблиці.*

Також ви можете використовувати конструкцію `[+PREFIX+]`, щоб автоматично підставляти префікс до вашого запиту.


## Приклад: ##
Ви можете використовувати команду `@SELECT` і тип відображення ТВ `DropDownListMenu`, щоб надати редакторам сайту динамічний список параметрів з будь-якої таблиці (або з дерева документів).
```
@SELECT pagetitle,id FROM [+PREFIX+]site_content WHERE parent= 3 LIMIT 10 
```
Запит виведе випадаючий список із заголовків всіх документів, батьківським яких є документ з id=3. При виборі значення ТВ-параметр, id буде збережений обраного пункту.

Це можна використовувати, наприклад, для створення блоку "Схожі товари".
