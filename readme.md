# Phapi Memcache

**Please note that PHP 7 isn't supported until there is a working Memcached extension for PHP 7.**

Phapi Memcache is a cache package using Memcache(d) as backend.


<blockquote>Phapi has one important rule regarding cache: A working cache should **not** be a requirement for the application to work. So if Phapi is unable to connect to the cache backend it wont stop the execution. Instead the configured cache will be replaced with a dummy cache, <code>new NullCache()</code>.</blockquote>

## Configuration
You need to make two modifications to enable Memcache in Phapi. First, add the needed dependency to composer.json.
```shell
$ composer require phapi/cache-memcache:1.*
```
Second, update your configuration to look something like this:
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
