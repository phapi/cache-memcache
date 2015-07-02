# Phapi Memcache

Phapi Memcache is a cache package using Memcache as backend.

<blockquote>Phapi has one important rule regarding cache: A working cache should **not** be a requirement for the application to work. So if Phapi is unable to connect to the cache backend it wont stop the execution. Instead the configured cache will be replaced with a dummy cache, <code>new NullCache()</code>.</blockquote>

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
Phapi Memcache is licensed under the MIT License - see the [license.md](https://github.com/phapi/cache-memcache/blob/master/license.md) file for details

## Contribute
Contribution, bug fixes etc are [always welcome](https://github.com/phapi/cache-memcache/issues/new).
