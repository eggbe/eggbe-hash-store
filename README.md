## Introduction
This is the powerful package provides you an easiest way to create and manage of your own lists of hashes.   


## Features
This package is fully file-based so you don't need use any databases. 


## Requirements
* PHP >= 7.0.0
* [Eggbe/Helpers](https://github.com/eggbe/helpers)


## Install
Here's a pretty simple way to start using Eggbe/HashStore:

1. Use [Composer](http://getcomposer.org) to add Eggbe/HashStore in your project: 

```bash
composer require eggbe/hash-store
```

2. Configure the follow setting in your code:

```php
$HashStore = new \Eggbe\HashStore\HashStore([
	'path' => 'path-to-storage-directory',
	'sort' => HashStore::BY_DATE | HashStore::BY_DESC,
	'filter' => '^.{0,32}$',
]);
```

The `path` option define the directory in which all generated files will be stored. Please pay attention what you would get an exception if this directory doesn't exists.
Also the `sort` option specifies the type of sorting and the `filter` option just set a filter for the hashes names.     

3. Sorting:

All hashes stored with a timestamp to have an ability for extended sorting features.

Currently it possible to sort hashes by: 
* Keywords in direct order (`'sort' => HashStore::BY_WORD`)
* Keywords in converse order (`'sort' => HashStore::BY_WORD | HashStore::BY_DESC`) 
* Dates by descending (`'sort' => HashStore::BY_DATE`)
* Dates by ascending (`'sort' => HashStore::BY_DATE | HashStore::BY_DESC`) 


## Usage
You have to use the following method to create and add new hash into storage: 

```php
$HashStore->create('keyword');
```
 
Of course you always can view all existing hashes via the following code: 

```php
foreach($HashStore->all() as $keyword => $content){
	echo $keyword . ' ' . $content;
}  
```

The following method help you to find any hash by a keyword:

```php
$hash = $HashStore->find('keyword');
```

If you need to get a keyword by a hash so it also possible:

```php
$keyword = $HashStore->search('a2f51b04c9a31cd2defc4d3550eecb71');
```

And of course you can remove any hash if you really wish:

```php
$HashStore->remove('keyword');
```

Unfortunately currently this library support only md5 hashes usage but we have plans to extend of the functionality. We will keep you in touch!


## Authors
Made with love at [Eggbe](http://eggbe.com).


## Feedback 
We always welcome your feedback at [github@eggbe.com](mailto:github@eggbe.com).


## License
This package is released under the [MIT license](https://github.com/eggbe/hash-store/blob/master/LICENSE).
