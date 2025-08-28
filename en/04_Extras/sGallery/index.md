## Repository ##
https://github.com/Seiger/sGallery

# sGallery for Evolution CMS
![sGallery](https://user-images.githubusercontent.com/12029039/169609394-08ea36d6-2393-4261-aff2-348f73a6103c.png)
[![Latest Stable Version](https://img.shields.io/packagist/v/seiger/sgallery?label=version)](https://packagist.org/packages/seiger/sgallery)
[![CMS Evolution](https://img.shields.io/badge/CMS-Evolution-brightgreen.svg)](https://github.com/evolution-cms/evolution)
![PHP version](https://img.shields.io/packagist/php-v/seiger/sgallery)
[![License](https://img.shields.io/packagist/l/seiger/sgallery)](https://packagist.org/packages/seiger/sgallery)
[![Issues](https://img.shields.io/github/issues/Seiger/sgallery)](https://github.com/Seiger/sgallery/issues)
[![Stars](https://img.shields.io/packagist/stars/Seiger/sgallery)](https://packagist.org/packages/seiger/sgallery)
[![Total Downloads](https://img.shields.io/packagist/dt/seiger/sgallery)](https://packagist.org/packages/seiger/sgallery)

**sGallery** emerges as a versatile and indispensable plugin tailor-made for Evolution CMS,
revolutionizing the way you manage media assets within your website. Specifically
designed for the Evolution CMS admin panel, this dynamic plugin introduces a host
of powerful features to elevate your content presentation.

**sGallery** stands as a testament to Evolution CMS's commitment to robust and user-friendly
content management. Whether you are a content creator or an administrator, this plugin
empowers you to curate a visually stunning and engaging website with unparalleled ease.
Elevate your media management experience with **sGallery** today.

## Features

- [x] Image and Video Attachment.
- [x] Effortless Media Upload.
- [x] YouTube Integration.
- [x] Sortable Positions.
- [x] Text Fields for File Management.
- [x] Image Resize and AVIF or WEBP Conversion.
- [x] Integration with Custom Modules.
- [x] **[sLang](https://github.com/Seiger/sLang)** Integration.
- [x] More than one tab.
- [x] Full Image slider in Admin panel.

## Supported formats

The following image formats are tested and supported by the package. If your GD/Imagick installation supports
a format that is not listed you are probably fine to use it but your mileage may vary.

| Format | GD | Imagick |
|--------|----| --- |
| jpeg   | ✅  | ✅ |
| png    | ✅  | ✅ |
| gif    | ✅  | ✅ |
| webp   | ✅  | ✅ |
| avif   | ✅  | ✅ |
| heic   | ❌  | ✅ |
| tiff   | ❌  | ✅ |

## Minimum requirements

- Evolution CMS 3.2.0
- PHP 8.2.0
- Composer 2.2.0
- PostgreSQL 10.23.0
- MySQL 8.0.3
- MariaDB 10.5.2
- SQLite 3.25.0

## Install by artisan package installer

Go to You /core/ folder:

```console
cd core
```

Run php artisan command

```console
php artisan package:installrequire seiger/sgallery "*"
```

Generate the config file in **../core/custom/config/seiger/settings** with
name **sgallery.php** the file should return a
comma-separated list of templates.

```console
php artisan vendor:publish --provider="Seiger\sGallery\sGalleryServiceProvider"
```

Run make DB structure with command:

```console
php artisan migrate
```

## Configure

Templates for displaying gallery tabs are configured in the

```console
core/custom/config/seiger/settings/sGallery.php
```

file, where the array contains template IDs for connecting the gallery.

## Usage in blade

Sow all files with Image filter:
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
or YouTube filter
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
or
```php
@foreach(sGallery::collections()->documentId($product->id)->itemType('product')->get() as $item)
    <div class="swiper-slide">
        <a class="js-trigger-fancybox" href="{{$item->src}}" data-fancybox="product-gallery">
            <img loading="lazy" src="{{$item->src}}" width="440" height="440" />
        </a>
    </div>
@endforeach
```

## Integration into the products module

Just paste this code in your View:
```php
{!!sGallery::initialiseView()->viewType('section')->itemType('product')->idType('i')!!}
```

[Full docs](https://seiger.github.io/sGallery/)
