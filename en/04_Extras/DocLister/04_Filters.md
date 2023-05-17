##Filters

В комплекте следующие фильтры:

* content - для фильтрации по полям таблицы site_content, можно заменить параметром addWhereList;
* tv - для фильтрации по TV-параметрам;
* tvd - для фильтрации по TV-параметрам с учетом значений по умолчанию;
* private - для фильтрации документов с учетом прав доступа.

##Построение фильтра
####Пример
```
OR(AND(filter:field:operator:value;filter2:field:operator:value);(...))
```

##Операторы
###=, eq, is

Равно.

###!=, no, isnot

Не равно.

###>, gt

Больше.

###<, lt

Меньше.

###<=, elt

Меньше или равно.

###>=, egt
Больше или равно.

###%, like
Содержит строку.

###like-r
Начинается строкой.

###like-l
Заканчивается строкой.

###regexp
Выборка с использованием регулярных выражений [REGEXP](https://dev.mysql.com/doc/refman/5.5/en/regexp.html).

###against
Полнотекстовый поиск.
####Пример
```
[[DocLister? &filters=`AND(content:pagetitle,description,content,introtext:against:искомая строка)`]]
```
Из данного примера предполагается, что в базе данных имеется FULLTEXT индекс по полям pagetitle,description,content,introtext

###containsOne
Поиск любого слова или его части в тексте при помощи LIKE.
####Пример:
```
[[DocLister? &filters=`AND(content:content:containsOne:когда,наступит,мир)`]]
```
Будет построен SQL запрос вида
```
(content LIKE '%когда%' OR content LIKE '%наступит%' OR content LIKE '%мир%')
```
Т.е. в конечном счете из базы будут выбраны документы в тексте которых используется слова "когда" или "наступит" или "мир".
Из примера вызова видно, что слова разделены запятой. Это поведение можно переопределить параметром ___filter_delimiter___.


###containsAll
Поиск всех слов в тексте при помощи LIKE.
####Пример:
```
[[DocLister? &filters=`AND(content:content:containsAll:все,эти,слова,должны,присутствовать)`]]
```
Будет построен SQL запрос вида
```
(content LIKE '%все%' AND content LIKE '%эти%' AND content LIKE '%слова%' AND content LIKE '%должны%' AND content LIKE '%присутствовать%')
```

###in
Входит в множество.

###notin
Не входит в множество.

####Пример вызова с фильтрацией по цене от 0 до 300:

```
[[DocLister? &filters=`AND(tv:price:gt:0;tv:price:lt:300)`]]
```

А теперь тоже самое, только с учетом значений по умолчанию

```
[[DocLister? &filters=`AND(tvd:price:gt:0;tvd:price:lt:300)`]]
```
