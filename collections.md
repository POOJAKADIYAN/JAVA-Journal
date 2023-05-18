# JAVA COLLECTIONS

In Java we can’t create collections of primitive data type

## List

List is an interface in JAVA, classes like ArrayList, LinkedList, Stack, Vector implement this List interface.

```java
String[] items = {"apples", "bananas", "milk"};
List<String> list = List.of(items); // this creates an immutable list of items   .of operator
list.add("almond"); // this will throw an exception  
```

## ArrayList

Resizable list in Java

```java
ArrayList<Integer> list = new ArrayList<Integer>(); // Integer on RHS is optional
ArrayList list = new ArrayList(); //this is allowed in Java, its called raw version of ArrayList, it accepts anything of type Object
```

## Ways to convert array to ArrayList -

1. asList method of Arrays Class - non-resizable but mutable
2. List.of method of List Class - Immutable

```java
// asList
String[] arr = new String[] {"abc", "xyz", "mno"};
var list = Arrays.asList(arr);
// NOTE - any change made to this list is a change to the array as well
// Also the arraylist created like this is not resizable

// List.of
List<String> list = List.of(items);
```

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/997b3f08-8d91-4863-b9a7-b592d6f05125/5e2c76ba-ec37-4f1e-9772-58022311b662/image.png)

## Ways to convert ArrayList to Array -

```java
ArrayList<String> list = new ArrayList<>(List.of("Jan", "Feb", "Mar"));
String[] arr = list.toArray(new String[0]); // if you pass less size here than the list size, still you get an array of size N (size of the list)
// if you pass array size > list size, extra elements are initialized with default value of the datatype.
```

Creating array of primitive types, space is allocated contiguously.

ArrayList is backed by Array only, so space allocated is contiguous, and once memory is reached then new block of memory is allocated so that elements can be stored sequentially.

## LinkedList

Linkedlist is not indexed. It is backed by doubly ended linked list. 

```java
// Queue methods
list.offer("abc"); // adds at the end of the list
list.offerLast("d"); // adds at the end of the list
list.offerFirst("g"); // adds at the front of the list
// Stack methods
list.push("l"); // pushes an element onto the stack represented by this list

// Remove methods
String removedItem = list.remove(); // removes first element in the list

// List Iterator
ListIterator<String> iterator = list.listIterator(); // you can pass index here as param to start iterating from a particular index
while(iterator.hasNext()) {
	var item = iterator.next();
}
```

## Iterators

An Iterator is forwards only and only support the ‘remove’ method.

A ListIterator allows you to navigate both forwards and backwards. It supports ‘remove’, ‘add’, ‘set’ methods

## Autoboxing and Unboxing

Primitive to wrapper objects - Autoboxing

Wrapper objects to primitive type - Unboxing

How Autoboxing works - 

```java
// Way 1
Integer boxedInt = new Integer(15); //deprecated code after Java 9
// Way 2
Integer boxedInt = Integer.valueOf(15);
// Way 3 ----- AUTOBOXING
Integer boxedInt = 15; // always use this
```

How Unboxing works -
```java
Integer boxedInt = 15;
// Way 1
int unboxedInt = boxedInt.intValue(); // manual unboxing
//Way 2 
int unboxedInt = boxedInt; // automatic unboxing. Use this 
```