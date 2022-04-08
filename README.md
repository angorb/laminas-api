# phplange 👆



My no frills docker-compose setup/project skeleton for personal web (PHP) development.

This is ever evolving and subject to improvement as time permits. Mostly it's here so I don't have so set up the same thing for every personal 'huh, I wonder how quickly I can hack this thing together?' project I start (and quickly abandon).

## Contains

- [Standard PHP package skeleton](https://github.com/php-pds/skeleton)
- Apache
- PHP 8.1.x
- PostgreSQL

## Composer Cheat Sheet

### UI Shim Repos

- Bootstrap ([twbs/bootstrap](https://github.com/twbs/bootstrap))
- jQuery ([components/jquery](https://github.com/components/jquery))

#### post-install for Boostrap &

Add these to `composer.json` or, better yet, write a more cogent shell script & execute it from there.

```json
{
    "scripts": {
        "post-update-cmd": [
            "rm -f public/css/bootstrap.min.css public/css/bootstrap.min.css.map public/scripts/bootstrap.min.js public/scripts/jquery.min.js public/scripts/bootstrap.min.js.map",
            "cp vendor/twbs/bootstrap/dist/css/bootstrap.min.* public/css/",
            "cp vendor/twbs/bootstrap/dist/js/bootstrap.min.* public/scripts/",
            "cp vendor/components/jquery/jquery.min.js public/scripts/"
        ]
    }
}
```

### HTTP/Routing

- [league/route](https://github.com/thephpleague/route)
- [laminas/laminas-diactoros](https://github.com/laminas/laminas-diactoros)
- [laminas/laminas-httphandlerrunner](https://github.com/laminas/laminas-httphandlerrunner)

#### .htaccess Setup

Use these rewrite rules in `public/.htaccess` to redirect all request to `index.php`

```htaccess
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . index.php [QSA,L]
```

- [guzzlehttp/guzzle](https://github.com/guzzle/guzzle)

### Logging

- [monolog/monolog](https://github.com/Seldaek/monolog)

### Filesystem

- [Filesystem](https://github.com/thephpleague/climate)

### CLI

- [league/climate](https://github.com/thephpleague/climate)

### Development

- [phpunit/phpunit](https://github.com/sebastianbergmann/phpunit)
- [phpstan/phpstan](https://github.com/phpstan/phpstan)
- [squizlabs/php_codesniffer](https://github.com/squizlabs/PHP_CodeSniffer)
