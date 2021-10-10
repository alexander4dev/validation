[![Build Status](https://travis-ci.com/alexander4dev/validation.svg?branch=master)](https://secure.travis-ci.com/alexander4dev/validation)
[![Coverage Status](https://coveralls.io/repos/github/alexander4dev/validation/badge.svg?branch=master)](https://coveralls.io/github/alexander4dev/validation?branch=master)
# Installation

```sh
composer require alexander4dev/validation:dev-master
```

# Testing

```sh
composer test
```

# Usage example

```php
    $inputData = [
        'email' => 'test@example.com',
        'regex' => '1',
        'fibonacci' => 1548008755920,
    ];

    $validators = [
        'email' => [
            'validators' => [
                'isEmail',
            ],
        ],
        'regex' => [
            'validators' => [
                ['name' => 'isMatch', 'options' => ['regex' => '/\d+/']]
            ],
        ],
        'fibonacci' => [
            'validators' => [
                'isFibonacci',
            ],
        ],
    ];

    $validationManager = new Validation\ValidationManager($validators, $inputData);

    if (!$validationManager->validate()) {
        foreach ($validationManager->getErrors() as $errorMessage) {
            echo $errorMessage . PHP_EOL;
        }
    } else {
        echo 'Validation passed' . PHP_EOL;
    }
```
