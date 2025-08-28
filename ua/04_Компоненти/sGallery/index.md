## Репозиторій ##
https://github.com/Seiger/sGallery

# sGallery для Evolution CMS
![sGallery](https://user-images.githubusercontent.com/12029039/169609394-08ea36d6-2393-4261-aff2-348f73a6103c.png)
[![Latest Stable Version](https://img.shields.io/packagist/v/seiger/sgallery?label=version)](https://packagist.org/packages/seiger/sgallery)
[![CMS Evolution](https://img.shields.io/badge/CMS-Evolution-brightgreen.svg)](https://github.com/evolution-cms/evolution)
![PHP version](https://img.shields.io/packagist/php-v/seiger/sgallery)
[![License](https://img.shields.io/packagist/l/seiger/sgallery)](https://packagist.org/packages/seiger/sgallery)
[![Issues](https://img.shields.io/github/issues/Seiger/sgallery)](https://github.com/Seiger/sgallery/issues)
[![Stars](https://img.shields.io/packagist/stars/Seiger/sgallery)](https://packagist.org/packages/seiger/sgallery)
[![Total Downloads](https://img.shields.io/packagist/dt/seiger/sgallery)](https://packagist.org/packages/seiger/sgallery)

**sGallery** постає як універсальний та необхідний плагін, створений для Evolution CMS,
який змінює підхід до керування медіафайлами на вашому сайті. Спеціально
розроблений для адміністративної панелі Evolution CMS, цей динамічний плагін надає низку
потужних можливостей для покращення подання контенту.

**sGallery** підтверджує прагнення Evolution CMS до надійного та зручного
керування контентом. Незалежно від того, чи ви контент-менеджер, чи адміністратор, цей плагін
дозволяє легко створювати привабливий та інтерактивний сайт.
Покращіть свій досвід роботи з медіафайлами разом із **sGallery** вже сьогодні.

## Можливості

- [x] Прикріплення зображень та відео
- [x] Просте завантаження медіа
- [x] Інтеграція з YouTube
- [x] Сортування позицій
- [x] Текстові поля для керування файлами
- [x] Зміна розміру зображень та конвертація у AVIF чи WEBP
- [x] Інтеграція з власними модулями
- [x] Інтеграція з **[sLang](https://github.com/Seiger/sLang)**
- [x] Підтримка кількох вкладок
- [x] Повноекранний слайдер у адмінпанелі

## Підтримувані формати

Наведені нижче формати зображень протестовані і підтримуються пакетом. Якщо ваша інсталяція GD/Imagick підтримує
формат, якого тут немає, швидше за все він працюватиме, але результати можуть відрізнятися.

| Формат | GD | Imagick |
|--------|----| --- |
| jpeg   | ✅  | ✅ |
| png    | ✅  | ✅ |
| gif    | ✅  | ✅ |
| webp   | ✅  | ✅ |
| avif   | ✅  | ✅ |
| heic   | ❌  | ✅ |
| tiff   | ❌  | ✅ |

## Мінімальні вимоги

- Evolution CMS 3.2.0
- PHP 8.2.0
- Composer 2.2.0
- PostgreSQL 10.23.0
- MySQL 8.0.3
- MariaDB 10.5.2
- SQLite 3.25.0

## Встановлення через artisan package installer

Перейдіть у теку /core/:

```console
cd core
```

Виконайте команду php artisan

```console
php artisan package:installrequire seiger/sgallery "*"
```

Згенеруйте конфігураційний файл у **../core/custom/config/seiger/settings** з
ім'ям **sgallery.php**. Файл повинен повертати
список шаблонів, розділених комою.

```console
php artisan vendor:publish --provider="Seiger\sGallery\sGalleryServiceProvider"
```

Створіть структуру БД командою:

```console
php artisan migrate
```

## Налаштування

Шаблони для відображення вкладок галереї налаштовуються у файлі

```console
core/custom/config/seiger/settings/sGallery.php
```

, де масив містить ідентифікатори шаблонів для підключення галереї.

## Використання у blade

Показ усіх файлів із фільтром зображень:
```php
@foreach(sGallery::collections()->get() as $item)
    @if(sGallery::hasImage($item->type))
        <a class="swiper-slide" @if(trim($item->link))href="{{$item->link}}"@endif>
            <div class="container">
                <img loading="lazy" class="intro__img" src="{{$item->src}}" alt="{{$item->alt}}" width="1440" height="456">
                <div class="intro__inner">
                    <div class="h1__title">{{$item->title}}</div>
                    <p class="intro__text">{{$item->description}}</p>
                    @if(trim($item->link_text))<div class="btn background__mod">{{$item->link_text}}</div>@endif
                </div>
            </div>
        </a>
    @endif
@endforeach
```
або фільтр YouTube
```php
@foreach(sGallery::collections()->get() as $item)
    @if(sGallery::hasYoutube($item->type))
        <div class="item">
            <div class="video">
                <iframe width="560" height="315" src="https://www.youtube.com/embed/{{$item->file}}" title="YouTube video player" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
            </div>
            <p>{{$item->title}}</p>
        </div>
    @endif
@endforeach
```
або
```php
@foreach(sGallery::collections()->documentId($product->id)->itemType('product')->get() as $item)
    <div class="swiper-slide">
        <a class="js-trigger-fancybox" href="{{$item->src}}" data-fancybox="product-gallery">
            <img loading="lazy" src="{{$item->src}}" width="440" height="440" />
        </a>
    </div>
@endforeach
```

## Інтеграція в модуль продуктів

Просто вставте цей код у ваш View:
```php
{!!sGallery::initialiseView()->viewType('section')->itemType('product')->idType('i')!!}
```

[Повна документація](https://seiger.github.io/sGallery/)
