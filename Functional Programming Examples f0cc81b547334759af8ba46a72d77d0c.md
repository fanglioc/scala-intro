# Functional Programming Examples

## Examples

Here are some concrete examples.

### Example 1

Here's an example of how functional programming can be used to implement a simple application that reads a list of integers from a file, sorts them in ascending order, and writes them back to the file.

First, we define a pure function `readIntegersFromFile` that takes a filename as input and returns a List of integers read from the file:

```
import scala.io.Source

def readIntegersFromFile(filename: String): List[Int] = {
  val source = Source.fromFile(filename)
  val lines = source.getLines.toList
  source.close()
  lines.map(_.toInt)
}

```

This function reads the contents of the file using Scala's `Source` class, converts each line to an integer using `map`, and returns the resulting List of integers.

Next, we define a higher-order function `sort` that takes a List of integers and a comparison function as input, and returns a sorted List of integers:

```
def sort(nums: List[Int], compare: (Int, Int) => Boolean): List[Int] = {
  nums.sortWith(compare)
}

```

This function uses Scala's built-in `sortWith` method to sort the List of integers according to the comparison function passed as input.

Finally, we define a function `writeIntegersToFile` that takes a filename and a List of integers as input and writes the integers to the file:

```
import java.io.PrintWriter

def writeIntegersToFile(filename: String, nums: List[Int]): Unit = {
  val pw = new PrintWriter(filename)
  nums.foreach(pw.println)
  pw.close()
}

```

This function creates a `PrintWriter` object that writes to the specified file, and then uses `foreach` to write each integer in the List to a new line in the file.

To use these functions to implement our application, we first read the integers from the input file using `readIntegersFromFile`, then sort them using the `sort` function with a simple comparison function that sorts in ascending order, and finally write the sorted integers back to the file using `writeIntegersToFile`:

```
val inputFile = "input.txt"
val outputFile = "output.txt"

val nums = readIntegersFromFile(inputFile)
val sortedNums = sort(nums, (a, b) => a < b)
writeIntegersToFile(outputFile, sortedNums)

```

This simple example illustrates how functional programming concepts can be applied to build efficient and maintainable applications in Scala.

### Example 2

Here's another example of functional programming with Scala:

Suppose we have a list of integers, and we want to perform a mathematical operation on each element of the list and then calculate the sum of the resulting values. We can do this using functional programming concepts in Scala.

First, we define a pure function `square` that takes an integer and returns its square:

```
def square(x: Int): Int = {
  x * x
}

```

Next, we define a higher-order function `map` that takes a List of integers and a function as input, and returns a new List that contains the result of applying the input function to each integer in the input List:

```
def map(nums: List[Int], f: Int => Int): List[Int] = {
  nums.map(f)
}

```

This function uses Scala's built-in `map` method to apply the input function `f` to each integer in the input List `nums`, and returns a new List containing the result.

Finally, we can use these functions to perform the mathematical operation on each element of the list and calculate the sum of the resulting values. Here's how we can do it:

```
val nums = List(1, 2, 3, 4, 5)

val squares = map(nums, square)

val sumOfSquares = squares.sum

```

In this code, we first define a List of integers `nums`. Then, we use the `map` function with `square` as the input function to apply `square` to each integer in the List, and return a new List containing the result. Finally, we use `sum` to calculate the sum of the resulting List of squared integers.

This example illustrates how functional programming concepts can be used to perform common mathematical operations on data structures such as Lists in a concise and expressive way in Scala.

### Example 3

Here's one more example of functional programming with Scala:

Suppose we have a list of strings, and we want to perform a filter operation to remove all the strings that contain a certain character, and then concatenate the remaining strings into a single string. We can do this using functional programming concepts in Scala.

First, we define a pure function `containsChar` that takes a character and a string as input, and returns true if the input string contains the input character:

```
def containsChar(c: Char, s: String): Boolean = {
  s.contains(c)
}

```

Next, we define a higher-order function `filter` that takes a List of strings and a predicate function as input, and returns a new List that contains only the elements of the input List that satisfy the input predicate:

```
def filter(strings: List[String], p: String => Boolean): List[String] = {
  strings.filter(p)
}

```

This function uses Scala's built-in `filter` method to apply the input predicate function `p` to each string in the input List `strings`, and returns a new List containing only the elements that satisfy the predicate.

Finally, we can use these functions to perform the filter operation and concatenate the remaining strings into a single string. Here's how we can do it:

```
val strings = List("hello", "world", "scala", "functional", "programming")

val filteredStrings = filter(strings, !containsChar(_, 'l'))

val result = filteredStrings.mkString(" ")

```

In this code, we first define a List of strings `strings`. Then, we use the `filter` function with a predicate function that removes all strings containing the character 'l' to create a new List `filteredStrings`. Finally, we use `mkString` to concatenate the remaining strings in `filteredStrings` into a single string.

This example illustrates how functional programming concepts such as pure functions, higher-order functions, and function composition can be used to solve complex problems in a concise and expressive way in Scala.

### Example 4

Here's another example of functional programming with Scala:

Suppose we have a list of tuples representing points in a 2D plane, and we want to calculate the distance between each pair of points. We can do this using functional programming concepts in Scala.

First, we define a pure function `distance` that takes two tuples representing points as input, and returns the Euclidean distance between the points:

```
def distance(p1: (Double, Double), p2: (Double, Double)): Double = {
  val dx = p1._1 - p2._1
  val dy = p1._2 - p2._2
  math.sqrt(dx * dx + dy * dy)
}

```

Next, we define a higher-order function `combinations` that takes a List of elements and returns a List of all possible pairs of elements in the input List:

```
def combinations[T](elements: List[T]): List[(T, T)] = {
  elements.flatMap(x => elements.map(y => (x, y))).filter(pair => pair._1 != pair._2)
}

```

This function uses Scala's built-in `flatMap` method to create a new List of pairs of elements by applying the input function `f` to each element in the input List `elements`, and then flattening the resulting List of Lists into a single List. The resulting List contains all possible pairs of elements in the input List.

Finally, we can use these functions to calculate the distance between each pair of points in the input List. Here's how we can do it:

```
val points = List((0.0, 0.0), (1.0, 1.0), (2.0, 2.0))

val pairs = combinations(points)

val distances = pairs.map(pair => distance(pair._1, pair._2))

```

In this code, we first define a List of tuples representing points in a 2D plane `points`. Then, we use the `combinations` function to create a new List `pairs` containing all possible pairs of points in `points`. Finally, we use `map` to apply the `distance` function to each pair of points in `pairs`, and return a new List `distances` containing the resulting distances.

This example illustrates how functional programming concepts can be used to solve complex problems involving data structures such as Lists of tuples in a concise and expressive way in Scala.

[Advanced Examples ](Functional%20Programming%20Examples.md)
