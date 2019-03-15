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

## Queries
* <b> Get all documents </b>
```php
 $cursor = $collection->find();
```
Iterate using for loop

* <b> Get particular documents </b>
Similar to <i>Select * from table where attribute = value</i>

```php
 $cursor = $collection->findOne(array('email'=>$email));
```

``$cursor["attributename"]`` will give value of that attribute</b> 

