# QC Questions on Java Basics
 - What is Java?
    - Object-Oriented: Java uses objects and classes to organize code, making it easier to manage and reuse.
    - Platform-Independent: Java code runs on the JVM, making it portable across different operating systems (Windows, Mac, Linux).

 - Pillars of OOP
    - Abstraction : the concept of hiding / Contract  by using abstract(extends) and Interface(Implements)
    - Polymorphism : Many form -> overloading(dif parameter same name) and overriding (same everything)
    - Inheritance :  Parent -> child 
    - Encasulation :  technique to make data as "one unit" -> by making var private / protected

 - Define Abstraction
   - Abstraction simplifies a complex system by showing only the essential attributes and behaviors, while hiding unnecessary detail:
      - Abstract Classes: Classes that cannot be instantiated on their own and may contain abstract methods (methods without a body).
      - Interfaces: Define a contract of methods that a class must implement.

 - Define Polymorphism
   - Many Forms -> Involves changing the behavior of a method through overriding and overloading:
      - Method Overriding (Run-time Polymorphism): same method name , same paramaeter usually the changes happen in the subclass
      - Method Overloading (Compile-time Polymorphism) : same name  but different parameter 

 - Define Inheritance
   -  Inheritance allows you to use the code written in one class in another class without having to rewrite it.
   - Inheritance in Java is implemented using: 
      - "extends"


 - Define Encapsulation
   -  It refers to the bundling of data (variables) and methods that operate on that data into a single unit:
      - Making the fields (data) private
      - Providing public getter and setter methods

 - In what way does Java employ abstraction?
   - Abstraction in Java is primarily achieved through:
      - Abstract Classes (extends)
      - Interfaces (implements)

 - In what way does Java employ polymorphism?
   - Method Overriding (Run-time Polymorphism)
   - Method Overloading (Compile-time Polymorphism)

 - In what way does Java employ inheritance?
   - Reusing Code : child can reuse parent method
   - Creating a Class Hierarchy: PARENT > CHILD CLASS
   - Extending Functionality : you can write new stuff thorugh child or event overide method

 - In what way does Java employ encapsulation?
   - Private Fields
   - Public Getters and Setters
   - Data Hiding

 - Describe the JDK, JRE, and the JVM
   - jvm < jre < jdk:
      - jvm (java vitual machine) : acts like a puzzle piece that fits into different operating systems
      - jre (Java Runtime Environment) : provide the enviroment to run java 
      - jdk (Java Development Kit) : Contains everything needed to develop and run Java applications.

 - What is the difference between an object and a class?
   - Class: Blueprint or template that defines properties and behaviors.
   - Object: Instance of a class; actual representation with data.

 - List the Java primitive types
   - byte
   - short
   - int
   - long
   - float
   - double
   - char
   - boolean

 - What are wrapper classes?
   - in Java are objects that encapsulate (wrap) a primitive data type within an object.
   - summary : to make primitive data as an object 

 - What is autoboxing and unboxing?
   - Autoboxing: Automatic to change a primitive to its wrapper object.
   - Unboxing: Automatic to change a wrapper object to its primitive.

 - What does the "final" keyword mean?
   - Final Variable: Once assigned, its value cannot be changed.
   - Final Method: Cannot be overridden by subclasses.
   - Final Class: Cannot be subclassed.


 - What does the "static" keyword mean?
   - Static Variable: A single copy of the variable is shared across all instances of the class.
   - Static Method: 
      - A method that belongs to the class rather than to any object instance. 
      - It can be called without creating an instance of the class.
   - Static Block: A block of code that runs once when the class is loaded into memory, typically used for static initialization.


 - What are variable arguments?
   - Java allow a method to accept zero or more arguments
   - example : 
   ```java
   public static int sum(int... numbers)
      System.out.println(sum(1, 2, 3)); 
      System.out.println(sum(4, 5)); 
   ```

 - What is the "new" keyword used for?
   - Create an Object: Instantiate a class by calling its constructor.
   - Allocate Memory: Allocate memory for the new object in the heap.
   - Initialize the Object: Call the class's constructor to initialize the object.

 - What is the "super" keyword used for?
   - Call the constructor / method of the superclass from the subclass constructor
   
 - What is the "this" keyword used for?
 - What is a constructor?
 - What is the difference between the == operator and .equals() method?
 - What is the Object class's function in the Java language?
 - What is a POJO?
 - What is method overloading?
 - What is method overriding?
 - What is type casting?
 - What are access modifiers?
 - List the access modifiers from most visible to least visible
 - What is the difference in visibility between protected and package-private access level?
 - What are some non-access modifying keywords used in Java?
 - What is the difference between an interface and an abstract class?
 - What is the purpose of the .finalize() method?
 - Is multiple inheritance supported in Java?
 - Can garbage collected be forced in Java?
 - What are packages used for?
 - What are imports?
 - What is the main method signature?
 - What property of a Java primitive array tells us the size of the array?
 - What are some constructs used in Java for flow control?
 - What is the difference between a while and a do-while loop?
 - What is the difference between a for loop and an enhanced for loop?
 - What is the difference between an exception and an error in Java?
 - What is the difference between a checked and an unchecked exception?
 - How can exceptions be handled in Java?
 - What is the purpose of the finally block?
 - Are you required to handle RuntimeExceptions?
 - Can exceptions be caught by multiple catch blocks in any order?
