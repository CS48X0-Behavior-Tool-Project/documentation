Here is where we should upload any documentation that has to do with testing.


## 3.0 Testing

In the current project, we're going to have several ways to run tests. Every time you commit to the repository it will run automated tests through CircleCI. You will be alerted as to whether these tests have passed or failed. Below, you will find how to create tests, and how to run them.

### 3.1 Creating Tests

Creating tests is simple. When a test is created, it is placed by default in the *src/tests/Feature* folder. Feature tests are used to test if an entire feature works, it's in the name. For example, the ExampleTest.php feature tests to see if we get a 200 return code on the index of the website. To create a feature test:

```sh
docker-compose exec brt php artisan make:test ExampleTest
```

Be sure to replace the "Example" text with whatever text is necessary to describe that test.

Unit tests on the other hand are placed in the *src/tests/Unit* folder, and are created for the sole purpose of testing small individual components of the project, like database seeding. To create a unit test is very similar to creating a feature test:

```sh
docker-compose exec brt php artisan make:test ExampleTest --unit
```

The same applies to above, ensure that you replace the "Example" text with whatever text is necessary to describe that text.

### 3.2 Modifying Tests

As stated before, you can find tests in *src/vendor/Feature* or *src/vendor/Unit*. You can read more about PHPUnit assertions in their [documentation](https://phpunit.readthedocs.io/en/9.3/assertions.html).

There isn't much else to say, aside from the fact that if you want something to be registered as a test function, you must remember to preface the function with the keyword "test". See src/vendor/Unit/ExampleTest.php as an example.

### 3.3 Running Tests

We also have a manual method of testing, with a certain Composer package. PHPUnit is a flexible unit testing library that has been used for ages in PHP, it is the definition of tried and true. To run the tests that have been created:

```sh
docker-compose exec brt php ./vendor/bin/phpunit
```

The PHPUnit command will give a very succinct output, simply displaying how many tests passed successfully. If we want a more verbose output, then we can run the Artisan test command:

```sh
docker-compose exec brt php artisan test
```
