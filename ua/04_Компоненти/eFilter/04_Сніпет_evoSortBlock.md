Сніпет для виведення блоку з налаштувань сортування і вибору кількості товарів на сторінці.

## evoSortBlock
Сніпет для формування блоку сортування. З приємних речей.



## Параметри
1. displayConfig налаштування селекта або посилань для вказівки кількості товарів на сторінці. 
Приклад: 20 || 30 || 40 || все == all.
2. 2.sortConfig налаштування посилань для вказівки поля по якому товари сортуються. 
Приклад: За назву == pagetitle || За індексом == menuindex || Ціна від маленької == price: asc || Ціна від великої == price: desc
3.ajax - використовувати чи ajax за замовчуванням нуль.
4..changeSortByClickField - змінити напрямок сортування при повторному натисканні на параметру сортування. 1/0. За замовчуванням 0. 
Параметр необхідний якщо у нас немає блоку для вибору напрямку, а треба змінювати напрямок при кліці вдруге за параметром поля.

### Шаблони
#### Верстка
1. ownerTpl - Основна верстка блоку.
    Плейсхолдери ```[+class+] [+display.block+] [+sort.block+] [+sort.direction+]```.
    Приклад: ```<div class="[+class+]">[+display.block+][+sort.block+]</div>```

    * class Плейсхолдер з класcами для верстки які необхідніі для роботи js, а саме sort-wrap і ajax
    * display.block блок вибору кількості товарів
    * sort.block блок вибору поля для сортування
    * sort.direction блок вибору напрамку сортування
#### Вибір кількості товарів
   displayOwnerTpl - верстка блоку для вибору кількості елементів на сторінці. 
   Плейсхолдери: [+class+]">[+wrapper+] 
   Приклад: <select class="[+class+]">[+wrapper+]</select> 
   Пример: <div class="[+class+]">[+wrapper+]</div>

2. displayRowTpl - Шаблон виведення рядка. ( option для селекту або тег a для блоку).
    Плейсхолдери: ```[+value+],[+selected+],[+data+],[+class+],[+caption+] ```
    Приклад: ``` <option value="[+value+]" [+selected+] >[+caption+]</option>```
    Приклад: ``` <a [+data+] class="[+class+]">[+caption+]</a> ```
#### Вибір поля для сортування
1. sortOwnerTpl  - обгортка блоку для вибору поля за яким елементи сортуються на сторінці.
    Плейсхолдери: ```[+wrapper+]```
    Приклад: ```<ul>[+wrapper+]</ul>```

2. sortRowTpl - Шаблон виведення посилання для вибору поля.
        Плейсхолдери: ```[+class+],[+data+] [+caption+]```
        Приклад: ```<a class="[+class+]" [+data+]>[+caption+]</a>```

#### Вибір напрямку сортування
1. sortDirectionTpl - верстка блоку вибору напрямку.
    Плейсхолдери: ```[+up+][+down+]```
    up - сортування asc
    down - сортування desc
2. sortDirectionUpTpl - шаблон посилання для вибору напрямку сортування asc
    Плейсхолдери: ```[+class+][+data+]```
    class - css клас
    data - Дата атрибут data-value в якому зберігається поточне поле а напрямок сортування asc. Приклад price: asc
3. sortDirectionDescTpl - шаблон посилання для вибору напрямку сортування desc
    Плейсхолдери: ```[+class+][+data+]```
    class - css клас
    data - Дата атрибут data-value в якому зберігається поточне поле а напрямок сортування asc. Приклад price: desc


##### Класи
1. displayActiveClass - Клас для активного пункту у виборі кількості елементів на сторінці. За замовчуванням active.
2. sortActiveClass - Клас для активного пункту в виборі поля для сортування елементів на сторінці.
3. sortUpClass - Клас для посилання вибору поля коли сортування від маленького до великого. За замовчуванням up
4. sortDownClass - Клас для посилання вибору поля коли сортування від великого до маленького. За замовчуванням down
5. sortFieldClass - Клас для посилань вибору поля і напряму сортування. За замовчуванням set-sort-field.
6. sortDirectionActiveClass - Класс для активной ссылки выбранного направления сортировки. По умолчанию active.


##### Значення за замовчуванням
1. displayDefault - кількість елементів на сторінці за замовчуванням
2. sortFieldDefault - поле сортування за замовчуванням
3. sortOrderDefault - напрямок сортування за замовчуванням


## Встановлювані плейсхолдери для роботи без eFilterResult
 * sort_display - кількість товарів
 * sort_field - поле для сортування
 * sort_order - направление сортировки
Також якщо використовувати сніпет без eFilter необхідно підключити js файл eFilter.js вручну.
А товари обернути у верстку eFilterResult
```
    <div id="eFiltr_results_wrapper">
        <div class="eFiltr_loader"></div>
        <div id="eFiltr_results">
        </div>
    </div>
    ```


## Логіка роботи js.
### Для вибору кількості товарів.
Обробляється клік по елементу з класом set-display-field.
Якщо це тег a (посилання) і подія click, то інформація про кількість береться з дата атрибута.
Якщо ця подія change інформація береться з атрибуту value елемента option.
Далі ajax запит з параметром sortDisplay і значенням.
Якщо ajax відключений, то оновлення сторінки.

### Для вибору поля і напряму сортування.
Обробляється клік по елементу з класом set-sort-field.
Якщо це тег a (посилання) і подія click то інформація про поле і напрямок береться з дата атрибута.
Якщо ця подія change інформація береться з атрибуту value елмента option.
Далі ajax запит з параметром sortBy і значенням.
Якщо ajax відключений то оновлення сторінки.




##### Приклад
    [!evoSortBlock?
        &ownerTpl=`<div  class="sorting-block__filters [+class+]"><form action="#">[+display.block+][+sort.block+]</form></div>`
        &displayOwnerTpl=`<div class="sorting-block__filters-amount"><span class="sorting-block__filters-label">Показывать:</span><div class="sorting-block__select"><div class="inline-select"><select class="decor-select js-select[+class+]">[+wrapper+]</select></div></div></div>`
        &sortOwnerTpl=`<div class="sorting-block__filters-type"><span class="sorting-block__filters-label sorting-block__filters-label--type">Сортувати:</span><div class="sorting-block__filters-block"><span class="sorting-block__filters-mobile-active"><span class="sorting-block__filters-mobile-active-inner">По популярності</span></span><ul class="sorting-block__filters-list">[+wrapper+]</ul></div></div>`
        &sortRowTpl=`<li class="sorting-block__filters-item"><a href="#"  [+data+] [+selected+]  class="sorting-block__filters-link [+class+]">[+caption+]</a></li>`
        &sortActiveClass=`is-active`
        &sortConfig=`Назва==pagetitle||Дата надходження==menuindex||Ціна==price`
        &ajax=`1`
    !]


