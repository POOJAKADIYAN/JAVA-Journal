# GENERICS

Class, interface, methods or records with type parameters. Generics enable **type safety.**

T = Type Identifier, placeholder for any type

```java
//Normal class 
class ITellYou {
		private String field;
}
//Generic class 
class YouTellMe<T> {
		private T field;
}
```

Raw use of Generics - When you don’t write <T> while using the generic class its called raw use of generics. It’s supported due to backward compatibility, but you should avoid it.

Always use <T> type parameters with generic usage.

**Note -** You can’t use primitive data types with generics, it’ll give compiler error

## Upper Bound For Generics

if we simply write class A<T>, this means that any subclass of java.lang.Object can be passed as a type in class A. That means we can pass String, Integer, any custom class, etc, anything.

Which might be wrong way to use generic in most cases.

What if we want to put a bound here?  like only the classes that implement an interface Comparator can be passed as a type here. This is done like - 

```java
class Team<T extends Player> { // This means that only the subtypes of Player or Player itself can be used as a type here 
}
class Team<T super Player> { // this means that Player or any parent of Player can be used here
}

class Team<T extends AbstractClassA & InterfaceA & InterfaceB> { //class must be listed first
}
```

## Generic Methods

Type parameters are placed between access modifiers and return type.

```java
public <T> void myMethod(T input) {
		return input.toString();
}
```

## Wildcard In Generics

Wildcard is represented by ‘**?**’