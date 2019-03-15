<h1 align="center"><a href="#">MongoDB with PHP Cheatsheat</a></h1>

## Install Composer

```sh
composer require "mongodb/mongodb=^1.0.0"
```

## Insert in PHP file
```php
require 'vendor/autoload.php';
```

## Connect to MongoDB Client
```php
$client = new MongoDB\Client();
```

## Select Database
```php
$db = $client->dbname;
```

## Select Collection
```php
$collection = $db->collname;
```