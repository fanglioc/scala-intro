# Intro to Scala Lang

# Intro to Scala Lang

Scala is a high-level, general-purpose programming language that was designed to be concise and expressive. It is a powerful language that is widely used for building scalable applications. In this tutorial, we will cover the basics of Scala for beginners.

## Installation

Before we can start coding in Scala, we need to install the Scala environment. Scala requires the Java Runtime Environment (JRE) to run, so we will need to download and install both the JRE and Scala.

### Steps to Install Scala

1. Download and install the latest version of the Java Runtime Environment (JRE) from the official website.
2. Download the latest version of Scala from the official website.
3. Extract the downloaded Scala archive to a directory of your choice.
4. Set the environment variable `PATH` to include the `bin` directory of the extracted Scala archive.

Once you have completed the installation, you can verify that Scala is installed correctly by opening a command prompt and typing `scala -version`.

## Basic Syntax

Scala syntax is very similar to Java syntax. However, Scala is a functional language, which means it has some additional features that are not present in Java. Here are some examples of basic Scala syntax:

### Hello World

```
object HelloWorld {
  def main(args: Array[String]) {
    println("Hello, world!")
  }
}

```

### Variables

In Scala, we can define variables using the `val` and `var` keywords.

```
val x = 10 // immutable variable
var y = 5 // mutable variable

```

### Functions

Functions are a key feature of Scala. Here is an example function that takes two integer arguments and returns their sum:

```
def add(x: Int, y: Int): Int = {
  x + y
}

```

### Classes

Scala is an object-oriented programming language, which means that it allows us to define classes. Here is an example class that represents a person:

```
class Person(name: String, age: Int) {
  def getName(): String = {
    return name
  }
  def getAge(): Int = {
    return age
  }
}

```

## Collections

Scala provides a set of collection classes that are used to store and manipulate data. Here are some examples of collection classes:

### Arrays

Arrays can be defined using the `Array` keyword.

```
val arr = Array(1, 2, 3, 4, 5)

```

### Lists

Lists are another common collection class in Scala.

```
val myList = List(1, 2, 3, 4, 5)

```

### Maps

Maps are used to store key-value pairs.

```
val myMap = Map("John" -> 25, "Jane" -> 30)

```

### Advanced Topics

Scala also has several advanced features that can make it even more powerful for certain use cases. Some of these features include:

- Type inference: Scala can often infer the type of a variable based on its value, which can make code more concise and readable.
- Higher-order functions: Scala allows functions to take other functions as arguments, which can make code more flexible and reusable.
- Pattern matching: Scala has a powerful pattern matching syntax that can be used to match complex data structures and perform different actions based on the structure of the data.
- Futures and Promises: These are used for asynchronous programming.
- Akka: Akka is a toolkit used for building highly concurrent, distributed, and fault-tolerant systems.

By mastering these advanced features, you can become a more proficient Scala programmer and take advantage of its full potential.

---

## Examples

### Example 1

Here is an example program that calculates the factorial of a number in Scala:

```
object Factorial {
  def main(args: Array[String]) {
    val num = 5
    val result = factorial(num)
    println(s"Factorial of $num = $result")
  }

  def factorial(num: Int): Int = {
    if (num <= 1) 1
    else num * factorial(num - 1)
  }
}

```

This program defines a function called `factorial` that recursively calculates the factorial of a given number. The program then calls this function with the value 5 and prints the result.

When you run this program, you should see the following output:

```
Factorial of 5 = 120

```

This is just a simple example, but it demonstrates some of the basic features of Scala, such as defining functions and calling them with arguments. With a little more practice, you can learn to write more complex programs in Scala that take advantage of its advanced features.

### Example 2

Here is an example program that reads a file and counts the number of occurrences of each word:

```
import scala.io.Source

object WordCount {
  def main(args: Array[String]) {
    val filename = "example.txt"
    val lines = Source.fromFile(filename).getLines().toList
    val words = lines.flatMap(_.split("\\\\W+"))
    val wordCounts = words.groupBy(identity).mapValues(_.size)
    wordCounts.foreach(println)
  }
}

```

This program reads the contents of the file `example.txt` and splits it into words. It then counts the number of occurrences of each word and prints the results.

When you run this program with a file containing text, you should see output that looks something like this:

```
(hello,1)
(world,1)
(this,2)
(is,2)
(an,1)
(example,1)
(of,3)
(text,1)
(file,1)
)

```

This program demonstrates some of the advanced features of Scala, such as working with files, using higher-order functions, and using collections to manipulate data. With these features, you can write powerful and flexible programs in Scala that can handle a wide range of tasks.

### Example 3

Here is an example program that calculates the average of a list of numbers in Scala:

```
object Average {
  def main(args: Array[String]) {
    val numbers = List(1, 2, 3, 4, 5)
    val result = average(numbers)
    println(s"Average of $numbers = $result")
  }

  def average(numbers: List[Int]): Double = {
    numbers.sum.toDouble / numbers.length.toDouble
  }
}

```

This program defines a function called `average` that calculates the average of a given list of numbers. The program then calls this function with a list of numbers and prints the result.

When you run this program, you should see the following output:

```
Average of List(1, 2, 3, 4, 5) = 3.0

```

This is a simple example, but it demonstrates some of the basic features of Scala, such as defining functions and working with collections. With these tools, you can write code that is both concise and expressive, making it easier to read and understand.

### Example 4

Scala is a language that supports object-oriented programming, so it allows us to define classes and objects. Here's an example class that represents a car:

```
class Car(val make: String, val model: String, var year: Int) {
  def startEngine(): Unit = {
    println("Starting engine...")
  }
  def stopEngine(): Unit = {
    println("Stopping engine...")
  }
  def getAge(): Int = {
    val currentYear = java.time.Year.now.getValue
    currentYear - year
  }
}

```

This class has three fields (`make`, `model`, and `year`) and three methods (`startEngine`, `stopEngine`, and `getAge`). The `startEngine` and `stopEngine` methods simply print out messages to indicate that the engine is starting or stopping. The `getAge` method calculates the age of the car based on the current year and the year it was manufactured.

To create an instance of the `Car` class, we can use the `new` keyword:

```
val myCar = new Car("Toyota", "Corolla", 2010)

```

This creates a new instance of the `Car` class with the specified make, model, and year. We can then call the methods of the `Car` class on this instance:

```
myCar.startEngine()
myCar.stopEngine()
println(s"My car is ${myCar.getAge()} years old.")

```

This will output:

```
Starting engine...
Stopping engine...
My car is 11 years old.

```

This is just a simple example, but it demonstrates the basics of object-oriented programming in Scala. With these tools, you can define complex classes and objects that can be used to build powerful and flexible applications.
