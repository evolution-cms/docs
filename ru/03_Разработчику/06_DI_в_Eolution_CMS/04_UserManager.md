### UserManager ###

#### Доступные функции и примеры использования ####

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
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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

**delete** - удаление пользователя
```php
User \UserManager::delete(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает username пользователя

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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

**login** - авторизация пользователя
```php
User \UserManager::login(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий поля необходимые для авторизации пользователя. Обязательные поля 
username и password, необходимы для авторизации пользователя. 
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $userData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример авторизации пользователя

```php
$data = ['username'=> 'manager', 'password' => '123456'];
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

**logout** - Выход пользователя из системы
```php
User \UserManager::logout(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает username пользователя

Параметры, которые принимает функция:
- $userData - можно передавать пустой массив или вообще ничего. 
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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

**setRole** - назначению пользователю его роли
```php
User \UserManager::setRole(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя и role оба поля обязательны.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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

**setGroups** - назначению пользователю его группы пользователей
```php
User \UserManager::setGroups(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя и groups массив групп пользователя. Оба поля обязательны.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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

**saveSettings** - сохранение настройки пользователя
```php
User \UserManager::saveSettings(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает true в случае успешного сохранения

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя и прочие данные. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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

**repairPassword** - сохранение настройки пользователя
```php
User \UserManager::repairPassword(array $userData, bool $events = true, bool $cache = true)
```

Функция возвращает hash для сброса пароля

Параметры, которые принимает функция:
- $userData - массив содержащий id пользователя. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные с созданием пользователя
- $cache - указатель сбрасываем ли кэш после создания пользователя

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
