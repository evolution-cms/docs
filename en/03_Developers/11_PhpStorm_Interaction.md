This instruction will help you configure IDE [PhpStorm](https://jetbrains.com/phpstorm/) in such a way that Blade directives have correct highlighting when working with the program code of the site.

> **Note**  
> When using the [Laravel Idea](https://laravel-idea.com/) plugin, all Blade directives are added automatically. But Evolution CMS has certain Blade directives not supplied by PhpStorm Laravel Idea plugin.

## PhpStorm extension

1. In PhpStorm, open Preferences and go to PHP -> Blade (File | Settings | PHP | Blade).
2. Uncheck "Use default settings" and then click the "Directives" tab.
3. Add new directives.

## Blade directives for Evolution CMS

This list contains only those Blade directives registered with Evolution CMS. To add other directives you may need, refer to the relevant instructions.

### @makeUrl()

The directory `@makeUrl($id)` in the Blade template corresponds to the `UrlProcessor::makeUrl($id);` method call in the PHP code.

Accepts only one argument - resource ID.

#### makeUrl

* Has parameter = YES
* Prefix: <?php echo app("UrlProcessor")->makeUrlWithString(
* Suffix: );?>

### @evoRole()

The `@evoRole($role)` directory in the Blade template is responsible for displaying content depending on the user's role.

Accepts only one argument - the role key, or nothing.

#### evoRole

* Has parameter = YES
* Prefix: <?php if(evo_role(
* Suffix: )): ?>

#### evoElseRole

* Has parameter = YES
* Prefix: <?php elseif(evo_role(
* Suffix: )): ?>

#### evoEndRole

* Has parameter = NO
* Prefix: empty
* Suffix: empty

#### evoConfig

* Has parameter = YES
* Prefix: <?php echo evo()->getConfig(
* Suffix: , "");?>
