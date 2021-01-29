# Convention defaults

This package is to be required on all php projects

```bash
composer require --dev phpro/symfony-conventions
```

## Configuration
Change your grumphp file to this:
```yaml
imports:
    - { resource: vendor/phpro/symfony-conventions/grumphp.yml }
```

On older projects you might have to clear following dev dependencies first:
```bash
composer remove --dev phpro/grumphp nikic/php-parser phpstan/phpstan friendsofphp/php-cs-fixer jakub-onderka/php-parallel-lint
```

## Overridable parameters

```yaml
parameters:
    phpstan.config: "phpstan.neon"
    phpcsfixer2.config: ".php_cs.dist"
    phpstan.level: 2
    phpparser.ignore:
        - vendor
        - config
    phpstan.ignore:
        - "Tests/"
        - "vendor/"
        - "var/"
        - "src/Migrations/"
        - "spec/"
```

## Override php_cs paths
```php
<?php

$finder = PhpCsFixer\Finder::create()
    ->in('.')
    ->name('*.php')
    ->exclude('vendor')
;

include __DIR__.'/vendor/phpro/symfony-conventions/.php_cs_rules.dist';
return $config;
```