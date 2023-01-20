# Cornell Custom Dev - Laravel Helpers

A collection of Laravel utilities for Cornell Custom Development projects.

## Installation
You can install the package via composer:

```bash
composer require cornell-custom-dev/laravel-helpers
```

## Usage

### PhoneNumber
A class for parsing and formatting a phone number. It parses a wide range of user-formatted input, incorporating a best-guess approach to determining the region a number is from. It formats numbers for user display and for href "tel" numbers that are appropriate when dialing from the US.

This class is a wrapper for [propaganistas/laravel-phone](https://github.com/Propaganistas/Laravel-Phone), which is built on a PHP port of Google's libphonenumber library. The Laravel Phone package provides additional features that may be of use, including Laravel validation rules, but generally requires a more technical knowledge of international phone number formatting.

Examples:

```php
$phoneNumber = new PhoneNumber('6072551111');
echo $phoneNumber->getNumber();
// Outputs '+16072551111'

echo $phoneNumber->getNumberFormattedForUS();
// Outputs '(607) 255-1111'

$phoneNumber = new PhoneNumber('+41446681800');
echo $phoneNumber->getNumberFormattedForUS();
// Outputs '+41 44 668 18 00'

$phoneNumber = new PhoneNumber('44 668 1800', '41');
echo $phoneNumber->getNumberFormattedForUS();
// Outputs '+41 44 668 18 00'

echo $phoneNumber->getNumberFormattedForTel();
// Outputs '+41446681800'
```

See [PhoneNumberTest.php](./tests/PhoneNumberTest.php) for additional usage examples.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md)
