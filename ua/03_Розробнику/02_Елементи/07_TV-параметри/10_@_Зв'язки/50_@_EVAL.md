**Синтаксис**
```
@EVAL php_code
```
Виконує стрічку php-кода й оброблює значення, яке повертається. 

Де php_code - це фактичний PHP-код, який повинен бути виконаний. Значення, яке повертається може бути стрічкою рядка, масивом або набором записів.
Виконуючи команду @EVAL, ви можете писати php-коди, щоб створити все, що можливо, за допомогою php-скриптів сьогодні.

Це найуніверсальніша і найпотужніша з всіх команда, яка відкриває шлях до необмежених можливостей.

```
@EVAL return «Время:» . time ();
```

## Приклад ##
Необхідно зробити у ТВ, щоб була можливість обирати ресурс з дерева документів (документ під номером 3).
* Створюємо ТВ-параметр, обираємо йому тип вводу "DropDown List Menu".
* В поле "Можливі значення" викликаємо DocLister, даємо йому id і шаблон стрічки рядка для DropDown.

**Виклик сніпета**
```
@EVAL return $modx->runSnippet('DocLister', array( 'parents' => 3, 'tpl'=>'@CODE: [+pagetitle+]==[+id+]||') );
```



### Вкладені прив'язки ###
Як ви бачите з попереднього прикладу, можна вкладати одну @-прив'язку в іншу.

Наприклад, прив'язка @EVAL може бути розміщена всередині ТВ, а в ній використана прив'язка @CODE для шаблону стрічки рядка. Так ви не будете робити зайві чанки, зазвичай вміст з одним-двома рядками.
