# Advanced Examples

# Tutorial on Advanced Scala Code

Scala is a high-level programming language that was created to be both object-oriented and functional. It is designed to be concise, expressive, and powerful, and it has become a popular language for developing applications in various domains, from web development to big data processing.

In this document, we will explore some advanced Scala code, including classes, functions, collections, and more. We will begin with an overview of Scala's class and object model, and then we will dive into the details of Scala's functional programming features and collection classes.

## Classes and Objects

Scala is an object-oriented language, which means that everything in Scala is an object, including primitive types like `Int` and `Boolean`. Scala also supports functional programming, which means that functions are first-class citizens and can be passed as arguments, returned as results, and composed together.

Scala's class and object model is designed to be simple and flexible. In Scala, we can define a class using the `class` keyword, and we can define an object using the `object` keyword. Classes can have fields, methods, and constructors, and objects can have fields, methods, and singletons.

```
class Person(name: String) {
  def apply(age: Int) = println(s"I have aged $age years")
}

val bob = new Person("Bob")
bob.apply(43)
bob(43) // INVOKING bob as a function === bob.apply(43)

```

In the above example, we defined a class `Person` that takes a single argument `name` and has a method `apply` that takes an `age` argument and prints a message indicating that the person has aged by that amount. We then created an instance of this class named `bob` and invoked the `apply` method on it with an argument of `43`. In Scala, we can also invoke an object as if it were a function, so we can write `bob(43)` instead of `bob.apply(43)`.

## Functions

Scala is a functional programming language, which means that functions are first-class citizens. We can compose functions, pass them as arguments, and return them as results. In Scala, all functions are instances of a `FunctionX` type, where `X` is the number of arguments the function takes.

We can define a function that increments its argument by 1 using a `Function1` type. This type takes a single argument, `arg`, and returns an integer.

```
val simpleIncrementer = new Function1[Int, Int] {
  override def apply(arg: Int): Int = arg + 1
}

simpleIncrementer.apply(23) // 24
simpleIncrementer(23) // simpleIncrementer.apply(23)

```

We can also define functions that take multiple arguments by using `Function2`, `Function3`, and so on. In the following example, we define a function that concatenates two strings.

```
val stringConcatenator = new Function2[String, String, String] {
  override def apply(arg1: String, arg2: String): String = arg1 + arg2
}

stringConcatenator("I love", " Scala") // "I love Scala"

```

Scala provides syntax sugars for defining functions, such as the following function that doubles its argument.

```
val doubler: Int => Int = (x: Int) => 2 * x
doubler(4) // 8

```

We can also define higher-order functions that take functions as arguments or return functions as results. In the following example, we use the `map`, `flatMap`, and `filter` functions to transform and filter a list.

```
val aMappedList: List[Int] = List(1,2,3).map(x => x + 1) // HOF
val aFlatMappedList = List(1,2,3).flatMap { x =>
  List(x, 2 * x)
} // alternative syntax, same as .flatMap(x => List(x, 2 * x))
val aFilteredList = List(1,2,3,4,5).filter(_ <= 3) // equivalent to x => x <= 3

```

We can also use for comprehensions as an alternative syntax for chaining map and flatMap operations.

```
val alternativePairs = for {
  number <- List(1,2,3)
  letter <- List('a', 'b', 'c')
} yield s"$number-$letter"
// equivalent to the map/flatMap chain above

```

## Collections

Scala provides a rich set of collection classes, including lists, sequences, vectors, sets, ranges, tuples, and maps.

We can create and manipulate lists using the `List` class. For example, we can create a list, access its first element and tail, prepend an element, and append an element.

```
val aList = List(1,2,3,4,5)
val firstElement = aList.head
val rest = aList.tail
val aPrependedList = 0 :: aList // List(0,1,2,3,4,5)
val anExtendedList = 0 +: aList :+ 6 // List(0,1,2,3,4,5,6)

```

Sequences are similar to lists, but they can be implemented differently. We can create a sequence and access its elements using the same syntax as lists.

```
val aSequence: Seq[Int] = Seq(1,2,3)
val accessedElement = aSequence(1) // the element at index 1: 2

```

Vectors are a fast implementation of sequences, optimized for random access.

```
val aVector = Vector(1,2,3,4,5)

```

Sets are collections that do not contain duplicates. We can create a set, check if it contains an element, add an element, and remove an element.

```
val aSet = Set(1,2,3,4,1,2,3) // Set(1,2,3,4)
val setHas5 = aSet.contains(5) // false
val anAddedSet = aSet + 5 // Set(1,2,3,4,5)
val aRemovedSet = aSet - 3 // Set(1,2,4)

```

Ranges are collections of numeric values. We can create a range and transform its elements using the `map` function.

```
val aRange = 1 to 1000
val twoByTwo = aRange.map(x => 2 * x).toList // List(2,4,6,8..., 2000)

```

Tuples are groups of values under the same value. We can create a tuple and access its elements using the `._1`, `._2`, and so on syntax.

```
val aTuple = ("Bon Jovi", "Rock", 1982)

```

Maps are collections of key-value pairs. We can create a map, access its values using keys, add a pair, and remove a pair.

```
val aPhonebook: Map[String, Int] = Map(
  ("Daniel", 6437812),
  "Jane" -> 327285 // ("Jane", 327285)
)

```

## Pattern Matching

Pattern matching is a powerful feature of Scala that allows us to match a value against a set of patterns and execute code based on the matched pattern. Pattern matching can be used with any data type in Scala, including primitive types, objects, and collections.

```
val aNumber = 3
val matchedNumber = aNumber match {
  case 1 => "one"
  case 2 => "two"
  case _ => "other number"
}

```

In the example above, we define a variable `aNumber` with a value of `3`. We then use pattern matching to match this value against three patterns. If `aNumber` matches `1`, we return the string `"one"`. If `aNumber` matches `2`, we return the string `"two"`. If `aNumber` does not match `1` or `2`, we return the string `"other number"`. In this case, `aNumber` matches the `_` pattern, which is a wildcard pattern that matches any value.
