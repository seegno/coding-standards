# PHP Coding Standards

This documentation describes the **PHP** coding standards for all Seegno projects.

Our main focus will be the use of [Symfony2](http://symfony.com/) framework.

## Base Standards

We follow the standards described in these documents:
- [PSR-0](http://www.php-fig.org/psr/psr-0/)
- [PSR-1](http://www.php-fig.org/psr/psr-1/)
- [PSR-2](http://www.php-fig.org/psr/psr-2/)

Any extension to those standards will be described here.

### Examples

You can check [Symfony documentation](http://symfony.com/doc/current/contributing/code/standards.html) for more examples since Symfony2 also follows the standards defined in `PSR-0`, `PSR-1` and `PSR-2`.

## Table of contents

1. [Indenting](#indenting)
1. [DocBlocks](#docblocks)
1. [Visibility](#visibility)
1. [Namespace and Use declarations](#namespace-and-use-declarations)
1. [Method declaration](#method-declaration)
1. [Naming conventions](#naming-conventions)
1. [Yoda Conditions](#yoda-conditions)
1. [Tests directory structure](#tests-directory-structure)
1. [Gitignore](#gitignore)

## Indenting

Code indentation *must* be of `4 spaces`.

## DocBlocks

Classes and methods *must* have a multi-line `DocComment` with a brief description of the class/method.

Example:

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

You *must* break `DocComment` if the description exceeds the `80 columns`.

Example:

```php
/**
 * This is a very long method description to demonstrate how to break a comment
 * into several lines if the total number of columns exceeds 80.
 */
public function foobar()
{
    // ...
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

## Namespace and Use declarations

All PHP files *must* have a `namespace` declaration. You *must* also include an `use` declaration for each external class that is used.

Example:

```php
<?php

namespace Vendor\Package;

use \DateTime as DateTime;
use \Exception as Exception;
use Foobar;
use Foobaz as Baz;
use OtherVendor\OtherPackage\Qux;

// ...
```

## Method declaration

All methods *must* have visibility declared and you *must* type all method arguments that you can.
Method names *must* be declared in camelCase.

Example:

```php
/**
 * A brief description of the foobar method.
 */
public function doSomething($arg1, FoobizClass $arg2, array $arg3 = [])
{
    // ...
}
```

If the method declaration exceeds `80 columns`, you *must* break the arguments as shown in the example below.

Example:

```php
/**
 * A method example when the declaration exceeds the 80 columns.
 */
public function doSomething(
    $arg1,
    FoobizClass $arg2,
    array $arg3 = [],
    SomeClass $arg4
) {
```

## Yoda Conditions

You *must* use yoda conditions when doing logical comparisons `===` and `!==`. *Must not* use yoda conditions for `<`, `>`, `<=` and `>=` since they are difficult to read.

```php
if ('foo' === $foobar) {
    // ...
}

if ('bar' !== $foobar) {
    // ...
}
```

## Naming Conventions

Variables, arguments, functions and methods *must* use camelCase, not underscores.

Example:

```php
public function doSomething($firstArgument)
{
    $someVariableName = 'foobar';
}
```

Options and parameters names *must* use underscores, not camelCase.

Example:

```php
public function foobarAction(Request $request, array $options = array())
{
    $mergedOptions = array_merge(
        array(
            'some_default' => 'values',
            'another_default' => 'more values',
        ),
        $options
    );

    if ('string' === $mergedOptions['some_default']) {
        return $request->get('some_parameter');
    }

    return $request->get('another_parameter');
}
```

Prefix abstract classes with `Abstract`.

Example:

```php
// ...

abstract class AbstractFoobar
{
    \\ ...
}
```

Suffix interfaces with `Interface`.

Example:

```php
// ...

interface FoobarInterface
{
    \\ ...
}
```

Suffix traits with `Trait`.

Example:

```php
// ...

trait FoobarTrait
{
    \\ ...
}
```

Suffix exceptions with `Exception`.

Example:

```php
// ...

class FoobarException extends Exception
{
    \\ ...
}
```

## Tests directory structure

Inside the `Tests` directory, unit and integration tests *must* be in separate folders - `Integration/` and `Unit/`.

`Tests/` directory *must* look like the example below:

```php
XXX/...
    FoobarBundle/
        Tests/
            Integration/
                Controller/
                    FoobarControllerTest.php
                    ...
                Entity/
                    FoobarTest.php
                    ...
                Fixtures/
                    FoobarFixtures.php
                    ...
                Manager/
                    FoobarManagerTest.php
                    ...
                Repository/
                    FoobarRepositoryTest.php
                    ...
                ...
            Unit/
                Entity/
                    FoobarTest.php
                    ...
                Manager/
                    FoobarManagerTest.php
                    ...
                ...
```

## Gitignore

Here you'll find a `.gitignore` example:

```php
!app/cache/.gitkeep
!app/logs/.gitkeep
/app/bootstrap.php.cache
/app/cache/*
/app/config/parameters.yml
/app/logs/*
/app/spool/*
/bin/
/composer.phar
/node_modules/
/vendor/
/web/app.php
/web/assets/vendor
/web/build/
/web/bundles/
/web/uploads/
```
