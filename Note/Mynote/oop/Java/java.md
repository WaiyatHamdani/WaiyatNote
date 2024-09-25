## Table of Contents
- [Primitive Data Types](#primitive-data-types)
- [Conditional Statements](#conditional-statements)
- [Loops](#loops)
- [Methods](#methods)
- [Try-Catch](#try-catch)
- [Class and Objects](#class-and-objects)
- [Array](#array)
- [Stringbuilder](#stringbuilder)
- [String Methods](#string-methods)
- [Type Conversions](#type-conversions)
- [Scanner](#scanner)
- [Collections](#collections)

## Primitive Data Types
Java has several primitive data types:
- 
```java
// Primitive data types
int age = 23; 
char gender = 'F'; 
boolean isActive = true; 
double height = 1.65; 
```

## Conditional Statements
```java
// Conditional statement
if (isActive) {
    System.out.println("Yuqi is actively promoting.");
} else {
    System.out.println("Yuqi is currently on a break.");
}
```

## Loops
```java
// Using a loop to print Yuqi's stage name 5 times
for (int i = 0; i < 5; i++) {
    System.out.println("Yuqi");
}
// Using the enhanced iterate over the array/list
for (String x : idols) {
    System.out.println("Idol: " + x);
}
```

## Methods
```java
public class Idol {
    // Method without paramater
    public void greet() {
        System.out.println("Hello, I'm Yuqi!");
    }
    // Method with parameters
    public void introduce(String group, int age) {
        System.out.println("I am Yuqi from " + group + ", and I am " + age + " years old.");
    }
}
```

## Try-Catch
```java
//---------------try catch begin here -----------------------

try {
    String[] idols = {"Yuqi", "Minnie"};
    System.out.println(idols[2]); // This will throw an ArrayIndexOutOfBoundsException
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Error: No idol at this index.");
}
//--------------- try catch end here-------------------------

//---------------try catch with resource begin here -----------------------

try (BufferedReader reader = new BufferedReader(new FileReader("yuqi.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    System.out.println("Error reading the file.");
}

//---------------try catch with resource end here -----------------------
```

## Class and Objects
```java
public class Idol {
    // Properties
    private String name;
    private String group;

    // Constructor
    public Idol(String name, String group) {
        this.name = name;
        this.group = group;
    }

    // Method to display info
    public void displayInfo() {
        System.out.println(name + " is a member of " + group);
    }

    public static void main(String[] args) {
        Idol yuqi = new Idol("Yuqi", "(G)I-DLE");
        yuqi.displayInfo(); 
    }
}
```

## Array
```java
// Declare an array with a fixed size of 5
String[] idols = new String[5];

// Insert data into the array
idols[0] = "Yuqi";
idols[1] = "Minnie";
idols[2] = "Soyeon";
idols[3] = "Miyeon";
idols[4] = "Shuhua";

// Array with initial value 
String[] Gidle = {"Yuqi", "Minnie", "Soyeon", "Miyeon", "Shuhua"};
```
## Stringbuilder
```java
StringBuilder sb = new StringBuilder("Yuqi");
    sb.append(" - (G)I-DLE");
    sb.insert(0, "Idol: ");
    sb.replace(5, 9, "Yuki");
    sb.deleteCharAt(0); // Removes 'I' in "Idol: "
System.out.println(sb.toString()); // Output: "dol: Yuki - (G)I-DLE"
```
## String Methods
```java
String idol = "  Yuqi  ";
    System.out.println(idol.trim());          // "Yuqi"
    System.out.println(idol.toUpperCase());   // "  YUQI  "
    System.out.println(idol.toLowerCase());   // "  yuqi  "
    System.out.println(idol.length());        // 7 (includes spaces)
    System.out.println(idol.substring(2, 5)); // "Yuq"
    System.out.println(idol.contains("qi"));  // true
    System.out.println(idol.replace(" ", "_")); // "__Yuqi__"
```

## Type Conversions
```java
//String to Other Data Types
int age = Integer.parseInt("32"); // String to int
double height = Double.parseDouble("1.65"); // String to double

//Other Data Types to String
String ageStr = Integer.toString("32"); // int to String
String heightStr = String.valueOf("1.65"); // double to String
```

## Scanner
```java
Scanner scanner = new Scanner(System.in);
System.out.print("Enter idol's name: ");
String name = scanner.nextLine();
System.out.print("Enter idol's age: ");
int age = scanner.nextInt();
System.out.println("Idol: " + name + ", Age: " + age);
```

## Collections
the most collection that i use :
- Arraylist :
    - add(E e)
    - add(int index, E element)
    - get(int index)
    - set(int index, E element)
    - remove(int index)
    - remove(Object o)
    - size()
    - contains(Object o)
    - clear()
    - isEmpty()
- HashMap :
    - put(K key, V value)
    - get(Object key)
    - remove(Object key)
    - containsKey(Object key)
    - containsValue(Object value)
    - size()
    - clear()
    - isEmpty()
    - keySet()
    - values()
- HashSet :
    - add(E e)
    - remove(Object o)
    - contains(Object o)
    - size()
    - clear()
    - isEmpty()
    - iterator()


```java
// Arraylist (add() , )
import java.util.ArrayList;
ArrayList<String> idols = new ArrayList<>();

//HashMap
import java.util.HashMap;
HashMap<String, String> idolMap = new HashMap<>();

//HashSet
import java.util.HashSet;
HashSet<String> idolSet = new HashSet<>();
```