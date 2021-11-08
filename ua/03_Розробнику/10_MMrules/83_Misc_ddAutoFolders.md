###Віджет для плагіна ManagerManager, дозволяє при збереженні документа (подія OnBeforeDocFormSave) автоматично переміщати його, грунтуючись на його даті (даті публікації, або будь-яку дату в tv) в папку року і місяця.

mm_ddAutoFolders($ddRoles, $ddTemplates, $ddParent, $ddDateSource, $ddYearTpl, $ddMonthTpl, $ddYearPub, $ddMonthPub);

####Опис параметрів
Назва|Опис|Допустимі значення|Значення за замовчуванням|Обов'язковий?
--------|--------|---------|--------|--------
ddRoles|Ролі, для яких необхідно застосувати віджет, порожнє значення — всі ролі.|{comma separated string}|—|false
ddTemplates|Id шаблонів, для яких необхідно застосувати віджет.|{comma separated string}|—|true
ddParent|ID кореневого батька.	|{integer}|—|true
ddDateSource|Поле, з якого необхідно брати дату.|{string}|'pub_date'|false
ddYearTpl|ID шаблону, який необхідно виставляти документам-рокам.|{integer}|0|false
ddMonthTpl|ID шаблону, який необхідно виставляти документам-місяцям.|{integer}|0|false
ddYearPub|Чи треба публікувати документи-роки?|{0; 1}|0|false
ddMonthPub|Чи треба публікувати документи-місяці?|{0; 1}|0|false
