### UserManager ###
Это различные методы связанные с управлением пользователем в EvolutionCMS, все действия связанные с пользователем проходят через эти методы.
#### Доступные функции и примеры использования ####
1. [get](#get) - получение пользователя
2. [create](#create) - регистрация пользователя
3. [edit](#edit) - редактирование пользователя
4. [delete](#delete) - удаление пользователя
5. [getValues](#getValues) - получение TV пользователя
6. [saveValues](#saveValues) - редактирование TV пользователя
7. [login](#login) - авторизация пользователя
8. [loginById](#loginById) - авторизация пользователя по его id
9. [logout](#logout) - Выход пользователя из системы
10. [setRole](#setRole) - назначение пользователю его роли
11. [setGroups](#setGroups) - назначению пользователю его группы пользователей
12. [clearSettings](#clearSettings) - удалеение всех настроек пользователя
13. [saveSettings](#saveSettings) - сохранение настроек пользователя
14. [repairPassword](#repair) - получение хэша для сброса пароля
15. [changePassword](#changePassword) - смена пароля при наличии старого пароля
16. [hashChangePassword](#hashChangePassword) - смена пароля по хэшу полученному из метода [ repairPassword ](#repair)
17. [generateAndSavePassword](#generateAndSavePassword) - смена пароля на автосгенерированный для дальнейшей отправки пользователю
18. [refreshToken](#refreshToken) - обновление токена авторизации
19. [getVerifiedKey](#getVerifiedKey) - получение ключа верификации пользователя
20. [verified](#verified) - подтверждение пользователя с помощью ключа верификации


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

Пользователи по умолчанию создаются подтверждёнными, если необходимо чтобы пользователь был не подтверждён, необходимо в $userData передать элемент с ключом verified и значнием 0

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
$data = [ 'id' => 1 ];
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
<a name="getValues"></a>
**getValues** - получение TV пользователя
```php
array \UserManager::getValues(array $userData, bool $events = true, bool $cache = true)
```
Функция возвращает массив TV пользователя User в формате `[ 'tvname1' => 'tvvalue1', 'tvname2' => 'tvvalue2', ... ]`

Параметры, которые принимает функция:
- userData - массив содержащий поля пользователя.
  - id - обязательное поле, необходимо для поиска пользователя.
  - tvNames - необязательное поле, массив имён TV. Если не указано, то возвращаются все TV.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример общий
```php
$data = [ 'id' => $userid ];
try {
    $arrTVs = \UserManager::getValues($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

Пример получения всех TV пользователя 
```php
$data = [ 'id' => 1 ];
$tvValues = \UserManager::getValues($data);
print_r($tvValues);
```

Пример получения отдельных TV пользователя 
```php
$data = [ 'id' => 1, 'tvNames' => [ 'user_tv1', 'user_tv2' ] ];
$tvValues = \UserManager::getValues($data);
print_r($tvValues);
```

Пример с использованием id пользователя из evo
```php
$userid = evolutionCMS()->getLoginUserID();
$data = [ 'id' => $userid ];
$tvValues = \UserManager::getValues($data);
print_r($tvValues);
```

___
<a name="saveValues"></a>
**saveValues** - редактирование TV пользователя
```php
array \UserManager::saveValues(array $userData, bool $events = true, bool $cache = true)
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

Пример общий
```php
$data = [ 'id' => 1, 'some_tv1' => 'something', 'other_tv2' => 'awesome' ];
try {
    $result = \UserManager::saveValues($data);
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
$data = [ 'username'=> 'manager', 'password' => '123456' ];
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
<a name="loginById"></a>
**loginById** - авторизация пользователя по его id
```php
User \UserManager::loginById(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий поля необходимые для авторизации пользователя. Обязательнон поле id
- $events - указатель вызываем ли мы события связанные с авторизацией пользователя
- $cache - указатель сбрасываем ли кэш после авторизации пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример авторизации пользователя

```php
$data = [ 'id' => 1 ];
try {
    $user = \UserManager::loginById($data);
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
    $username = \UserManager::logout();
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
$data = [ 'id' => 1, 'role' => 2 ];
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
$data = [ 'id' => 1, 'groups' => [1,2]];
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
<a name="clearSettings"></a>
**clearSettings** - удаление всех настроек пользователя
```php
User \UserManager::clearSettings(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает true в случае успешного сохранения

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные с удалением настроек пользователя
- $cache - указатель сбрасываем ли кэш после удаления настроек пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции сохранения настроек пользователей

```php
$data = [ 'id' => 1 ];
try {
    $result = \UserManager::clearSettings($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="saveSettings"></a>
**saveSettings** - сохранение настроек пользователя
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
$data = [ 'id' => 1, 'some_settings' => 'some_data'];
try {
    $result = \UserManager::saveSettings($data);
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
$data = [ 'id' => 1];
try {
    $hash = \UserManager::repairPassword($data);
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
$data = [ 'id' => 1, 'old_password' => '111111', 'password' => '123456', 'password_confirmation' => '123456'];
try {
    $hash = \UserManager::changePassword($data);
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
$data = [ 'hash' => '111111', 'password' => '123456', 'password_confirmation' => '123456'];
try {
    $hash = \UserManager::hashChangePassword($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

<a name="generateAndSavePassword"></a>
 **generateAndSavePassword** - смена пароля на автосгенерированный для дальнейшей отправки пользователю
 ```php
 User \UserManager::generateAndSavePassword(array $userData, bool $events = true, bool $cache = true)
 ```

 Функция возвращает пароль

 Параметры, которые принимает функция:
 - $userData - массив содержащий поле id. Поле обязательно к заполнению.
 - $events - указатель вызываем ли мы события связанные со сменой пароля пользователя
 - $cache - указатель сбрасываем ли кэш после смены пароля пользователя

 **ВНИМАНИЕ**
 Функция может бросить два различных исключения 

 - **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
 - **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

 Пример функции смена пароля

 ```php
 $data = [ 'id' => 1 ];
 try {
     $password = \UserManager::generateAndSavePassword($data);
 } catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
     $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
     print_r($validateErrors); //Выводим все ошибки валидации
 } catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
 }
 ```

 ___
 <a name="refreshToken"></a>
 **refreshToken** - обновление токена авторизации
 ```php
 User \UserManager::refreshToken(array $userData, bool $events = true, bool $cache = true)
 ```

 Функция возвращает актуальный токен

 Параметры, которые принимает функция:
 - $userData - массив содержащий поле refresh_token. Поле обязательно к заполнению.
 - $events - указатель вызываем ли мы события связанные с обновлением токена пользователя
 - $cache - указатель сбрасываем ли кэш после обновления токена пользователя

 **ВНИМАНИЕ**
 Функция может бросить два различных исключения 

 - **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
 - **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

 Пример функции обновления токена

 ```php
 $data = [ 'refresh_token' => '1asdasd1sad2dd4t54351fd1dfs1fd1' ];
 try {
     $token = \UserManager::refreshToken($data);
 } catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
     $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
     print_r($validateErrors); //Выводим все ошибки валидации
 } catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
 }
 ```

 ___
 <a name="getVerifiedKey"></a>
 **getVerifiedKey** - получение ключа верификации пользователя
 ```php
 User \UserManager::getVerifiedKey(array $userData, bool $events = true, bool $cache = true)
 ```

 Функция возвращает объект пользователя из которого можно получить ключ верификации $user->verified_key;

 Параметры, которые принимает функция:
 - $userData - массив содержащий поле id. Поле обязательно к заполнению.
 - $events - указатель вызываем ли мы события связанные с верификацией пользователя
 - $cache - указатель сбрасываем ли кэш после верификации пользователя

 **ВНИМАНИЕ**
 Функция может бросить два различных исключения 

 - **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
 - **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

 Пример функции обновления токена

 ```php
 $data = [ 'id' => '1' ];
 try {
     $user = \UserManager::getVerifiedKey($data);
 } catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
     $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
     print_r($validateErrors); //Выводим все ошибки валидации
 } catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
 }
 ```


 ___
 <a name="verified"></a>
 **verified** - подтверждение пользователя с помощью ключа верификации
 ```php
 User \UserManager::verified(array $userData, bool $events = true, bool $cache = true)
 ```

 Функция возвращает объект пользователя

 Параметры, которые принимает функция:
 - $userData - массив содержащий поля verified_key и username. Оба поля обязательны к заполнению.
 - $events - указатель вызываем ли мы события связанные с верификацией пользователя
 - $cache - указатель сбрасываем ли кэш после оверификациии пользователя

 **ВНИМАНИЕ**
 Функция может бросить два различных исключения 

 - **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
 - **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

 Пример функции обновления токена

 ```php
 $data = [ 'username' => 'test', 'verified_key' => '166a44621c209ef152cc92a2316c6307'];
 try {
     $user = \UserManager::verified($data);
 } catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
     $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
     print_r($validateErrors); //Выводим все ошибки валидации
 } catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
 }
 ```
