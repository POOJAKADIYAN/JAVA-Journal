## Inheritance

‘*extends*’ keyword

only one class can be extended only one parent class. Multiple inheritance is not supported in JAVA due to diamond problem. Ambiguous reference problem.

super() - calling super class constructor from the child class constructor directly. In constructor chaining we wrote this(), super() is similar to this but for inheritance.

super() has to be the first statement of the constructor like this(). Therefore this() and super() can’t be used from the same constructor.

First child class methods are called if it exists, if JAVA doesn’t find any method in the child class for that name then it goes to the parent class for that method. This allows us to write some custom code on child class instead of directly going to parent class methods. These methods are called **overridden** methods.

⭐ In Inheritance I can write - Animal dog = new Dog(); ✅

But not - ~~Dog dog = new Animal();~~

## Overriding

Overridden methods can do one of these 3 things - 

1. Implement completely different behaviour,  overriding the behaviour of the parent.
2. Simply call the parent class’s method.
3. Call the parent class’s method and include other code to run as well for added functionality.

Note - We can’t override static methods, only instance methods can be overridden

Constructors and private methods can not be overridden

Methods that are final can not be overridden

## java.lang.Object

Every JAVA class extends a special class called Object. It’s in java.lang package

⭐ Only one class in the JAVA source file can be made public.

⭐ toString() method in Object class prints - *ClassName@hashCode of object*

## Text Block