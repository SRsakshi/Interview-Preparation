
- Can you override a private or static method in Java?

You can not override a private or static method in Java, if you create a similar method with same return type and same method arguments in child class then it will hide the superclass method, this is known as method hiding.

Similarly, you cannot override a private method in sub class because it's not accessible there, what you do is create another private method with the same name in the child class. [See this](http://www.java67.com/2012/08/can-we-override-private-method-in-java.html)

- What is a.hashCode() used for? How is it related to a.equals(b)?

hashCode() method returns an int hash value corresponding to an object. It's used in hash based collection classes e.g Hashtable, HashMap, LinkedHashMap and so on. It's very tightly related to equals() method. According to Java specification, two objects which are equal to each other using equals() method must have same hash code.

- Difference between ArrayList and LinkedList in Java? (answer)

The obvious difference between them is that ArrrayList is backed by array data structure, supprots random access and LinkedList is backed by linked list data structure and doesn't supprot random access. Accessing an element with the index is O(1) in ArrayList but its O(n) in LinkedList. See the answer for more detailed discussion.

-  Is it possible for two unequal objects to have the same hashcode?

Yes, two unequal objects can have same hashcode that's why collision happen in a hashmap.
the equal hashcode contract only says that two equal objects must have the same hashcode it doesn't say anything about the unequal object.

- What is the difference between Comparator and Comparable in Java?

The Comparable interface is used to define the  natural order of object while Comparator is used to define custom order. Comparable can be always one, but we can have multiple comparators to define customized order for objects. [See this](http://www.java67.com/2013/08/difference-between-comparator-and-comparable-in-java-interface-sorting.html)

- Why you need to override hashcode, when you override equals in Java?
 Because equals have code contract mandates to override equals and hashcode together .since many container class like HashMap or HashSet depends on hashcode and equals contract. [See this](https://javarevisited.blogspot.com/2015/01/why-override-equals-hashcode-or-tostring-java.html)

- The difference between checked and unchecked Exception in Java?
checked exception is checked by the compiler at compile time. It's mandatory for a method to either handle the checked exception or declare them in their throws clause. These are the ones which are a sub class of Exception but doesn't descend from RuntimeException. The unchecked exception is the descendant of RuntimeException and not checked by the compiler at compile time. This question is now becoming less popular and you would only find this with interviews with small companies, both investment banks and startups are moved on from this question.

- The difference between throw and throws in Java?

the throw is used to actually throw an instance of java.lang.Throwable class, which means you can throw both Error and Exception using throw keyword e.g.
```
throw new IllegalArgumentException("size must be multiple of 2")
```
On the other hand, throws is used as part of method declaration and signals which kind of exceptions are thrown by this method so that its caller can handle them. It's mandatory to declare any unhandled checked exception in throws clause in Java. Like the previous question, this is another frequently asked Java interview question from errors and exception topic but too easy to answer.

- What do you mean by Object?

An object consists of methods and class which depict its state and perform operations. A java program contains a lot of objects instructing each other their jobs. This concept is a part of core java.

- What is class in Java?

Java encapsulates the codes in various classes which define new data types. These new data types are used to create objects.

---

Programming and Coding Questions


- How to check if a String contains only numeric digits?
[Answer](http://www.java67.com/2014/01/java-regular-expression-to-check-numbers-in-String.html)

- How to reverse a String in Java without using StringBuffer? [solution](http://www.java67.com/2012/12/how-to-reverse-string-in-java-stringbuffer-stringbuilder.html)

- How do you check if two given String are anagrams? [solution](https://javarevisited.blogspot.com/2013/03/Anagram-how-to-check-if-two-string-are-anagrams-example-tutorial.html)

- How do you print duplicate elements from an array in Java? [solution](https://javarevisited.blogspot.com/2015/06/3-ways-to-find-duplicate-elements-in-array-java.html)
