 ## eFilterResult
 Снипеет является оберткой Doclister. Если нет выбраных тв параметров ведет себя как обычный doclister  
 и получает товары в режыме idType = parents, если форма фильтрации не пустая то в режыме documents получая плейсхолдер  
 из списокм ids от eFilter  
 
 ## Параметры
 ###lang
 Язык необходимо для склонения. по умолчанию ru.
 
 ###pid 
 аналог parents 
 
 Для работы ajax необходима следующая структура обертки
 ````
 <div id="eFiltr_results_wrapper">
     <div class="eFiltr_loader"></div>
     <div id="eFiltr_results">[+dl.wrap+][+pages+]</div>
 </div>
 ````
 
 Если для eFilter задан параметр ajax = 1 то стандартная пагинация переопределяеться  
 TplNextP ``<a data-prefix="" data-page="[+num+]">&gt;</a>``  
 TplPrevP ``<a data-prefix="" data-page="[+num+]">&lt;</a>``  
 TplPage ``<a data-prefix="" data-page="[+num+]" class="page">[+num+]</a>``  
 
 Можна задать свои шаблоны главное вместо href использовать data-page="[+num+]"  
 и если задан параметр id для eFilterResult  в data-prefix необходимо записать id + '_'  
 
 Обертка пагинации должна иметь клас .pagination
 
 ### Склонение слова Товар к количеству
 [+параметр_id.pluarl+] Склонение слова Товар к количеству
 Для переопределения склоняемого слова необходимо прописать параметры.
 phrase1 Товар
 phrase2 Товара
 phrase3 Товаров
 
 
 ### Подгрузка товаров через ajax
 Пример html шаблона для блока показать ищо
 ```
 [!if? &is=`[+параметр_id.isstop+]:!=:1`  &then=`
    <div class="amount eFilter_more_wrap">
        <a data-page="[+параметр_id.pages_next+]" data-prefix="[+параметр_id.isstop+]_" class="eFilter_more">Показать ещё </a>
    </div>
 `]]
 ```
 eFilter_more_wrap Клас для обертки
 eFilter_more Клас для ссылки
 Если id для eFilter не задан  data-prefix пустой
 При использование Показать еще в блоке из класом eFiltr_results должны быть только товары
 
 ### Количество товаров и склонение
 Для замены количество товаров на странице и склоняемого слова товар нужно задать класы 
 
 filter_display количество товаров  
 filter_plural склоняемое слово   
 ```[+параметр_id.pages_next+]``` номер следующей страницы
 