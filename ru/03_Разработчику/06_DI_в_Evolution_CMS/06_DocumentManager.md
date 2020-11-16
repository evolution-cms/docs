### DocumentManager ###
Это различные методы связанные с управлением ресурсами в EvolutionCMS, все действия связанные с пользователем проходят через эти методы.
#### Доступные функции и примеры использования ####
1. [ get ](#get) - получение документа
2. [ create ](#create) - создание документа
3. [ edit ](#edit) - редактирование документа
4. [ delete ](#delete) - удаление документа
5. [ undelete ](#undelete) - восстановление удаленного документа
6. [ duplicate ](#duplicate) - копирование документа
7. [ setGroups ](#setGroups) - установка групп документа
8. [ publish ](#publish) - опубликовать документ
9. [ unpublished ](#unpublished) - снять с публикации документ
10. [ clearCart ](#clearCart) - очистить корзину с удалёнными документами


<a name="get"></a>
**get** - получение документа
```php
SiteContent \DocumentManager::get(integer $documentId)
```
Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentId - id документа который желаем получить

Пример получения документа
```php
$document = \DocumentManager::get(1);
print_r($document->toArray());
```

___
<a name="create"></a>
**create** - создание документа
```php
SiteContent \DocumentManager::create(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий поля документа и TV-шки, для ключей TV названия этих TV. Обязательные поля pagetitle, template
- $events - указатель вызываем ли мы события связанные с созданием документа
- $cache - указатель сбрасываем ли кэш после создания документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции создания документа

```php
$document = ['pagetitle' => 'test', 'template' => '1', 'test'=>'value']; //test - название tv
try {
    $document = \DocumentManager::create($document);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="edit"></a>
**edit** - редактирование документа
```php
SiteContent \DocumentManager::edit(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий поля документа. Обязательные поля: id, необходимо для поиска документа. 
- $events - указатель вызываем ли мы события связанные с редактированием документа
- $cache - указатель сбрасываем ли кэш после редактирования документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции редактирования документа

```php
$data = ['id'=> 1, 'pagetitle' => 'new title', 'test'=>'new value']; //test - название tv
try {
    $document = \DocumentManager::edit($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
     print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```
___
<a name="delete"></a>
**delete** - удаление документа
```php
SiteContent \DocumentManager::delete(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий id документа.
- $events - указатель вызываем ли мы события связанные с удалением документа
- $cache - указатель сбрасываем ли кэш после удаления документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции удаления документа

```php
$data = ['id'=> 1];
try {
    $document = \DocumentManager::delete($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="undelete"></a>
**undelete** - восстановление удаленного документа
```php
SiteContent \DocumentManager::undelete(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий id документа.
- $events - указатель вызываем ли мы события связанные с восстановлением документа
- $cache - указатель сбрасываем ли кэш после восстановления документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример восстановления удалённого документа

```php
$data = ['id'=> 1];
try {
    $document = \DocumentManager::undelete($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="duplicate"></a>
**duplicate** - копирование документа
```php
SiteContent \DocumentManager::duplicate(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий id копируемого документа.
- $events - указатель вызываем ли мы события связанные с копированием документа
- $cache - указатель сбрасываем ли кэш после копирования документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции копирования документа

```php
$data = ['id'=> 1];
try {
    $document = \DocumentManager::duplicate($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="setGroups"></a>
**setGroups** - назначению документу его группы документа
```php
SiteContent \DocumentManager::setGroups(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий id документа и document_groups массив групп документа. Оба поля обязательны.
- $events - указатель вызываем ли мы события связанные с назначением группы документа
- $cache - указатель сбрасываем ли кэш после назначения группы документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции назначения группы документов

```php
$data = ['id'=> 1, 'document_groups' => [1,2]];
try {
    $document = \DocumentManager::setGroups($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="publish"></a>
**publish** - опубликовать документ
```php
SoteContent \DocumentManager::publish(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий id документа. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные публикацией документа
- $cache - указатель сбрасываем ли кэш после публикации документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции публикации документа

```php
$data = ['id'=> 1];
try {
    $document = \DocumentManager::publish($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="unpublished"></a>
**unpublished** - снять с публикации документ
```php
SoteContent \DocumentManager::unpublished(array $documentData, bool $events = true, bool $cache = true)
```

Функция возвращает объект модели документа SiteContent

Параметры, которые принимает функция:
- $documentData - массив содержащий id документа. Поле id является обязательным.
- $events - указатель вызываем ли мы события связанные со снятием с публикации документа
- $cache - указатель сбрасываем ли кэш после снятия с публикации документа

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции снятия с публикации документа

```php
$data = ['id'=> 1];
try {
    $document = \DocumentManager::unpublished($data);
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```

___
<a name="clearCart"></a>
**clearCart** - очистить корзину с удалёнными документами
```php
SoteContent \DocumentManager::clearCart(array $documentData => [], bool $events = true, bool $cache = true)
```

Функция возвращает объект модели первого документа SiteContent 

Параметры, которые принимает функция:
- $documentData - Необязательное поле
- $events - указатель вызываем ли мы события связанные очисткой корзины
- $cache - указатель сбрасываем ли кэш после очистки корзины

**ВНИМАНИЕ**
Функция может бросить два различных исключения 
 
- **\EvolutionCMS\Exceptions\ServiceValidationException** исключение срабатывает в случае если мы передали плохие данные в $documentData.
- **\EvolutionCMS\Exceptions\ServiceActionException** исключение срабатывает в ситуации когда возникла ошибка в процессе обработки данных.

Пример функции очистки корзины

```php
try {
    $document = \DocumentManager::clearCart();
} catch (\EvolutionCMS\Exceptions\ServiceValidationException $exception) {
    $validateErrors = $exception->getValidationErrors(); //Получаем все ошибки валидации
    print_r($validateErrors); //Выводим все ошибки валидации
} catch (\EvolutionCMS\Exceptions\ServiceActionException $exception) {
    print_r($exception->getMessage()); //Выводим ошибку процесса обработки данных
}
```
