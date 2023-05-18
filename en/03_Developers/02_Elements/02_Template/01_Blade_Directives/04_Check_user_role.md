<img src="https://img.shields.io/badge/Evolution%20CMS-%3E%3D3.2.1-brightgreen" alt="Evolution CMS >= 3.2.1">

Starting with version Evolution CMS >= 3.2.1, it became possible to display content depending on the user's role using the `@evoRole` directive. Example:

```blade
@evoRole('Administrator')
     This text will only be visible to a user with the Administrator role.
@evoEndRole
```

> **Warning**  
> Be very careful, the `@evoRole` directive requires the `@evoEndRole` directive to close the display block. If the `@evoEndRole' directive is omitted, it will lead to errors in the site's operation.

By default, the following roles are available after installing Evolution CMS:

* Administrator
* Editor
* Publisher

### Output data subject to role validation

Above is the simplest case of user role verification. At the expense of displaying your own text for each role, in this case the `@evoElseRole` directive will be useful. Example:

```blade
@evoRole('Administrator')
     This text will only be visible to a user with the Administrator role.
@evoElseRole('Editor')
     This text will only be visible to a user with the Editor role.
@evoElseRole()
     This text will be shown to all users who are authorized on the site.
@else
     This text will be shown to all others, including unauthorized users.
@evoEndRole
```

### User authorization check

If an empty string is passed as an argument to the `@evoRole` and `@evoElseRole` directives, or nothing is passed, the check is performed only for user authorization.

```blade
@evoRole()
     This user is authorized on the site.
@else
     This user is not authorized on the site.
@evoEndRole
```