# Comparable VS Comparator

Comparable Interface 

```java
public interface Comparable<T> {
		int compareTo(T o);
}
```

| **Resulting Value** | **Logic** |
| --- | --- |
| 0 | o == this |
| -ve | this < o |
| +ve | this > o |

**Note -** Collections.sort() works on objects that implement Comparable interface. Eg., Arrays.sort()

Comparator Interface

```java
public interface Comparator<T> {
		 int compare(T o1, T o2);
}
```

Collections.sort(arr, comparator) → this requires custom logic of comparator. It wont call comparable.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/997b3f08-8d91-4863-b9a7-b592d6f05125/f516a2f0-1dcb-4ba4-9676-40b280a49b0c/image.png)