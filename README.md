# RRULE for PHP

Lightweight and fast implementation of recurrence rules for PHP (RFC 5545), to easily work with recurring dates and events (such as in a calendar).
This library is heavily based on [python-dateutil](https://labix.org/python-dateutil).

[![Build Status](https://travis-ci.org/rlanvin/php-rrule.svg?branch=master)](https://travis-ci.org/rlanvin/php-rrule)

## Basic example

```php
use RRule\RRule;

$rrule = new RRule([
	'FREQ' => 'MONTHLY',
	'INTERVAL' => 1,
	'DTSTART' => '2015-06-01',
	'COUNT' => 6
]);

foreach ( $rrule as $occurrence ) {
	echo $occurrence->format('D d M Y'),"\n";
}

// will output:
// Mon 01 Jun 2015
// Wed 01 Jul 2015
// Sat 01 Aug 2015
// Tue 01 Sep 2015
// Thu 01 Oct 2015
// Sun 01 Nov 2015

echo $rrule->humanReadable(),"\n";
// monthly on the 1st of the month, starting from 01/06/2015, 6 times
```

Complete doc is available in [the wiki](https://github.com/rlanvin/php-rrule/wiki).

## Requirements

- PHP >= 5.3
- [intl extension](http://php.net/manual/en/book.intl.php) is recommended for `humanReadable()` but not strictly required

## Installation

The recommended way is to install the lib [through Composer](http://getcomposer.org/).

Just add this to your `composer.json` file (change the version by the release you want, or use dev-master for the development version):

```JSON
{
    "require": {
        "rlanvin/php-rrule": "1.*"
    }
}
```

Then run `composer install` or `composer update`.

Or just run `composer require "rlanvin/php-rrule" "1.*"` for it to be automatically installed and included in your  `composer.json`

Now you can use the autoloader, and you will have access to the library:

```php
<?php
require 'vendor/autoload.php';
```

### Alternative method (not recommended)

- Download [the latest release](https://github.com/rlanvin/php-rrule/releases/latest)
- Put the files in a folder that is autoloaded, or `inclure` or `require` them

## Documentation

Complete doc is available in [the wiki](https://github.com/rlanvin/php-rrule/wiki).

## Contribution

Feel free to contribute! Just create a new issue or a new pull request.

## Note

I started this library because I wasn't happy with the existing implementations
in PHP, so I thought it would be a good learning project to port the
python-dateutil rrule implementation into PHP.

The Python lib was a bit difficult to understand because the algorithms 
are not commented and the variables are very opaque (I'm looking at
you `lno1wkst`). I tried to comment and explain as much of the algorithm as possible
in this PHP port, so feel free to check the code if you're interested.

The lib differs from the python version in various aspects, notably in the 
respect of the RFC. This version is a bit strictier and will not accept many
non-compliant combinations of rule parts, that the python version otherwise accepts.
There are also some additional features in this version.

## License

This library is released under the MIT License.
