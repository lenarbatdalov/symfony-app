# Basic
```
symfony new example
symfony server:start --no-tls

панель инструментов профилировщика
composer require --dev symfony/profiler-pack
```

# sqlite
```
composer require symfony/orm-pack
composer require --dev symfony/maker-bundle

edit file .env
php bin/console doctrine:database:create
```

# Creating an Entity Class (database)
```
php bin/console make:entity
php bin/console make:migration
php bin/console doctrine:migrations:migrate
php bin/console dbal:run-sql 'SELECT * FROM product'
```

# controller
```
composer require twig
php bin/console make:controller ProductController
```

# Auth
```
composer require symfony/security-bundle
php bin/console make:user
> User > yes > email > yes
php bin/console make:migration
php bin/console doctrine:migrations:migrate
```
### Auth. Login Form
```
php bin/console make:auth
> Login form authenticator
> LoginFormAuthenticator
> SecurityController
> yes

src/Security/LoginFormAuthenticator.php
line 54 added redirect to app_homepage
```
### Auth. Remember me
```
config/packages/security.yaml

security:
    firewalls:
        main:
            ....
            remember_me:
                secret:   '%kernel.secret%'
                lifetime: 604800 # 1 week in seconds
                path:     /

templates/security/login.html.twig
line 31
        <div class="checkbox mb-3">
            <label>
                <input type="checkbox" name="_remember_me"> Remember me
            </label>
        </div>
```
