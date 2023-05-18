## Class

Blueprint of an object. We create an object by instantiating a class.

```java
public class House {
		private String color;
		private int floor;
}
```

You can create n number of houses with this blueprint i.e., you can create n no. of objects with this class.

In a single .java file you can have only 1 public class, not more than one.

## Object and Instance

Objects and Instances are same.

```java
House houseObj = new House("Red", 2);
```

## Reference

Reference to the object in memory.

```java
House anotherObj = houseObj; // this just created reference. If you want a separate obj with no memory link use - House anotherObj = new House(houseObj); //Copy constructor
anotherObj.setColor("Blue");
System.Out.println(houseObj.getColor()) //"Blue"
System.Out.println(anotherObj.getColor()) //"Blue"
```

Both ‘anotherObj’ and ‘houseObj’ are pointing to the same object in memory.

## Static Variables

They belong to the Class rather than the object. 

```java
class Dog {
		private static String name;
}

public class Main {
		public static void main(String[] args) {
					Dog rex = new Dog("rex");
					Dog fluffy = new Dog("fluffy");
					rex.printName();     //"fluffy"
					fluffy.printName();  //"fluffy"
		}
}
```

## Static Methods

Static methods can’t access any instance methods or instance variables directly. 

They can’t use ‘this’ keyword. Because this belongs to that instance of the class.

Can’t use ‘super’ keyword. Because super is used to refer to the immediate parent class object.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/997b3f08-8d91-4863-b9a7-b592d6f05125/157a1398-852e-45ea-95f3-4ec9fa1d698d/Untitled.png)

## POJO / Entity / DTO (Data Transfer Object)

Plain old JAVA object is class that only has instance fields

POJO is called entity because it mirrors DB entities

It's a Java object that doesn't have a requirement to implement a particular interface or derive from a particular base class, or make use of particular annotations in order to be compatible with a given framework, and can be any arbitrary (often relatively simple) Java object. 

Below are some properties of the POJO class:

- The POJO class must be public.
- It must have a public default constructor.
- It may have the arguments constructor.
- All objects must have some public Getters and Setters to access the object values by other Java Programs.
- The object in the POJO Class can have any access modifies such as private, public, protected. But, all instance variables should be private for improved security of the project.
- A POJO class should not extend predefined classes.
- It should not implement prespecified interfaces.
- It should not have any prespecified annotation.

## BEAN

Bean is a POJO with some extra rules. A JavaBean follows certain conventions. Getter/setter naming, having a public default constructor, being serialisable etc.

⭐ Class s = new Class();

System.out.println(s); //Here ToString() method is implicitly called if you have overridden it in the Class. 

## Record

Records are immutable entities. They don’t have any setters instead if you want to modify or set any value either pass it in record header or constructor. You can use records when you don’t want to modify the data but want to pass it around as it is. For eg, reading lots of DB entries which dont need modification, just passing those in the program.

```java
// Define a record
public record House(String color, int floors) {}

public class Main {
    public static void main(String[] args) {
        // Create a new House record
        House houseObj = new House("Red", 2);

        // Access the fields using the automatically generated methods
        System.out.println("Color: " + houseObj.color());  // "Red"
        System.out.println("Floors: " + houseObj.floors()); // 2
				houseObj.color = "Blue"; // this gives compile-time error - Error: Cannot assign a value to final variable 'color'
    }
}

```