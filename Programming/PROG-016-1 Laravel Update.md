
# Update Laravel 12
1. Update composer.json
require and require-dev
```
"require": {
        "php": "^8.2",
        "guzzlehttp/guzzle": "^7.8",
        "laravel/framework": "^12.0",
        "laravel/sanctum": "^4.0",
        "laravel/tinker": "^2.9"
    },

"require-dev": {
        "fakerphp/faker": "^1.23",
        "laravel/pint": "^1.13",
        "laravel/sail": "^1.26",
        "mockery/mockery": "^1.6.7",
        "nunomaduro/collision": "^8.1",
        "phpunit/phpunit": "^11.0",
        "spatie/laravel-ignition": "^2.4"
    },
```


### Window
```bash
del composer.lock
rmdir /s /q vendor
```


1. Composer update


2. Clear Composer Cache
```bash
del composer.lock
rmdir /s /q vendor
```

3. Optimise Cache
```bash
php artisan optimize: clear
php artisan --version
```

### Linux
```bash
# 删除旧的锁文件和依赖目录
rm -rf vendor
rm composer.lock

# 更新依赖
composer update
```

# Troubleshoot
```
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - Root composer.json requires phpunit/phpunit ^10.5 -> satisfiable by phpunit/phpunit[10.5.0, ..., 10.5.x-dev].
    - Conclusion: don't install laravel/framework v12.0.1 (conflict analysis result)
    - Conclusion: don't install laravel/framework v12.1.0 (conflict analysis result)

...
```

```
Composer update --with-all-dependencies
```


1. 尝试再次生成优化文件（跳过报错的脚本） 
   composer dump-autoload --optimize --no-scripts 
2. 手动清理并重新发现包 
   php artisan optimize:clear 
   php artisan package:discover

# Last Action
1. Delete Vendor File
2. Delete composer.lock
3. Rerun composer install