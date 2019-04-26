# PHP Interview Questions (all level)

There is an interview tomorrow? 
Is it your first time or are you a senior? Don't worry. Here is a cheat sheet to do the best on your interview and refresh your memory.

## Questions

- [What are magic methods? Tell me 3 magic methods.](#what-are-magic-methods-tell-me-3-magic-methods)
- [PHP support multiple inheritance?](#php-support-multiple-inheritance)
- [Interface vs abstract class, tell me the diference.](#interface-vs-abstract-class-tell-me-the-diference)
- [What the final keyword does?](#what-the-final-keyword-does)
- [What does the following code?](#what-does-the-following-code)

-----
### What are [magic methods](https://www.php.net/manual/en/language.oop5.magic.php)? Tell me 3 magic methods.
PHP provides a number of 'magic' methods that allow you to do some pretty neat tricks in object oriented programming.
These methods, identified by a two underscore prefix (__), function as interceptors that are automatically called when certain conditions are met.
- [__toString()](https://www.php.net/manual/en/language.oop5.magic.php#object.tostring)

    > The __toString() method allows a class to decide how it will react when it is treated like a string.
- [__call()](https://www.php.net/manual/en/language.oop5.overloading.php#object.call)

    > This method is triggered when you try to reach a method what is not in the class.
- [__get()](https://www.php.net/manual/en/language.oop5.overloading.php#object.get)

    > This behaves the same as __call() but this on is for class properties not methods.

-----

### PHP support multiple [inheritance](https://www.php.net/manual/en/language.oop5.inheritance.php)?

PHP do not support multiple inheritance. To allow this feature, you can use interfaces in PHP or you can use "Traits" in PHP instead of classes for implementing multiple inheritance in PHP.

-----
    
### [Interface](https://www.php.net/manual/en/language.oop5.interfaces.php) vs [abstract class](https://www.php.net/manual/en/language.oop5.abstract.php), tell me the diference. 

An interface is an OOP element that groups a set of function declarations without implementing them, that is, it specifies the name, return type, and arguments, but not the block of code.

An interface is always an agreement or a promise. When a class says "I implement interface Y", it is saying "I promise to have the same public methods that any object with interface Y has".
```php
    // this is saying that "X" agrees to speak language "Y" with your code.
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

        // But in an abstract class you can give functionality for method.
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
