 ## eFilterResult
Сніпет є версткою Doclister. Якщо немає обраних тв параметрів поводить себе як звичаний DocLister
і отримує товари в режимі idType = parents, якщо форма фільтрації не пуста то в режимі documents 
отримує плейсхолдер зі списку ids від eFilter

 ## Параметрb
 ### lang
 Мова необхідна  для схилення. За замовчуванням ru

 ### pid
 аналог parents

 Для роботи ajax необхідна наступна структура шаблону
 ````
 <div id="eFiltr_results_wrapper">
     <div class="eFiltr_loader"></div>
     <div id="eFiltr_results">[+dl.wrap+][+pages+]</div>
 </div>
 ````

 Якщо для eFilter заданий параметр ajax = 1 то стандартна пагінація переоприділяється.
 Верстка пагінації повинна мати клас .pagination!
 ```
&TplNextP = `@CODE: <a data-prefix="" data-page="[+num+]">&gt;</a>`
&TplPrevP = `@CODE: <a data-prefix="" data-page="[+num+]">&lt;</a>`
&TplPage = `@CODE: <a data-prefix="" data-page="[+num+]" class="page">[+num+]</a>`
&TplWrapPaginate=`@CODE: <div class="paginate">[+wrap+]</div>`
```
Можна задати свої шаблони, головне замість href використовувати data-page="[+num+]"
і якщо заданий параметр id для eFilterResult в data-prefix необхідно записати id + '_'


 ### Схилення слова Товар до кількості
 [+параметр_id.pluarl+] Схиляння слова Товар до кількості
 для перевизначення схиляємого слова необхнідни прописати параметри:
 phrase1 Товар
 phrase2 Товару
 phrase3 Товарів


 ### Підвантаження товарів через ajax
 Приклад html шаблону для блоку “Показати ще”
 ```
 [!if? &is=`[+параметр_id.isstop+]:!=:1`  &then=`
    <div class="amount eFilter_more_wrap">
        <a data-page="[+параметр_id.pages_next+]" data-prefix="[+параметр_id.isstop+]_" class="eFilter_more">Показать ещё </a>
    </div>
 `]]
 ```
 eFilter_more_wrap Клас для верстки
 eFilter_more Клас для посилання 
 Якщо id для eFilter не заданий data-prefix порожній
 При використанні "Показати ще" в блоці з класом eFiltr_results повинні бути тільки товари

 ### Кількість товарів і схилення
 Для заміни кількість товарів на сторінці і схиляємо слова товар потрібно задати класи

 filter_display кількість товарів
 filter_plural відмінюване слово
 ```[+параметр_id.pages_next+]``` номер наступної сторінки
