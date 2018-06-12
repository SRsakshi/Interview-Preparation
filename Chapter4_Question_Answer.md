Test-Series – Part 4 - Answers
---

- Why `main()` in java is declared as `public static void main`? What if the main method is declared as private?

  Public - main method is called by JVM to run the method which is outside the scope of project therefore the access specifier has to be public to permit call from anywhere outside the application static - When the JVM makes are call to the main method there is not object existing for the class being called therefore it has to have static method to allow invocation from class. void - Java is platform independent language therefore if it will return some value then the value may mean different to different platforms so unlike C it can not assume a behavior of returning value to the operating system. If main method is declared as private then - Program will compile properly but at run-time it will give "Main method not public." error.

- How to create a immutable object in Java? Does all property of immutable object needs to be final?

  To create a object immutable You need to make the class final and all its member final so that once objects gets crated no one can modify its state. You can achieve same functionality by making member as non final but private and not modifying them except in constructor. Also its NOT necessary to have all the properties final since you can achieve same functionality by making member as non final but private and not modifying them except in constructor.

- Can we Override static methods in java?

  We can declare static methods with same signature in subclass, but it is not considered overriding as there won’t be any run-time polymorphism. Hence the answer is ‘No’. Static methods cannot be overridden because method overriding only occurs in the context of dynamic (i.e. runtime) lookup of methods. Static methods (by their name) are looked up statically (i.e. at compile-time).

- What is “this” keyword in java?

  Within an instance method or a constructor, this is a reference to the current object — the object whose method or constructor is being called. You can refer to any member of the current object from within an instance method or a constructor by using this.
  Usage of this keyword

  Used to refer current class instance variable.
  To invoke current class constructor.
  It can be passed as an argument in the method call.
  It can be passed as argument in the constructor call.
  Used to return the current class instance.
  Used to invoke current class method (implicitly)

- Differences between HashMap and HashTable in Java.

  1. HashMap is non synchronized. It is not-thread safe and can’t be shared between many threads without proper synchronization code whereas Hashtable is synchronized. It is thread-safe and can be shared with many threads.
  2. HashMap allows one null key and multiple null values whereas Hashtable doesn’t allow any null key or value.
  3. HashMap is generally preferred over HashTable if thread synchronization is not needed  

- Can a top level class be private or protected?

Top level classes in java can’t be private or protected, but inner classes in java can. The reason for not making a top level class as private is very obvious, because nobody can see a private class and thus they can not use it. Declaring a class as protected also doesn’t make any sense. The only difference between default visibility and protected visibility is that we can use it in any package by inheriting it. Since in java there is no such concept of package inheritance, defining a class as protected is no different from default.

- What is the difference between ‘throw’ and ‘throws’ in Java Exception Handling?

 1. throw keyword is used to throw Exception from any method or static block whereas throws is used to indicate that which Exception can possibly be thrown by this method
 2. If any method throws checked Exception, then caller can either handle this exception(using try catch block )or can re throw it by declaring another ‘throws’ clause in method declaration.
 3. throw clause can be used in any part of code where you feel a specific exception needs to be thrown to the calling method  

- What is `ArrayIndexOutofbounds` Exception in Java?

  Java supports creation and manipulation of arrays, as a data structure. The index of an array is an integer value that has value in interval [0, n-1], where n is the size of the array. If a request for a negative or an index greater than or equal to size of array is made, then the JAVA throws a ArrayIndexOutOfBounds Exception.

  The ArrayIndexOutOfBoundsException is a Runtime Exception thrown only at runtime. The Java Compiler does not check for this error during the compilation of a program.

  Follow-up: Write a code that throws `ArrayIndexOutofbounds` exception and then catch it.

- What is Singleton Class in Java? Write a code to implement the same.

    [Answer](https://www.geeksforgeeks.org/singleton-class-java/)

- Differences between TreeMap, HashMap and LinkedHashMap in Java

  [Answer](https://www.geeksforgeeks.org/differences-treemap-hashmap-linkedhashmap-java/)

- Differences between Comparable vs Comparator in Java. Write a code to implement the same.

    [Answer](https://www.geeksforgeeks.org/comparable-vs-comparator-in-java/)

- What are Restful Web Services?

  RESTful web services are built to work best on the Web. Representational State Transfer (REST) is an architectural style that specifies constraints, such as the uniform interface, that if applied to a web service induce desirable properties, such as performance, scalability, and modifiability, that enable services to work best on the Web. In the REST architectural style, data and functionality are considered resources and are accessed using Uniform Resource Identifiers (URIs), typically links on the Web. The resources are acted upon by using a set of simple, well-defined operations. The REST architectural style constrains an architecture to a client/server architecture and is designed to use a stateless communication protocol, typically HTTP. In the REST architecture style, clients and servers exchange representations of resources by using a standardized interface and protocol.

  RESTful Web Services utilize the features of the HTTP Protocol to provide the API of the Web Service. It uses the HTTP Request Types to indicate the type of operation:

  GET: Retrieve / Query of existing records.
  POST: Creating new records.
  DELETE: Removing records.
  PUT: Updating existing records.

  Using these 4 HTTP Request Types a RESTful API mimics the CRUD operations (Create, Read, Update & Delete). REST is stateless, each call the to a RESTful Web Service is completely stand-alone, it has no knowledge of previous requests.

---

Programs

- Write a program to reverse a number.

```java
public class NumberReverse {

    public int reverseNumber(int number){

        int reverse = 0;
        while(number != 0){
            reverse = (reverse*10)+(number%10);
            number = number/10;
        }
        return reverse;
    }

    public static void main(String a[]){
        NumberReverse nr = new NumberReverse();
        System.out.println("Result: "+nr.reverseNumber(17868));
    }
}

```

- Write a program to check the given number is a prime number or not?

[Answer](https://github.com/a2ankitrai/2KX7/blob/master/Mathematics/Mathematics.md#prime-numbers)

- Write a program to find out duplicate characters in a string.

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Set;

public class DuplicateCharsInString {

    public void findDuplicateChars(String str){

        Map<Character, Integer> dupMap = new HashMap<Character, Integer>();
        char[] chrs = str.toCharArray();
        for(Character ch:chrs){
            if(dupMap.containsKey(ch)){
                dupMap.put(ch, dupMap.get(ch)+1);
            } else {
                dupMap.put(ch, 1);
            }
        }
        Set<Character> keys = dupMap.keySet();
        for(Character ch:keys){
            if(dupMap.get(ch) > 1){
                System.out.println(ch+"--->"+dupMap.get(ch));
            }
        }
    }

    public static void main(String a[]){
        DuplicateCharsInString dcs = new DuplicateCharsInString();
        dcs.findDuplicateChars("Java2Novice");
    }
}
```
