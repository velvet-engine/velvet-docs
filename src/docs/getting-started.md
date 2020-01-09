# Getting Started

## Requirements

::: warning COMPATIBILITY NOTE
To use Velvet, you need PHP ≥ 7.2
:::

Although using Vue's syntax, Velvet does not require any Javascript runtime on server (i.e. Node)

Velvet also has zero dependency, so rest assure from conflicts with other package

[//]: # (This is for the ease of integrate into other framework)

## Some note

::: warning
__Velvet only support **evergreen** browser__
:::

The reason is the lack of transpiler (e.g. babel). So we only serve ES6+ modules to client.

## Installing

### Via Composer

``` bash
composer require velvet/velvet
```

### Alternatively you can just clone the repo

``` bash
git clone -b master https://github.com/trandinhbao/velvet
```

## Usage

__If you use composer__

```php
<?php
require 'vendor/autoload.php';

use Velvet\Velvet;
```
__...or if you not__

```php
<?php
require 'lib/Velvet.php' // change this to the correct path of the cloned Velvet.php file

use Velvet\Velvet;
```

__Create a simple Velvet instance__

```php
$velvet = new Velvet('/template', '/cache');
$velvet->compileAll();

# This will render the file front.vue, passing the data {message: 'Hello World'}
$velvet->render("front", [
  'message' => 'Hello World'
]);
```
