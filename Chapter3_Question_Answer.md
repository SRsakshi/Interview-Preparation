What is Marker interface? How is it used in Java?

The marker interface is a design pattern, used with languages that provide run-time type information about objects. It provides a way to associate metadata with a class where the language does not have explicit support for such metadata. To use this pattern, a class implements a marker interface, and code that interact with instances of that class test for the existence of the interface. Whereas a typical interface specifies methods that an implementing class must support, a marker interface does not do so. The mere presence of such an interface indicates specific behavior on the part of the implementing class. There can be some hybrid interfaces, which both act as markers and specify required methods, are possible but may prove confusing if improperly used. Java utilizes this pattern very well and the example interfaces are

java.io.Serializable - Serializability of a class is enabled by the class implementing the java.io.Serializable interface. The Java Classes that do not implement Serializable interface will not be able to serialize or deserializ their state. All subtypes of a serializable class are themselves serializable. The serialization interface has no methods or fields and serves only to identify the semantics of being serializable.
java.rmi.Remote - The Remote interface serves to identify interfaces whose methods may be invoked from a non-local virtual machine. Any object that is a remote object must directly or indirectly implement this interface. Only those methods specified in a "remote interface", an interface that extends java.rmi.Remote are available remotely.
java.lang.Cloneable - A class implements the Cloneable interface to indicate to the Object.clone() method that it is legal for that method to make a field-for-field copy of instances of that class. Invoking Object's clone method on an instance that does not implement the Cloneable interface results in the exception CloneNotSupportedException being thrown.
javax.servlet.SingleThreadModel - Ensures that servlets handle only one request at a time. This interface has no methods.
java.util.EvenListener - A tagging interface that all event listener interfaces must extend.
The "instanceof" keyword in java can be used to test if an object is of a specified type. So this keyword in combination with Marker interface can be used to take different actions based on type of interface an object implements.

Write a program to find common elements between two arrays.

```java
package com.java2novice.algos;

public class CommonElementsInArray {

    public static void main(String a[]){
        int[] arr1 = {4,7,3,9,2};
        int[] arr2 = {3,2,12,9,40,32,4};
        for(int i=0;i<arr1.length;i++){
            for(int j=0;j<arr2.length;j++){
                if(arr1[i]==arr2[j]){
                    System.out.println(arr1[i]);
                }
            }
        }
    }
}

```


- What is the purpose of garbage collection?

Answer:
The garbage collection process is to identify the objects which are
no longer referenced or needed by a program so that their resources can be
reclaimed and reused. These identified objects will be discarded

- Why do we need generics in java?

Answer:
Code that uses generics has many benefits over non-generic code:

1) Stronger type checks at compile time: A Java compiler applies strong type checking to generic code and issues errors if the code violates type safety. Fixing compile-time errors is easier than fixing runtime errors, which can be difficult to find.

2) Elimination of casts: If you use generics, then explicit type casting is not required.

3) Enabling programmers to implement generic algorithms: By using generics, programmers can implement generic algorithms that work on collections of different types, can be customized, and are type safe and easier to read.


- How can you convert Map to List?

Answer:
We know that Map contains key-value pairs, whereas a list contains
only objects. Since Entry class contains both key-value pair,
Entry class will helps us to convert from Map (HashMap) to
List (ArrayList). By using Map.entrySet() you will get Set
object, which intern you can use it to convert to list object.

Code:
```java
public static void main(String a[]){
	Map<String, String> wordMap = new HashMap<String, String>();
	Set<Entry<String, String>> set = wordMap.entrySet();
	List<Entry<String, String>> list = new ArrayList<Entry<String, String>>(set);
}
```

- Can we have interfaces with no defined methods in java?

Answer:
The interfaces with no defined methods act like markers. They just tell the compiler that the objects of the classes implementing the interfaces with no defined methods need to be treated differently. Marker interfaces are also known as “tag” interfaces.

- Write a Java program to find if a number is prime number or not? [solution](https://javarevisited.blogspot.com/2012/04/java-program-to-print-prime-numbers-in.html)

- Print repeated characters of String? [solution](http://www.java67.com/2014/03/how-to-find-duplicate-characters-in-String-Java-program.html)

-  Reverse a number [solution](https://javarevisited.blogspot.com/2012/04/java-program-to-reverse-number-example.html)
