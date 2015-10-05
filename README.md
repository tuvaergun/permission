
# tuvaergunrgun/permission 

Laravel Permission adds role based permissions to built in Auth System of Laravel 5. Permission middleware protects routes and even crud controller methods.

# Table of Contents
* [Requirements](#requirements)
* [Getting Started](#getting-started)
* [Documentation](#documentation)
* [Roadmap](#roadmap)
* [Change Logs](#change-logs)
* [Contribution Guidelines](#contribution-guidelines)


# <a name="requirements"></a>Requirements

* This package requires PHP 5.4+

# <a name="getting-started"></a>Getting Started

1. Require the package in your `composer.json` and update your dependency with `composer update`:

```
"require": {
...
"tuvaergun/permission": "~1.0@dev",
...
},
```

2. Add the package to your application service providers in `config/app.php`.

```php
'providers' => [

'Illuminate\Foundation\Providers\ArtisanServiceProvider',
'Illuminate\Auth\AuthServiceProvider',
...
'Tuva\Permission\PermissionServiceProvider',

],
```

3. Publish the package migrations to your application and run these with `php artisan migrate.

```
$ php artisan vendor:publish --provider="Tuva\Permission\PermissionServiceProvider"
```

> **Use your own models.**
> Once you publish, it publishes the configuration file where you can define your own models which should extend to Permission models.

4. Add the middleware to your `app/Http/Kernel.php`.

```php
protected $routeMiddleware = [

....
'permission' => 'Tuva\Permission\Middleware\HasPermission',

];
```

5. Add the HasRole trait to your `User` model.

```php
use Tuva\Permission\Traits\HasRole;

class User extends Model implements AuthenticatableContract, CanResetPasswordContract
{
use Authenticatable, CanResetPassword, HasRole;
}
```

# <a name="documentation"></a>Documentation

Follow along the [Wiki](https://github.com/tuvaergun/permission/wiki) to find out more.

# <a name="roadmap"></a>Roadmap

Here's the TODO list for the next release (**2.0**).

* [ ] Refactoring the source code.
* [ ] Correct all issues.
* [ ] Adding cache to final user permissions.
* [ ] Adding tests.

# <a name="change-logs"></a>Change Logs

**June 14, 2015 (latest)**
* [x] Added backward compatibility to l5.0 for lists() method.
* [x] Added [Blade Template Extensions](https://github.com/tuvaergun/permission/wiki/Blade-Extensions).

*March 28, 2015*
* [x] Added Role Scope to get all users having a specific role. e.g `User::role('admin')->get();` will list all users having `admin` role.

*March 7, 2015*
* [x] `is()` and `can()` methods now support comma for `AND` and pipe as `OR` operator. Or pass an operator as a second param. [more information](https://github.com/tuvaergun/permission/wiki/Validate-Permissions-and-Roles)
* [x] You can bind multiple permissions together so they inherit ones permission. [more information](https://github.com/tuvaergun/permission/wiki/Permissions-Inheritance)

# <a name="contribution-guidelines"></a>Contribution Guidelines

Support follows PSR-2 PHP coding standards, and semantic versioning.

Please report any issue you find in the issues page.
Pull requests are welcome.
