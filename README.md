# PHP Interview Questions (all level)

There is an interview tomorrow? 
Is it your first time or are you a senior? Don't worry. Here is a cheat sheet to do the best on your interview and refresh your memory.


### What are [magic methods](https://www.php.net/manual/en/language.oop5.magic.php)? Tell me 3 magic methods.
PHP provides a number of 'magic' methods that allow you to do some pretty neat tricks in object oriented programming.
These methods, identified by a two underscore prefix (__), function as interceptors that are automatically called when certain conditions are met.
- [__toString()](https://www.php.net/manual/en/language.oop5.magic.php#object.tostring)

    > The __toString() method allows a class to decide how it will react when it is treated like a string.
- [__call()](https://www.php.net/manual/en/language.oop5.overloading.php#object.call)

    > This method is triggered when you try to reach a method what is not in the class.
- [__get()](https://www.php.net/manual/en/language.oop5.overloading.php#object.get)

    > This behaves the same as __call() but this on is for class properties not methods.
    
    

