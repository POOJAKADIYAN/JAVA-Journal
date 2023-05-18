# ABSTRACTION IN JAVA

Abstract classes and interfaces can have mix of abstract and concrete methods.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/997b3f08-8d91-4863-b9a7-b592d6f05125/24420f6e-cdc1-472b-8cb1-b8d0774fc022/14753115-9b93-4c66-b018-9ba8b1952bbf.png)

⭐ Abstract classes can’t be instantiated. Abstract methods can only be declared on Abstract class or Interface.

A subclass must provide a concrete method for any abstract method declared on its parent.

Abstract methods can’t be private, because subclasses need to define the abstract methods and if we make the abstract method private, subclasses won’t be able to see these methods. How would the define those then?

NOTE - A class can extend only 1 class, but it can implement any number of interfaces

Interfaces are implicitly abstract. Also methods in Interface that don’t have any method body are public and abstract implicitly.

```java
abstract interface FlightEnabled { // all interfaces are abstract
		void fly(); // public and abstract are implied
}
```

|  | **Interface** | **Abstract Class** |
| --- | --- | --- |
| **Concrete methods**  | No (Interfaces can’t have method body) *This is not true after Java 8, because of default and static  methods that can have method body* | Yes (abstract class can have combination of concrete and abstract methods) |
| **Abstract methods** | Yes (all methods in interface are abstract)  | Yes  |
| **Abstraction** | Fully abstract (as all methods are abstract) *This is not true after Java 8, because of default methods* | Partially abstract (as it can have some concrete methods as well) |

## Marker Interfaces

Interfaces with no methods

An interface that doesn’t define any methods but serves to indicate that a class possesses some particular property. It just serves as a special tag for the classes that implements it. 

Eg. - Serializable, Cloneable, Remote

```java
// Marker Interface, it serves as a tag that implementing classes' objects can be serialized into byte stream
public interface Serializable {
}
```

⭐ NOTE - Classes and its methods are **package private** by default

Interfaces are **public** by default. 

For interface methods, **Protected** modifier is not allowed, because the unimplemented methods need to accessible to all the classes.

## Functional Interfaces

*Only 1 abstract method. They can have only 1 functionality to exhibit.*

From Java 8 onwards, [**lambda expressions**](https://www.geeksforgeeks.org/lambda-expressions-java-8/) can be used to represent the instance of a functional interface. 

A functional interface can have any number of default/static methods.

## Default methods in Interface

Java 8 onwards, classes implementing Interface can either use default implementation or override it.

Default methods are public.

This was introduced to allow new functionality to be added to interfaces without breaking existing implementation.

```java
interface Animal {
     void sound();
     
     default void sleep() {
          System.out.println("The animal can sleep.");
     }
}
```

## Private methods in Interface

Java 8 onwards, since java started allowing default methods, we can create private methods inside the interface that can be shared between these default methods if code duplicity is there.

```java
interface Animal {
	   private void log() {
		       System.out.println("Logging animal activity");
	   }
	   
	   default void run() {
		       log();   // private method used inside interface
		       System.out.println("Animal is running");
	   }
}
```

## Static methods in Interface

Static methods in interfaces must have a method body. 

They cannot be overridden by the implementing classes because they belong to the interface itself, not the instances of the classes that implement the interface.

```java
interface Vehicle {
			void start();
			static void service() {
						System.out.println("Servicing vehicle");
			}
}

public class Main {
			public static void main(String[] args) {
						Vehicle.service();   //calling static method with Interface itself
			}
}
```

## Member Variables in Interface

Variables declared in Interface are not instance variables, they are by default **Public**, **Static** and **Final.**

They are constants. 

**Why instance variables are not allowed**:
Interfaces are meant to define a **contract** that implementing classes must follow, focusing on **method signatures** rather than the internal state. Allowing instance variables would conflict with this purpose because interfaces do not maintain an internal state like regular classes do. Instance variables are tied to object instances, but interfaces cannot have instances directly (they are abstract by nature).

Eg. - Integer.MIN_VALUE - this is accessed via Interface name and not instance as its static. It is final so you cannot modify its value. And its public so it can be accessed via any class.

```java
interface ABC {
			~~public static final~~ int count = 10; // here public static final is redundant, that is already implied by default
}
```

**Note** - interface A **extends** ✅ ****interface B. and not **implements** ❌ ****interface B

Also, in interface methods are public (ignoring the private method since they can’t be implemented anyways by implementing classes) so implementing class can’t reduce the visibility level. They need to make these concretions public as well. In other words, interface abstract methods, cant be made protected or private in implementing classes.

**Note** - When we want to call parent class implementation of a method from child class we usually write - 

```java
public void someMethod() {
	   super.parentMethod();
}
```

But in case of interface, let’s say we want to call the default method of interface from the class that implements it

```java
public void somemethod() {
	   InterfaceName.super.interfaceMethod(); // interfaceName. is needed before super keyword because Interface is not a class, nor it has the concept of instance 
	   // so super and this are not supported without interfaceName
}
```

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/997b3f08-8d91-4863-b9a7-b592d6f05125/a4f350bb-2e42-4aa8-84ea-6aa0625b98c0/image.png)

NOTE - If interfaces could have instance variables, it would create ambiguity and complexity in scenarios where multiple interfaces are implemented by the same class. There would be potential conflicts over which interface's instance variable should be used, leading to a **diamond problem**