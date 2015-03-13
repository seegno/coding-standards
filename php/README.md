# PHP Coding Standards

This documentation describes the **PHP** coding standards for all Seegno projects.

Our main focus will be the use of [Symfony2](http://symfony.com/) framework.

## Table of contents

1. [DocBlocks](#docblocks)
1. [Visibility](#visibility)

## DocBlocks

Classes and methods should have a multi-line `DocComment` with a brief description of the class/method.

Examples:

```php
/**
 * This handles some foobar stuff.
 */
class Foobar
{
    /**
     * Constructor.
     */
    public function __construct()
    {
        // ...
    }

    /**
     * Process action.
     *
     * @Template()
     */
    public function processAction()
    {
        // ...
    }

    /**
     * Do something cool and nice.
     */
    protected function doSomething()
    {
        // ...
    }
}
```

## Visibility

Visibility *must* be declared on all properties and methods. `abstract` and `final` must be declared before the visibility and `static` must be declared after the visibility.

Declare public methods first, then protected ones and finally private ones. The exceptions to this rule are the class `constructor` and the `setUp` and `tearDown` methods of PHPUnit tests, which should always be the first methods to increase readability.

Examples:

```php
/**
 * This handles some foobar stuff.
 */
class Foobar
{
    public $foo;
    protected $bar;
    private $qux;

    /**
     * Foobar.
     */
    public function foobar()
    {
        // ...
    }

    /**
     * Foobiz.
     */
    protected function foobiz()
    {
        // ...
    }

    /**
     * Foobaz.
     */
    protected function foobaz()
    {
        // ...
    }
}
```

```php
abstract class ClassName
{
    protected static $foobar;

    abstract protected function foo();

    final public static function bar()
    {
        // ...
    }
}
```
