###Виджет для плагина ManagerManager, позволяющий при сохранении документа (событие OnBeforeDocFormSave) автоматически перемещать его, основываясь на его дате (дате публикации, или любой дате в tv) в папку года и месяца.

mm_ddAutoFolders($ddRoles, $ddTemplates, $ddParent, $ddDateSource, $ddYearTpl, $ddMonthTpl, $ddYearPub, $ddMonthPub);

####Описание параметров
Название|Описание|Допустимые значения|Значение по умолчанию|Обязателен?
--------|--------|---------|--------|--------
ddRoles|Роли, для которых необходимо применить виждет, пустое значение — все роли.|{comma separated string}|—|false
ddTemplates|Id шаблонов, для которых необходимо применить виджет.|{comma separated string}|—|true
ddParent|ID корневого родителя.	|{integer}|—|true
ddDateSource|Поле, из которого необходимо брать дату.|{string}|'pub_date'|false
ddYearTpl|ID шаблона, который необходимо выставлять документам-годам.|{integer}|0|false
ddMonthTpl|ID шаблона, который необходимо выставлять документам-месяцам.|{integer}|0|false
ddYearPub|Надо ли публиковать документы-годы?|{0; 1}|0|false
ddMonthPub|Надо ли публиковать документы-месяцы?|{0; 1}|0|false