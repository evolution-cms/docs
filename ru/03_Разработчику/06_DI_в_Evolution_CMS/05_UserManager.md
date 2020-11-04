### UserManager ###
Это различные методы связанные с управлением пользователем в EvolutionCMS, все действия связанные с пользователем проходят через эти методы.
#### Доступные функции и примеры использования ####
1. [ get ](#get) - получение пользователя
2. [ create ](#create) - регистрация пользователя
3. [ edit ](#edit) - редактирование пользователя
4. [ delete ](#delete) - удаление пользователя
5. [ login ](#login) - авторизация пользователя
6. [ logout ](#logout) - Выход пользователя из системы
7. [ setRole ](#setRole) - назначение польхователю его роли
8. [ setGroups ](#setGroups) - назначению пользователю его группы пользователей
9. [ saveSettings ](#saveSettings) - сохранение настройки пользователя
10. [ repairPassword ](#repair) - получение хэша для сброса пароля
11. [ changePassword ](#changePassword) - смена пароля при наличии старого пароля
12. [ hashChangePassword](#hashChangePassword) - смена пароля по хэшу полученному из метода [ repairPassword ](#repair)


<a name="get"></a>
**get** - получение пользователя
```php
User \UserManager::get(integer $userId)
```
Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userId - id пользователя которого желаем получить

Пример получения пользователя и вывода его атрибутов
```php
$user = \UserManager::get(1);
print_r($user->attributes->toArray());
```

___
<a name="create"></a>
**create** - регистрация пользователя
```php
User \UserManager::create(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий поля пользователя. Обязательные поля 
username, password, password_confirmation, email. 
**password** должен быть минимум 6 символов. **password_confirmation** должен быть равен полю **password**. Поля **email** и **username** должны быть уникальными.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции регистрации пользователя

```php
$data = ['username' => 'admin22', 'password' => '123456', 'password_confirmation' => '123456', 'email' => 'test@test.test'];
try {
    $user = \UserManager::create($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="edit"></a>
**edit** - редактирование пользователя
```php
User \UserManager::edit(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий поля пользователя. Обязательные поля 
id, необходимо для поиска пользователя. В ситуациях если вы передаёте поле **password**: 
**password** должен быть минимум 6 символов. **password_confirmation** должен быть равен полю **password**. 
Если передаёте **email** и **username** они должны быть уникальными для этого пользователя.
- $events - указатель вызываем ли мы события связанные с редактированием пользователя
- $cache - указатель сбрасываем ли кэш после редактирования пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции редактирования пользователя

```php
$data = ['id'=> 1, 'username' => 'admin22', 'email' => 'test@test.test'];
try {
    $user = \UserManager::edit($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```
___
<a name="delete"></a>
**delete** - удаление пользователя
```php
User \UserManager::delete(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает username пользователя

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя.
- $events - указатель вызываем ли мы события связанные с удалением пользователя
- $cache - указатель сбрасываем ли кэш после удаления пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции удаления пользователя

```php
$data = ['id'=> 1];
try {
    $user = \UserManager::delete($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="login"></a>
**login** - авторизация пользователя
```php
User \UserManager::login(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий поля необходимые для авторизации пользователя. Обязательные поля 
username и password, необходимы для авторизации пользователя. 
- $events - указатель вызываем ли мы события связанные с авторизацией пользователя
- $cache - указатель сбрасываем ли кэш после авторизации пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример авторизации пользователя

```php
$data = ['username'=> 'manager', 'password' => '123456'];
try {
    $user = \UserManager::login($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="logout"></a>
**logout** - Выход пользователя из системы
```php
User \UserManager::logout(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает username пользователя

Параметры, которые принимает функция:
- $userData - можно передавать пустой массив или вообще ничего. 
- $events - указатель вызываем ли мы события связанные с выходом пользователя из системы
- $cache - указатель сбрасываем ли кэш после выхода пользователя из системы

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример выхода пользователя из системы

```php
try {
    $user = \UserManager::logout();
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="setRole"></a>
**setRole** - назначению пользователю его роли
```php
User \UserManager::setRole(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя и role оба поля обязательны.
- $events - указатель вызываем ли мы события связанные с назначением роли пользователя
- $cache - указатель сбрасываем ли кэш после назначения роли пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции назначения роли

```php
$data = ['id'=> 1, 'role' => 2];
try {
    $user = \UserManager::setRole($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="setGroups"></a>
**setGroups** - назначению пользователю его группы пользователей
```php
User \UserManager::setGroups(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя и groups массив групп пользователя. Оба поля обязательны.
- $events - указатель вызываем ли мы события связанные с назначением группы пользователя
- $cache - указатель сбрасываем ли кэш после назначения группы пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции назначения группы пользователей

```php
$data = ['id'=> 1, 'groups' => [1,2]];
try {
    $user = \UserManager::setGroups($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="saveSettings"></a>
**saveSettings** - сохранение настройки пользователя
```php
User \UserManager::saveSettings(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает true в случае успешного сохранения

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя и прочие данные. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные с сохранением настроек пользователя
- $cache - указатель сбрасываем ли кэш после сохранения настроек пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции сохранения настроек пользователей

```php
$data = ['id'=> 1, 'some_settings' => 'some_data'];
try {
    $user = \UserManager::saveSettings($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="repair"></a>
**repairPassword** - получение хэша для сброса пароля
```php
User \UserManager::repairPassword(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает hash для сброса пароля

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные с созданием хэша пароля пользователя
- $cache - указатель сбрасываем ли кэш после создания  хэша пароля пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции сброса пароля

```php
$data = ['id'=> 1];
try {
    $user = \UserManager::repairPassword($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="changePassword"></a>
**changePassword** - смена пароля при наличии старого пароля
```php
User \UserManager::changePassword(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает hash для сброса пароля

Параметры, которые принимает функция:
- $userData - массив содержащий поля id, old_password, password, password_confirmation. Все поля обязательны к заполнению.
- $events - указатель вызываем ли мы события связанные со сменой пароля пользователя
- $cache - указатель сбрасываем ли кэш после смены пароля пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции сброса пароля

```php
$data = ['id'=>1, 'old_password'=>'111111', 'password'=>'123456', 'password_confirmation'=>'123456'];
try {
    $user = \UserManager::changePassword($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="hashChangePassword"></a>
**hashChangePassword** - смена пароля по хэшу полученному из метода [ repairPassword ](#repair)
```php
User \UserManager::hashChangePassword(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает hash для сброса пароля

Параметры, которые принимает функция:
- $userData - массив содержащий поля hash, password, password_confirmation. Все поля обязательны к заполнению.
- $events - указатель вызываем ли мы события связанные со сменой пароля пользователя
- $cache - указатель сбрасываем ли кэш после смены пароля пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции сброса пароля

```php
$data = ['hash'=>'111111', 'password'=>'123456', 'password_confirmation'=>'123456'];
try {
    $user = \UserManager::hashChangePassword($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```
