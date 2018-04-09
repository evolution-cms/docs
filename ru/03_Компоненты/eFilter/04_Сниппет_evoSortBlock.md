Сниппет для вывода блока с настройков сортировки и выбора количества товаров на странице.

## evoSortBlock
Сниппет для формирования блока сортировки. Из приятных вещей.



## Параметры
1. displayConfig  настройка селекта или ссылок для указания количества товаров на странице.
Пример: 20||30||40||все==all.
2. sortConfig  настройка  ссылок для указания поля по которому товары сортируються.
Пример: По название==pagetitle||По индексу==menuindex||Цена от маленькой==price:asc||Цена от большой==price:desc
3. ajax - использовать ли ajax по умолчанию ноль.
4. changeSortByClickField - изменять направление сортировки при повторном клике по параметру сортировки. 1/0. По умолчанию 0.
Параметр необходим если у нас нет блока для выбора направление, а надо изменять направление при клике второй раз по параметру поля.

### Шаблоны
#### Обертка
1. ownerTpl - Основная обертка блока.
    Плейсхолдеры ```[+class+] [+display.block+] [+sort.block+] [+sort.direction+]```.
    Пример: ```<div class="[+class+]">[+display.block+][+sort.block+]</div>```

    * class Плейсхолдер из класcами для обертки которые необходимы для работы js, а именно sort-wrap и ajax
    * display.block блок выбора количества товаров
    * sort.block Блок выбора поля для сортировки
    * sort.direction Блок выбора направления сортировки
#### Выбор количества товаров
1. displayOwnerTpl - обертка блока для выбора количества елементов на странице.
    Плейсхолдеры: ```[+class+]">[+wrapper+]```
    Пример: ```<select class="[+class+]">[+wrapper+]</select>```
    Пример: ```<div class="[+class+]">[+wrapper+]</div>```

2. displayRowTpl - Шаблон вывода строки. ( option для селекта или тег a для блока).
    Плейсхолдеры: ```[+value+],[+selected+],[+data+],[+class+],[+caption+] ```
    Пример: ``` <option value="[+value+]" [+selected+] >[+caption+]</option>```
    Пример: ``` <a [+data+] class="[+class+]">[+caption+]</a> ```
#### Выбор поля для сортировки
1. sortOwnerTpl  - обертка блока для выбора поля по которому элементы сортируются на странице.
    Плейсхолдеры: ```[+wrapper+]```
    Пример: ```<ul>[+wrapper+]</ul>```

2. sortRowTpl - Шаблон вывода ссылки для выбора поля.
        Плейсхолдеры: ```[+class+],[+data+] [+caption+]```
        Пример: ```<a class="[+class+]" [+data+]>[+caption+]</a>```

#### Выбор направления сортировки
1. sortDirectionTpl - обертка блока выбора направления.
    Плейсхолдеры: ```[+up+][+down+]```
    up - сортировка asc
    down - сортировка desc
2. sortDirectionUpTpl - шаблон ссылки для выбора направления сортировки asc
    Плейсхолдеры: ```[+class+][+data+]```
    class - css клас
    data - Дата атрибут data-value в котором хранится текущее поле а направление сортировки asc. Пример price:asc
3. sortDirectionDescTpl - шаблон ссылки для выбора направления сортировки desc
    Плейсхолдеры: ```[+class+][+data+]```
    class - css клас
    data - Дата атрибут data-value в котором хранится текущее поле а направление сортировки asc. Пример price:desc


##### Классы
1. displayActiveClass - Класс для активного пунка в выборе количества элементов на странице. По умолчанию active.
2. sortActiveClass - Класс для активного пункта в выборе поля для сортировки элементов на странице.
3. sortUpClass - Класс для ссылки выбора поля когда сортировка от маленького к большому. По умолчанию up
4. sortDownClass - Класс для ссылки выбора поля  когда сортировка от большого к маленькому. По умолчанию down
5. sortFieldClass - Класс для ссылок выбора поля и направления сортировки. По умолчанию set-sort-field.
6. sortDirectionActiveClass - Класс для активной ссылки выбранного направления сортировки. По умолчанию active.


##### Значения по умолчаеию
1. displayDefault - количество элементов на странице по умолчанию
2. sortFieldDefault - поле сортировки по умолчанию
3. sortOrderDefault - направление сортировки по умолчанию


## Устанавливаемые плейсхолдеры для работы без eFilterResult
 * sort_display - количество товаров
 * sort_field - поле для сортировки
 * sort_order - направление сортировки
Также если использовать снипет без eFilter необходимо подключить js файл eFilter.js вручную.
А товары обернуть в обертку eFilterResult
```
    <div id="eFiltr_results_wrapper">
        <div class="eFiltr_loader"></div>
        <div id="eFiltr_results">
        </div>
    </div>
    ```


## Логика работы js.
### Для выбора количества товаров.
Обрабатывается клик по елементу из класом set-display-field.
Если это тег a ( ссылка ) и событие click то информация про количество берется из дата атрибута.
Если это событие change информация берется из атрибута value елмента option.
Дале ajax запрос из параметром sortDisplay и значением.
Если ajax отклчен то обновление страницы.

### Для выбора поля и направления сортировки.
Обрабатывается клик по елементу из класом set-sort-field.
Если это тег a ( ссылка ) и событие click то информация про поле и направление берется из дата атрибута.
Если это событие change информация берется из атрибута value елмента option.
Дале ajax запрос из параметром sortBy и значением.
Если ajax отклчен то обновление страницы.




##### Пример
    [!evoSortBlock?
        &ownerTpl=`<div  class="sorting-block__filters [+class+]"><form action="#">[+display.block+][+sort.block+]</form></div>`
        &displayOwnerTpl=`<div class="sorting-block__filters-amount"><span class="sorting-block__filters-label">Показывать:</span><div class="sorting-block__select"><div class="inline-select"><select class="decor-select js-select[+class+]">[+wrapper+]</select></div></div></div>`
        &sortOwnerTpl=`<div class="sorting-block__filters-type"><span class="sorting-block__filters-label sorting-block__filters-label--type">Сортировать:</span><div class="sorting-block__filters-block"><span class="sorting-block__filters-mobile-active"><span class="sorting-block__filters-mobile-active-inner">По популярности</span></span><ul class="sorting-block__filters-list">[+wrapper+]</ul></div></div>`
        &sortRowTpl=`<li class="sorting-block__filters-item"><a href="#"  [+data+] [+selected+]  class="sorting-block__filters-link [+class+]">[+caption+]</a></li>`
        &sortActiveClass=`is-active`
        &sortConfig=`Название==pagetitle||Дата поступления==menuindex||Цена==price`
        &ajax=`1`
    !]


