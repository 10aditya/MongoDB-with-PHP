<h1 align="center"><a href="https://docs.mongodb.com/php-library/current/reference/">MongoDB with PHP Cheatsheat</a></h1>

## Terminologies
|<center>RDBMS</center> |<center>MongoDB</center>
|:------------- |:-------------
|RDBMS|MongoDB
|Database|Database
|Table	|Collection
|Tuple/Row	|Document
|column|	Field
|Primary Key	|Primary Key (Default key _id provided by mongodb itself)

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
## Shorthand Selection
```php
$collection = (new MongoDB\Client)->dbname->collectionName;
```

## Queries
* <b> Get all documents </b>
```php
 $cursor = $collection->find();
```

Iterate using for loop

> ``$collection->find().pretty()`` will display documents in pretty format.

* <b> Get document(s) based on a single field </b><br>

Similar to <i>Select * from table where attribute = value</i>

```php
 $cursor = $collection->findOne(array('email'=>$email));
 $cursor = $collection->find({ status: "A" }, { item: 1, status: 1 }) //similar to Select item,status from table where status='A'
 //if any field:0, that field will not be shown
```
``$cursor["attributename"]`` will give value of that attribute</b> <br>

```php
$cursor = $collection->find(array('email'=>'admin@example.com'));
foreach ($cursor as $key){
echo $key['email'];
}
```

* <b> Insert Document </b>
```php
$result = $collection->insertOne([
    'username' => 'admin',
    'email' => 'admin@example.com',
    'name' => 'Admin User',
]);
```
> ``$result->getInsertedCount()`` will return the number of documents inserted.

* <b> Insert Multiple Documents </b>
```php
$res=$coll->insertMany([
		['email'=>'abc@xyz.com','password'=>'123'],
		['email'=>'abc@xyz.com','password'=>'111'],
		['email'=>'xyz@abc.com','password'=>'123'],
		['email'=>'xyz@abc.com','password'=>'111']]);
```

* <b> Delete Document </b>
```php
$var= $collection->deleteOne( ["username"=>"admin"]);
echo $var->getDeletedCount();
```

* <b>Delete Multiple Documents </b>
```php
$var= $collection->deleteMany( ["username"=>"admin"]);
```
> ``$var->getDeletedCount()`` will return the number of documents deleted.

* <b> Count </b>
```php
$c = $coll->count();
```