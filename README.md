# PHP Interview Questions (all level)

There is an interview tomorrow? 
Is it your first time or are you a senior? Don't worry. Here is a cheat sheet to do the best on your interview and refresh your memory.

## Questions

- [What are magic methods? Tell me 3 magic methods.](#what-are-magic-methods-tell-me-3-magic-methods)
- [PHP support multiple inheritance?](#php-support-multiple-inheritance)
- [Interface vs abstract class, tell me the difference.](#interface-vs-abstract-class-tell-me-the-diference)
- [What the final keyword does?](#what-the-final-keyword-does)
- [What does the following code?](#what-does-the-following-code)
- [What are namespaces and how to use them?](#what-are-namespaces-and-how-to-use-them)
- [Explain what are closures?](#explain-what-are-closures)
- [Tell what we need to know about error handling in PHP](#tell-what-we-need-to-know-about-error-handling-in-php)
- [Explain SOLID with examples](#explain-solid-with-examples)

-----
### What are [magic methods](https://www.php.net/manual/en/language.oop5.magic.php)? Tell me 3 magic methods.
PHP provides a number of 'magic' methods that allow you to do some pretty neat tricks in object-oriented programming.
These methods, identified by a two underscore prefix (__), function as interceptors that are automatically called when certain conditions are met.
- [__toString()](https://www.php.net/manual/en/language.oop5.magic.php#object.tostring)

    > The __toString() method allows a class to decide how it will react when it is treated like a string.
- [__call()](https://www.php.net/manual/en/language.oop5.overloading.php#object.call)

    > This method is triggered when you try to reach a method what is not in the class.
- [__get()](https://www.php.net/manual/en/language.oop5.overloading.php#object.get)

    > This behaves the same as __call() but this one is for class properties, not methods.

-----

### PHP support multiple [inheritance](https://www.php.net/manual/en/language.oop5.inheritance.php)?

PHP do not support multiple inheritance. To allow this feature, you can use interfaces in PHP or you can use "Traits" in PHP instead of classes for implementing multiple inheritance in PHP.

-----
    
### [Interface](https://www.php.net/manual/en/language.oop5.interfaces.php) vs [abstract class](https://www.php.net/manual/en/language.oop5.abstract.php), tell me the diference. 

An interface is an OOP element that groups a set of function declarations without implementing them, that is, it specifies the name, return type, and arguments, but not the block of code.

An interface is always an agreement or a promise. When a class says "I implement interface Y", it is saying "I promise to have the same public methods that any object with interface Y has".
```php
    //This is saying that "X" agrees to speak the language "Y" with your code.
    class X implements YInterface { }
    interface YInterface
    {
        // You can't define functionality here for methods (just in class X), these are just skeletons.
        public function setVariable($name, $var);
        public function getHtml($template);
    }
```

On the other hand, an Abstract Class is like a partially built class. It is much like a document with blanks to fill in.

An abstract class is the foundation for another object. When a class says "I extend abstract class Y", it is saying "I use some methods or properties already defined in this other class named Y".
```php
    // this is saying that "X" is going to complete the partial class "Y".
    class X extends YAbstract { }
    abstract class YAbstract
    {
        // These are just skeletons like in the YInterface
        abstract protected function setVariable($name, $var);
        abstract protected function getHtml($template);

        // But in an abstract class you can give functionality for the method.
        public function printOut() {
            print $this->getValue() . "\n";
        }
    }
```

Very important point: In an abstract class you can predefine the working method, but you can't in an interface.

----

### What the [final](https://www.php.net/manual/en/language.oop5.final.php) keyword does?

If you prefix a function in a class with the final keyword, the child class cannot overwrite that function.

```php
class BaseClass {
   final public function moreTesting() {
       echo "BaseClass::moreTesting() called\n";
   }
}

class ChildClass extends BaseClass {
   public function moreTesting() {
       echo "ChildClass::moreTesting() called\n";
   }
}
// Results in Fatal error: Cannot override final method BaseClass::moreTesting()
// You cannot override final methods even if they are defined as private.
```

----

### What does the following code?

```php
function foo(&$var)
{
    $var++;
}

$a = 5;
$b = $a;
$c = $a + 7;

foo($a);

echo $a;
echo $b;
echo $c;
```

<details>
<summary>echo $a;</summary>
<p></p>
<blockquote>
    <p>6</p>
</blockquote>
<p></p>
</details>

<details>
<summary>echo $b;</summary>
<p></p>
<blockquote>
    <p>5</p>
</blockquote>
<p></p>
</details>

<details>
<summary>echo $c;</summary>
<p></p>
<blockquote>
    <p>12</p>
</blockquote>
<p></p>
</details>

---

### What are namespaces and how to use them?

Namespaces in PHP prevent naming conflicts by encapsulating entities like classes, interfaces, functions, and constants. They're like directories for file systems, ensuring that two classes with the same name can coexist if they're in different namespaces.

To declare a namespace, you use the namespace keyword at the top of your PHP file, before any non-comment code. Here's a brief example:

```php
namespace MyProject\Database;

class Connection {}
```

```php
// Using the class from another file
$connection = new \MyProject\Database\Connection();
```
----

### Explain what are [closures](https://www.php.net/manual/en/functions.anonymous.php)?


A closure in PHP is an anonymous function that can capture variables from its surrounding scope. This means you can create a function without a name and pass it around as if it were a regular variable. Closures are useful for creating callback functions.

The use keyword is specifically related to closures in PHP. It allows you to inherit variables from the parent scope (where the closure is defined) into the closure itself. It's important because, by default, the inner function (closure) does not have access to the outer scope's variables.

```php

$message = 'Hello';

$exampleClosure = function() use ($message) {
    echo $message;
};

$exampleClosure(); // Outputs 'Hello'
```

----

### Tell what we need to know about error handling in PHP

**Error Types:**

- _Notices_: Minor issues, like accessing undefined variables. They don't stop script execution.
- _Warnings_: More significant issues, like including a missing file. The script continues to run.
- _Fatal Errors_: Critical problems, like calling undefined functions or classes. The script stops.

**Error Reporting**

- In a development environment, you might want to see all errors and warnings for debugging: error_reporting(E_ALL); or error_reporting(E_ERROR | E_WARNING | E_PARSE);
- In a production environment, you might want to suppress error messages to avoid displaying them to the user: error_reporting(0);

**set_error_handler()**

- The set_error_handler() function in PHP allows you to define a custom function to handle errors instead of using PHP's built-in error handling. This gives you more control over error management and allows for more robust error processing and logging. 

```php

function customErrorHandler($errno, $errstr, $errfile, $errline) {
    echo "Error: [$errno] $errstr - $errfile:$errline";
    // Save error to a log file or database
    return true; // To prevent PHP's default error handler from running
}

set_error_handler("customErrorHandler");

// $errno - holds the level of the error.
// $errstr - holds the error message.
// $errfile - holds the filename in which the error occurred.
// $errline - holds the line number in the file where the error occurred.

```

----

### Explain SOLID with examples

**Single Responsibility principle**

The Single Responsibility Principle means each class should have just one job. Think of it like a worker in a team, where every person has their own clear task. This keeps things simple and organized, making it easier to manage and update the system.

```php
class User {
    function getUserData() { /* ... */ }
    function saveUserData() { /* ... */ }
}

class UserReportGenerator {
    function generateReport(User $user) { /* ... */ }
}
```

**Open/Closed Principle**

The Open/Closed Principle is about designing your classes so that they are open for extension but closed for modification. In simpler terms, it means you should be able to add new features or behaviors to a class without changing its existing code. 

```php
interface Shape {
    public function area();
}

class Circle implements Shape {
    private $radius;

    public function area() {
        return pi() * $this->radius * $this->radius;
    }
}

class Square implements Shape {
    private $length;

    public function area() {
        return $this->length * $this->length;
    }
}
```

**Liskov Substitution Principle**

The Liskov Substitution Principle ensures that objects of a superclass can be replaced with objects of its subclasses without affecting the application's correctness. 

It's like saying, if you have a program that uses a bird, you should be able to swap in a different kind of bird, like a sparrow or a pigeon, and everything should still work just fine. It ensures that a subclass can stand in for its parent class without any errors or unexpected behavior.

```php

// In this setup, Bird is a general class, FlyingBird is a subclass for birds that can fly,
// and Penguin is a subclass for a bird that can't fly (a penguin).
// According to LSP, you should be able to replace instances of Bird with instances of its subclasses (FlyingBird or Penguin) without altering the correctness of the program.

class Bird {
    function move() { /* ... */ }
}

class FlyingBird extends Bird {
    function fly() { /* ... */ }
}

class Penguin extends Bird { /* No fly method */ }

```

**Interface Segregation Principle**

It means designing your interfaces in such a way that your classes don't have to implement methods they don't need. It encourages splitting large, multipurpose interfaces into smaller, more specific ones so that clients only need to know about the methods that are of interest to them. This leads to a cleaner, more organized codebase and reduces the impact of changes.

```php
// Split into two interfaces: Workable and Eatable. Classes implement only the interfaces that are relevant to them.

interface Workable {
    function work();
}

interface Eatable {
    function eat();
}

class HumanWorker implements Workable, Eatable {
    function work() { /* ... */ }
    function eat() { /* ... */ }
}

class RobotWorker implements Workable {
    function work() { /* ... */ }
    // No need to implement eat()
}
```

**Dependency Inversion Principle**

DIP is focusing on decoupling high-level modules from low-level modules by introducing an abstraction layer. 

- High-level modules should not depend on low-level modules. Both should depend on abstractions. 
- Abstractions should not depend on details. Details should depend on abstractions

```php
// Imagine you have a TV remote (the UserDataProcessor) that needs batteries (the DatabaseInterface) to work.
// It doesn't matter what brand of batteries you use (like MySQLDatabase or any other database), as long as they fit the remote.

interface DatabaseInterface {
    function fetchData();
}

class MySQLDatabase implements DatabaseInterface {
    function fetchData() { /* ... */ }
}

class UserDataProcessor {
    private $database;

    function __construct(DatabaseInterface $db) {
        $this->database = $db;
    }

    function processData() {
        $data = $this->database->fetchData();
        // process data
    }
}
```

