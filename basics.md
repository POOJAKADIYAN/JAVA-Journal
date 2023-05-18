# JAVA BASICS

## Object VS Reference Variable -

**Object** - Heap memory  eg - new Demo();

**Reference** **Variables** - Stack memory eg - Demo demoObj;

In JAVA, JVM creates the object. We write Classes, that are blueprint → Compiler compiles it to Bytecode



Multiple reference variables can refer to the same object:

```java
String str1 = "Hello";
String str2 = str1; // str2 refers to the same object as str1
```

Once the object is no longer referenced by any part of the code, it becomes **eligible for garbage collection**.

obj = null; // obj no longer references the object

Garbage collection is not immediate; the JVM decides when to run the garbage collector based on resource availability and memory pressure.

## Access Modifiers -

1. **Public** - any class in any package can access
2. **Protected** - class in same package, subclass in other package (Default - package protected)
3. **Private** - no class 

Good Practice - Make members of a class private, to support encapsulation and use public Getter Setter methods for access

⭐ **String is Class, NOT primitive Data Type**

## Default Values For Fields With Primitive Type -

| **boolean** | false |
| --- | --- |
| **byte 
short
int
long
char** | 0 |
| **double
float** | 0.0 |

⭐ **Any other type of fields i.e., non-primitive type like String will have ‘NULL’ value by default**

## this Keyword

refers to the instance that was created when the object was instantiated.

## Constructor

Class className = new Class();

new Class() → this creates a default constructor if no constructor is created explicitly.

Default constructor is also called no-args constructor

**Constructor Chaining -** when one constructor explicitly calls another overloaded constructor.  This can only be used within constructors.

inside caller constructor write this(params), this will call the constructor with params matching.

this(params) has to be the first statement of that constructor.