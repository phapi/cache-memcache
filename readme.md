# Memcache Cache Provider

[![Build status](https://img.shields.io/travis/phapi/cache-memcache.svg?style=flat-square)](https://travis-ci.org/phapi/cache-memcache)
[![Code Climate](https://img.shields.io/codeclimate/github/phapi/cache-memcache.svg?style=flat-square)](https://codeclimate.com/github/phapi/cache-memcache)
[![Test Coverage](https://img.shields.io/codeclimate/coverage/github/phapi/cache-memcache.svg?style=flat-square)](https://codeclimate.com/github/phapi/cache-memcache/coverage)

Memcache is a cache package using Memcache as backend.

<blockquote>Phapi has one important rule regarding cache: A working cache should **not** be a requirement for the application to work. So if Phapi is unable to connect to the cache backend it wont stop the execution. Instead the configured cache will be replaced with a dummy cache, <code>new NullCache()</code>.</blockquote>

## Memcache or Memcached?
Please note that there are two cache provider packages available: [phapi/cache-memcache](https://github.com/phapi/cache-memcache) and [phapi/cache-memcached](https://github.com/phapi/cache-memcached). The difference between the packages is the PHP extension they use.

### So which one should you use?
It depends on two things:

- Which extension do you have installed?
- PHP version. Both the [Memcache](http://php.net/manual/en/book.memcache.php) extension and the [Memcached](http://php.net/manual/en/book.memcached.php) exists for PHP 5.6 and HHVM. But according to the [gophp7 project extension catalog](https://github.com/gophp7/gophp7-ext/wiki/extensions-catalog) only Memcached will be updated to PHP 7.

## Installation
The package is **not** installed by default by the Phapi framework. Add the package as a dependency in composer to install the package.

```shell
$ composer require phapi/cache-memcache:1.*
```

## Configuration
Configure the package and add it to the container to enable it.

```php
<?php
$container['cache'] = function ($container) {
    return new \Phapi\Cache\Memcache($servers = [
        [
            'host' => 'localhost',
            'port' => 11211
        ]
    ]);
};
```
Add as many memcache servers as you want by extending the array.

See the [configuration documentation](http://phapi.github.io/docs/started/configuration/) for more information about how to configure the integration with the Phapi Framework.

## General cache usage
```php
<?php
// Add something to the cache
$cache->set('test', 'value');

// Read something from the cache
echo $cache->get('test'); // Will echo "value"

// Check if something exists in the cache
$bool = $cache->has('test');

// Remove from cache
$cache->clear('test');

// Flush the cache
$cache->flush();
```

## License
Memcache Cache Provider is licensed under the MIT License - see the [license.md](https://github.com/phapi/cache-memcache/blob/master/license.md) file for details

## Contribute
Contribution, bug fixes etc are [always welcome](https://github.com/phapi/cache-memcache/issues/new).
