# PHP Coding Standards

This documentation describes the **PHP** coding standards for all Seegno projects.

Our main focus will be the use of [Symfony2](http://symfony.com/) framework.

## Table of contents

1. [DocBlocks](#docblocks)

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
