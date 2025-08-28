## Repository ##
https://github.com/zatomant/combacart

## Capabilities ##
Using CombaCart, you can create a full-featured online store or marketplace (multiple Sellers on one website) based on EVO 1.4+ or Evolution CMS 3.+, and manage customer Orders.

Important: for editing extended product properties, use separate plugins or modules (multiTV and similar)

For Buyer:
- viewing, adding and editing Products in Cart, and further checkout of Cart into customer Order
- Order Tracking and Payment page
- Nova Poshta shipment tracking
- QR code with payment details
- online payment through LiqPay or monobank
- viewing Order history (personal cabinet). User registration and authorization should be done using Evolution CMS tools or through a specialized plugin, for example HybridAuth.
- multilingual support: Ukrainian, English.

For Manager:
- managing customer Orders on a separate page, by default //your_site/comba
- viewing, editing, changing processing statuses and printing Orders
- sending text messages via email, SMS, text for messengers.

For Administrator:
- automatic removal of Product from Carts if "Available for order" is removed from the product (editing Product page in admin panel (evo))
- for each product you can assign its own Seller
- Seller is a separate legal entity or individual entrepreneur with their own settings.
- when checking out Cart, several Orders will be automatically formed if Products in the cart are from different Sellers (optional)
- if Buyer made a payment on the site, callback from payment service will be processed, and order status will be changed to "Notified about payment"


## Minimum Technical Configuration ##

PHP 7.4 and higher

Composer

EVO CMS 1.4+ [Evolution CMS 1.4](https://github.com/evolution-cms/evolution/tree/1.4.x)
or
Evolution CMS 3.+ [Evolution CMS 3](https://github.com/evolution-cms/evolution/tree/3.2.x)


## Installation ##

For new installation, I recommend using the CombaCart extras package, which is prepared as a file for the Extras module in Evolution CMS.  
To learn details, go to the CombaCart extras page [combacart-extras](https://github.com/zatomant/combacart-extras)

## Updating CombaCart ##  

**Option 1 - Automatically through browser**:  
open in browser the page
```
your_site/assets/plugins/combacart/update/
```

**Option 2 - Automatically through web server console**:  
execute in console
```
cd _root_directory_of_your_site_/assets/plugins/combacart/update/

php process.php
```  
_Options 1 and 2 for automatic update operation require removal of the blocking file in the /combacart/update/ directory_.


**Option 3 - Manual file update**:
- download the latest CombaCart release [github.com](https://github.com/zatomant/combacart) and overwrite files in /assets/plugins/combacart
- in the /assets/plugins/combacart directory execute **composer update** to update dependencies

The composer.json file contains a list of components used in CombaCart.
You can remove unnecessary dependencies at your discretion and modify templates as needed.


## Configuration ##  

I recommend setting your own "secret" in the file /assets/custom/Config/secret.php or in the .env file of your environment variables.  
Otherwise the secret will be formed automatically and its value will depend on server settings.

**file /src/Config/**
* contains default marketplace settings. don't change anything in this directory.

**directory /assets/custom/Config/**
* contains files with your overridden settings according to [Settings Update Rules](https://github.com/zatomant/combacart/docs/override_settings.md)
* for example, place here your marketplace settings and authentication data for third-party services:
    - Nova Poshta (*as of May 2025, for Nova Poshta shipment tracking you may not need to use API key*)
    - LiqPay
    - monobank (currently requires callback testing)
    - SMS provider AlphaSMS
    - and others


**file /src/Bundle/Standalone/Server.php**
* contains the class of standalone local Comba server for Order management:
1. marketplace() method
    - returns general online store settings

2. sellers() method
    - returns data about Sellers (public data)
    - Sellers besides main parameters contain links to Payment Recipients

3. payee() method
    - returns Payment Recipients data
    - Payment Recipients are legal entities or individual entrepreneurs with payment options they support

4. delivery() method
    - returns list of delivery options

5. payment() method
    - returns list of payment options



## First Steps After Installation and Configuration Completion ##

1. Optional step, but it makes things easier.  
   On the Evolution CMS administration page open `Configuration -> Friendly URLs and disable "Use nested URLs"`  
   Use nested URLs: No

2. When installing via Extras [combacart-extras](https://github.com/zatomant/combacart-extras) the necessary elements will be automatically created (otherwise you'll have to create them manually), namely:

    * template for Product Page goods_tmplt
    * template for Checkout page checkout_tmplt
    * template for other pages blank_tmplt

    * tv
        - goods_avail flag whether product is available for order
        - goods_code product article (sku)
        - goods_price product price
        - goods_price_old old product price
        - goods_weight product weight
        - goods_isnewproduct "new product" flag
        - goods_isondemand "product on demand" flag
        - goods_seller Product Seller
        - goods_inbalances flag for product dependency on stock
        - goods_images contains list of images, details about [Images](https://github.com/zatomant/combacart/docs/images.md)
        - goods_goods contains list of product types (optional), uses multiTV

    * snippets:
        - CombaHeader
        - CombaFooter
        - CombaHelper
        - CombaFunctions

    * plugin CombaHelper

3. Create a new page (document), assign it the goods_tmplt template.  
   This will be your first product.
   Product code (article) must be unique within the page (document) context.  
   Details [Products](/docs/product.md)

4. Create a page with alias checkout and assign it the checkout_tmplt template  
   This will be the Checkout page.
   If using a different alias, then override 'PAGE_CHECKOUT'

5. Optional: create a page with alias tnx to which the Buyer will be redirected after creating an order.
   If using a different alias, then override 'PAGE_TNX'
   In the absence of such a page, the modx event 'OnPageNotFound' will be intercepted and processed

6. Create a page with alias cabinet, assign the blank_tmplt template and insert into the resource content ```[!CombaFunctions? &fnct=`cabinet`!]```  
   Details [Buyer Personal Cabinet](https://github.com/zatomant/combacart/docs/cabinet.md)

7. Optional: create a page with alias t - this will be the order tracking page.
   Details [Order Tracking](https://github.com/zatomant/combacart/docs/tracking.md)

8. Optional: create a page with alias p - this will be the page with order payment options.
   Details [Order Payment](https://github.com/zatomant/combacart/docs/payment.md)



## Order Processing ##

After the Buyer has formed an Order (Cart with products sent for processing by Marketplace managers), it can be viewed on the management page.
Any user with 'manager' role who has passed authorization through the EVO administrative page (http(s)://your_site/manager) has access to the page.
After authorization, open the order management page at http(s)://site_name/comba
On the page you can:
- view the list of orders for any time period
- search orders by number, Customer and their email
- edit orders
- print orders
- send emails, SMS messages and generate texts for further use in messengers.

There is a possibility to change language and interface theme.


## Dependencies and Configuration Requirements ##

0. if you get error Class 'IntlDateFormatter' not found  
   install and activate php_intl extension

1. **twig** (required) https://twig.symfony.com/  
   *available in composer.json  
   CombaCart uses twig for templates (after data processing by Modx/Evo parser)

2. **boostrap, bootstrap-icon** (required, optional) https://getbootstrap.com/  
   *available in composer.json  
   CombaCart layout is based on Bootstrap 5  
   if you have an existing bootstrap copy, change the paths to your bootstrap in the snippetGoodsFooter.php file

3. bootbox.js (optional) [bootboxjs](https://github.com/bootboxjs/bootbox)  
   *available in installation package  
   for working with bootstrap dialog forms

4. ~~phpthumb~~  
   decided to abandon this in favor of the more actively updated Intervention/image

5. Intervention\Image (required) [github](https://github.com/Intervention/image)  
   *available in composer.json
   if you use a different image processor than phpthumb, modify the ModxImage class for your needs.

6. multiTV (optional) [multiTV](https://github.com/extras-evolution/multiTV)  
   *installed with extras
    - used for image lists in TV goods_images. instead of lists you can use TV goods_images as "string" for one image
    - used for product subtype lists in TV goods_goods

   To fix the error with image property editing window positioning after multiTV installation    
   replace in file assets/tvs/multitv/css/colorbox.css
   line 5  
   ```#colorbox, #cboxOverlay, #cboxWrapper{position:absolute; top:0; left:0; z1-index:9999; overflow:hidden;}```
   with this  
   ```#colorbox, #cboxOverlay, #cboxWrapper{position:absolute; top:0; left:0; overflow:hidden;}```

7. cropper.js (optional, multiTV component)  
   *available in CombaCart extras installation package
   Description for cropper setup [multiTV](https://github.com/extras-evolution/multiTV)
   used together with multiTV for image lists

8. venobox (optional) [VenoBox](https://github.com/nicolafranchini/VenoBox)  
   *available in installation package  
   used for working with image dialog forms

9. reCaptcha (optional)  
   enter your keys for 'reCaptcha' provider in the override file /assets/custom/Config/provider.php if you want to use captcha when checking order placement


## Other ##  

By default, to support multilingualism on the site and in the order management panel, a built-in "translator" is used.
Details about [Multilingualism in templates](https://github.com/zatomant/combacart/docs/template.md)
