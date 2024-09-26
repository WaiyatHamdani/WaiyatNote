## Table of Contents
- [Basic Syntax](#basic-syntax)
- [Variables](#variables)
- [Data Types](#data-types)
- [String Interpolation](#string-interpolation)
- [Control Structures](#control-structures)
- [Functions](#functions)
- [Null Safety](#null-safety)
- [Classes](#classes)
- [Collections](#collections)
- [Coroutines](#coroutines)

## Basic Syntax
Kotlin almost like java but instead of System.out.println Kotlin only println
```kotlin
fun main() {
    println("Hello, World!")
}
```

## Variables
- val: Immutable (like final in Java).
- var: Mutable.  (can be change).

```kotlin
val name = "Yuqi"  // Immutable
var age = 28       // Mutable
```


## Data Types
Kotlin basic datatype:
- Int for integers
- Double for floating-point numbers
- String for text
- Boolean for true/false values

Kotlin can automatically specify datatype but you can actually do it like this 
```kotlin
val age: Int = 30
var height: Double = 1.75
val firstname: String = "Waiyat"
```
Kotlin does not require semicolons at the end of statements. However, you can still use them if you want!!

## String Interpolation
Kotlin supports string interpolation, allowing you to insert variables into strings.
```kotlin
val name = "Waiyat"
println("Hello, $name!")  // Output: Hello, Waiyat!

val age = 25
println("You are ${age + 5} years old.")  // Output: You are 30 years old.
```



## Control Structures
Kotlin's control flow statements :
- if 
- when ( this is like switch statement in java) 
- for 
- while

### if
```kotlin
val x = 20
val y = 18
if (x > y) {
  println("x is greater than y")
}else{
    println("y greater than x")
}

// or if can also return a value
val max = if (x > y) x else y
println("The greater value is $max")
```
### when 
```kotlin
val day = 3
val result = when(day) {
    1 -> "Monday"
    2 -> "Tuesday"
    3 -> "Wednesday"
    else -> "Invalid day"
}
println(result) // Output: Wednesday
```
### for
```kotlin
val nums = arrayOf(1, 5, 10, 15, 20)
for (x in nums) {
  println(x)
}
```
### while
```kotlin
var i = 0
while (i < 5) {
  println(i)
  i++
} 
```



## function
- Functions are declared with the fun keyword, and you can specify return types.
```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}

val sum = add(5, 10)
println(sum)  // Output: 15
```
- Single-expression functions
```kotlin
fun multiply(a: Int, b: Int) = a * b
```

## Null Safety
Kotlin’s most important features is its null safety. What is that mean ?
- variables cannot be null by default unless explicitly allowed using "?"
```kotlin
var name: String = "Waiyat"  // Non-nullable
// name = null  // This will cause a compilation error

var nullableName: String? = "Hamdani"  // Nullable
nullableName = null  // This is allowed
```

## Classes
- Kotlin syntax for defining classes and constructors.
```kotlin
class Person(val name: String, var age: Int) {
    fun sayHello() {
        println("Hello, my name is $name, and I am $age years old.")
    }
}

val person = Person("Waiyat", 30)
person.sayHello()  // Output: Hello, my name is Waiyat, and I am 30 years old.
```
- Data Classes: Kotlin provides data class to hold data, and it automatically generates useful methods like toString(), equals(), hashCode(), and copy().
```kotlin
data class User(val name: String, val age: Int)

val user = User("Waiyat", 30)
println(user)  // Output: User(name=Waiyat, age=30)
```


## Collections
Colection in Kotlin:
- List : immutable and mutable list
```kotlin
//imutable
val items = listOf("apple", "banana", "cherry")
println(items[0])  // Output: apple

// mutable 
val mutableItems = mutableListOf("apple", "banana")
mutableItems.add("cherry")
println(mutableItems)  // Output: [apple, banana, cherry]

```

- Set : immutable and mutalbe
```kotlin
// Immutable set (read-only)
val fruits = setOf("apple", "banana", "apple")  // Duplicate "apple" will be ignored
println(fruits)  // Output: [apple, banana]

// Mutable set (modifiable)
val mutableFruits = mutableSetOf("apple", "banana")
mutableFruits.add("cherry")
println(mutableFruits)  // Output: [apple, banana, cherry]
```

- Map : immutable and mutalbe
```kotlin
// Immutable map (read-only)
val countryCapitals = mapOf("France" to "Paris", "Germany" to "Berlin")
println(countryCapitals["France"])  // Output: Paris

// or you can use pair
val myMap: Map<String, Int> = mapOf(
    Pair("One", 1),
    Pair("Two", 2),
    Pair("Three", 3)
)


// Mutable map (modifiable)
val mutableCountryCapitals = mutableMapOf("France" to "Paris", "Germany" to "Berlin")
mutableCountryCapitals["USA"] = "Washington"
println(mutableCountryCapitals)  // Output: {France=Paris, Germany=Berlin, USA=Washington}
```

## Coroutines
coroutines are used for asynchronous programming. A coroutine allows you to write code that performs tasks asynchronously without blocking threads, making it more efficient than traditional approaches.

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello,")
}
```