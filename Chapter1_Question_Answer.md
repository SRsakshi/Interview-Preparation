Q1. What is the difference between “==” and “equals(…)” in comparing Java String objects?

A1. When you use “==” (i.e. shallow comparison), you are actually comparing the two object references to see if they point to the same object. When you use “equals(…)”, which is a “deep comparison” that compares the actual string values.

 For example:

```java
public class StringEquals {
 public static void main(String[ ] args) {
   String s1 = "Hello";
   String s2 = new String(s1);
   String s3 = "Hello";

   System.out.println(s1 + " equals " + s2 + "--> " +  s1.equals(s2)); //true

   System.out.println(s1 + " == " + s2 + " --> " + (s1 == s2)); //false
   System.out.println(s1 + " == " + s3+ " --> " + (s1 == s3)); //true
 }
}
```

The variable s1 refers to the String instance created by “Hello”. The object referred to by s2 is created with s1 as an initializer, thus the contents of the two String objects are identical, but they are 2 distinct objects having 2 distinct references s1 and s2. This means that s1 and s2 do not refer to the same object and are, therefore, not ==, but equals( ) as they have the same value “Hello”. The s1 == s3 is true, as they both point to the same object due to internal caching. The references s1 and s3 are interned and points to the same object in the string pool.

---

Q2. Why String class has been made immutable in Java?
A2. For performance & thread-safety.

1. Performance: Immutable objects are ideal for representing values of abstract data (i.e. value objects) types like numbers, enumerated types, etc. If you need a different value, create a different object. In Java, Integer, Long, Float, Character, BigInteger and BigDecimal are all immutable objects. Optimization strategies like caching of hashcode, caching of objects, object pooling, etc can be easily applied to improve performance. If Strings were made mutable, string pooling would not be possible as changing the string with one reference will lead to the wrong value for the other references.

2. Thread safety as immutable objects are inherently thread safe as they cannot be modified once created. They can only be used as read only objects. They can easily be shared among multiple threads for better scalability.

---

Q3. What is method overloading and method overriding?
Method Overloading :
In Method Overloading, Methods of the same class shares the same name but each method must have different number of parameters or parameters having different types and order.
Method Overloading is to “add” or “extend” more to method’s behavior.
It is a compile time polymorphism.
The methods must have different signature.
It may or may not need inheritance in Method Overloading.
Let’s take a look at the example below to understand it better.

```java
class Adder {
Static int add(int a, int b)
{
return a+b;
}
Static double add( double a, double b)
{
return a+b;
}
public static void main(String args[])
{
System.out.println(Adder.add(11,11));
System.out.println(Adder.add(12.3,12.6));
}}
```

Method Overriding:  
In Method Overriding, sub class have the same method with same name and exactly the same number and type of parameters and same return type as a super class.
Method Overriding is to “Change” existing behavior of method.
It is a run time polymorphism.
The methods must have same signature.
It always requires inheritance in Method Overriding.
Let’s take a look at the example below to understand it better.

```
class Car {
void run(){
System.out.println(“car is running”);
}
Class Audi extends Car{
void run()
{
System.out.prinltn(“Audi is running safely with 100km”);
}
public static void main( String args[])
{
Car b=new Audi();
b.run();
}
}
```


---

- What is the final class?

A final class is a constant value of a final variable. Extending A final class is not possible ie., final class may not be sub-classed. A final method cannot be overridden when its class is inherited.


---

- What will happen if you put return statement or System.exit () on try or catch block? Will finally block execute?

Finally block will execute even if you put a return statement in the try block or catch block but finally block won't run if you call System.exit() from try or catch block.

---

- What will happen if we put a key object in a HashMap which is already there?

If you put the same key again then it will replace the old mapping because HashMap doesn't allow duplicate keys. The Same key will result in the same hashcode and will end up at the same position in the bucket.

Each bucket contains a linked list of Map.Entry object, which contains both Key and Value. Now Java will take the Key object from each entry and compare with this new key using equals() method, if that return true then value object in that entry will be replaced by new value.

---

- If a method throws NullPointerException in the superclass, can we override it with a method which throws RuntimeException?

you can very well throw superclass of RuntimeException in overridden method, but you can not do same if its checked Exception.
[Study this](https://javarevisited.blogspot.com/2011/12/method-overloading-vs-method-overriding.html)

---

- What is difference between Checked and Unchecked Exception in Java?

Checked Exceptions should be handled in the code using try-catch block or else method should use throws keyword to let the caller know about the checked exceptions that might be thrown from the method. Unchecked Exceptions are not required to be handled in the program or to mention them in throws clause of the method.

Exception is the super class of all checked exceptions whereas RuntimeException is the super class of all unchecked exceptions. Note that RuntimeException is the child class of Exception.

Checked exceptions are error scenarios that requires to be handled in the code, or else you will get compile time error. For example, if you use FileReader to read a file, it throws FileNotFoundException and we must catch it in the try-catch block or throw it again to the caller method. Unchecked exceptions are mostly caused by poor programming, for example NullPointerException when invoking a method on an object reference without making sure that it’s not null. For example, I can write a method to remove all the vowels from the string. It’s the caller responsibility to make sure not to pass null string. I might change the method to handle these scenarios but ideally the caller should take care of this.

---

- How HashMap works in Java?
HashMap stores key-value pair in Map.Entry static nested class implementation. HashMap works on hashing algorithm and uses hashCode() and equals() method in put and get methods.

When we call put method by passing key-value pair, HashMap uses Key hashCode() with hashing to find out the index to store the key-value pair. The Entry is stored in the LinkedList, so if there are already existing entry, it uses equals() method to check if the passed key already exists, if yes it overwrites the value else it creates a new entry and store this key-value Entry.

When we call get method by passing Key, again it uses the hashCode() to find the index in the array and then use equals() method to find the correct Entry and return it’s value. Below image will explain these detail clearly.

---

- What is the importance of hashCode() and equals() methods?

HashMap uses Key object hashCode() and equals() method to determine the index to put the key-value pair. These methods are also used when we try to get value from HashMap. If these methods are not implemented correctly, two different Key’s might produce same hashCode() and equals() output and in that case rather than storing it at different location, HashMap will consider them same and overwrite them.

Similarly all the collection classes that doesn’t store duplicate data use hashCode() and equals() to find duplicates, so it’s very important to implement them correctly. The implementation of equals() and hashCode() should follow these rules.

If o1.equals(o2), then o1.hashCode() == o2.hashCode()should always be true.
If o1.hashCode() == o2.hashCode is true, it doesn’t mean that o1.equals(o2) will be true.

---

- What is difference between Array and ArrayList? When will you use Array over ArrayList?
Arrays can contain primitive or Objects whereas ArrayList can contain only Objects.
Arrays are fixed size whereas ArrayList size is dynamic.
Arrays doesn’t provide a lot of features like ArrayList, such as addAll, removeAll, iterator etc.

Although ArrayList is the obvious choice when we work on list, there are few times when array are good to use.

If the size of list is fixed and mostly used to store and traverse them.
For list of primitive data types, although Collections use autoboxing to reduce the coding effort but still it makes them slow when working on fixed size primitive data types.
