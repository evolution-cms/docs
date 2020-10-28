### UserManager ###

#### Доступные функции и примеры использования ####

**get** - получение пользователя
```
User \UserManager::get(integer $userId)
```
Функция возвращает объект модели пользователя User

Параметры, которые принимает функция:
- $userId - id пользователя которого желаем получить

Пример получения пользователя и вывода его атрибутов
```
$user = \UserManager::get(1);
print_r($user->attributes->toArray());
```

___

**create** - регистрация пользователя
```
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

```
$data = ['username' => 'admin22', 'password' => '123456', 'email' => 'test@test.test'];
try {
    $user = \UserManager::create($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
}
```

___

**edit** - редактирование пользователя
```
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

Пример функции регистрации пользователя

```
$data = ['id'=> 1, 'username' => 'admin22', 'password' => '123456', 'email' => 'test@test.test'];
try {
    $user = \UserManager::edit($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
}
```


