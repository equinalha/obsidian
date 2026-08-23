---
Verification: unverified
Tags: []
Last edited time: 2024-02-21T15:44:00
Owner:
  - Eduardo Quinalha
---
[https://bit.ly/443k9Kn](https://bit.ly/443k9Kn)

Java 8 is the most awaited release of Java programming language development because, in the entire history of Java, it never release that many major features. It consists of major features of Java. It is a new version of Java and was released by Oracle on 18 March 2014. Java provided support for functional programming, new Java 8 APIs, a new JavaScript engine, new Java 8 streaming API, functional interfaces, default methods, date-time API changes, etc.

![[Java-8-Tutorial.webp]]

This Tutorial covers all the important Java 8 features like Java 8 APIs, Java arrays, Java 8 ArrayList, and many more included in Java 8 programming language.

## Java 8 Features

- [Lambda Expressions](https://www.geeksforgeeks.org/java-8-features/#lambda)
- [Functional Interfaces](https://www.geeksforgeeks.org/java-8-features/#functional)
- [Method Reference](https://www.geeksforgeeks.org/java-8-features/#reference)
- [Streams](https://www.geeksforgeeks.org/java-8-features/#streams)
- [Comparable and Comparator](https://www.geeksforgeeks.org/java-8-features/#comp)
- [Optional Class](https://www.geeksforgeeks.org/java-8-features/#optional)
- [Date/Time API](https://www.geeksforgeeks.org/java-8-features/#datetime)
- [Miscellaneous](https://www.geeksforgeeks.org/java-8-features/#misc)

## Lambda Expressions

Lambda Expression basically expresses an instance of the functional interface, in other words, you can say it provides a clear and concise way to represent a method of the functional interface using an expression. Lambda Expressions are added in Java 8.

- [Lambda Expressions in Java 8](https://www.geeksforgeeks.org/lambda-expressions-java-8/)
- [Lambda Expressions Parameters](https://www.geeksforgeeks.org/java-lambda-expressions-parameters/)
- [Java Lambda Expression with Collections](https://www.geeksforgeeks.org/java-lambda-expression-with-collections/)
- [Lambda Expression Variable Capturing with Examples](https://www.geeksforgeeks.org/java-lambda-expression-variable-capturing-with-examples/)
- [How to Create Thread using Lambda Expressions in Java?](https://www.geeksforgeeks.org/how-to-create-thread-using-lambda-expressions-in-java/)
- [Serialization of Lambda Expression in Java](https://www.geeksforgeeks.org/serialization-of-lambda-expression-in-java/)
- [Block Lambda Expressions in Java](https://www.geeksforgeeks.org/block-lambda-expressions-in-java/)
- [Match Lambdas to Interfaces in Java](https://www.geeksforgeeks.org/match-lambdas-to-interfaces-in-java/)
- [Converting ArrayList to HashMap in Java 8 using a Lambda Expression](https://www.geeksforgeeks.org/converting-arraylist-to-hashmap-in-java-8-using-a-lambda-expression/)
- [Check if a String Contains Only Alphabets in Java Using Lambda Expression](https://www.geeksforgeeks.org/check-if-a-string-contains-only-alphabets-in-java-using-lambda-expression/)
- [Remove Elements From a List that Satisfy a Given Predicate in Java](https://www.geeksforgeeks.org/remove-elements-from-a-list-that-satisfy-given-predicate-in-java/)

## Functional Interfaces

An interface that contains only one abstract method is known as a functional interface, but there is no restriction, you can have **n **number of default and static methods inside a functional interface.

- [Functional Interfaces in Java](https://www.geeksforgeeks.org/functional-interfaces-java/)
- [Consumer Interface in Java with Examples](https://www.geeksforgeeks.org/java-8-consumer-interface-in-java-with-examples/)
- [BiConsumer Interface in Java with Examples](https://www.geeksforgeeks.org/java-8-biconsumer-interface-in-java-with-examples/)
- [Predicate Interface with Examples](https://www.geeksforgeeks.org/java-8-predicate-with-examples/)
- [Function Interface in Java with Examples](https://www.geeksforgeeks.org/function-interface-in-java-with-examples/)
- [Supplier Interface in Java with Examples](https://www.geeksforgeeks.org/supplier-interface-in-java-with-examples/)

## Method Reference

Method reference is a shorthand notation of a lambda expression to call a method. There are four types of method references that are as follows:

- Static Method Reference
- Instance Method Reference of a particular object
- Instance Method Reference of an arbitrary object of a particular type
- Constructor Reference.

**Example:**

```plain text
numList.stream().filter(n -> n > 5).sorted().forEach(System.out::println);
```

- [Method References in Java with examples](https://www.geeksforgeeks.org/method-references-in-java-with-examples/)
- [Converting ArrayList to HashMap using Method Reference in Java 8](https://www.geeksforgeeks.org/converting-arraylist-to-hashmap-using-method-reference-in-java-8/)

## Streams

Stream API is introduced in Java 8 and is used to process collections of objects with the functional style of coding using the lambda expression. So to understand what stream API is, you must have knowledge of both lambda and functional interfaces.

- [Java 8 Stream](https://www.geeksforgeeks.org/java-8-stream-tutorial/)
- [Difference Between Streams and Collections in Java](https://www.geeksforgeeks.org/difference-between-streams-and-collections-in-java/)
- [Implement Filter Function using Reduce in Java 8 Streams](https://www.geeksforgeeks.org/implement-filter-function-using-reduce-in-java-8-streams/)
- [Java Stream API – Filters](https://www.geeksforgeeks.org/java-stream-api-filters/)
- [Parallel vs Sequential Stream in Java](https://www.geeksforgeeks.org/parallel-vs-sequential-stream-in-java/)
- [Functional Programming in Java 8+ using the Stream API with Example](https://www.geeksforgeeks.org/functional-programming-in-java-8-using-the-stream-api-with-example/)
- [Intermediate Methods of Stream in Java](https://www.geeksforgeeks.org/intermediate-methods-of-stream-in-java/)
- [Difference Between map() And flatMap() In Java Stream](https://www.geeksforgeeks.org/difference-between-map-and-flatmap-in-java-stream/)
- [Array to Stream in Java](https://www.geeksforgeeks.org/array-stream-java/)
- [10 Ways to Create a Stream in Java](https://www.geeksforgeeks.org/10-ways-to-create-a-stream-in-java/)
- [How to Print Elements of a Stream in Java 8](https://www.geeksforgeeks.org/how-to-print-elements-of-a-stream-in-java-8/)
- [Collecting a Stream to an Immutable Collection in Java](https://www.geeksforgeeks.org/collecting-a-stream-to-an-immutable-collection-in-java/)
- [Comparing Streams to Loops in Java](https://www.geeksforgeeks.org/comparing-streams-to-loops-in-java/)
- [Why You Need to Close the Java Streams in Finally Block?](https://www.geeksforgeeks.org/why-you-need-to-close-the-java-streams-in-finally-block/)
- [Convert an Iterable to Stream in Java](https://www.geeksforgeeks.org/convert-an-iterable-to-stream-in-java/)
- [Convert an Iterator to Stream in Java](https://www.geeksforgeeks.org/convert-an-iterator-to-stream-in-java/)
- [Difference Between Stream.of() and Arrays.stream() method in Java](https://www.geeksforgeeks.org/difference-between-stream-of-and-arrays-stream-method-in-java/)
- [Convert Stream to Set in Java](https://www.geeksforgeeks.org/convert-stream-set-java/)
- [Convert a Set to Stream in Java](https://www.geeksforgeeks.org/convert-set-stream-java/)
- [Streams on Arrays in Java 8](https://www.geeksforgeeks.org/streams-arrays-java-8/)

## Java Stream Programs

- [Program to Convert a Map to a Stream in Java](https://www.geeksforgeeks.org/program-to-convert-a-map-to-a-stream-in-java/)
- [Program to Convert Boxed Array to Stream in Java](https://www.geeksforgeeks.org/program-to-convert-boxed-array-to-stream-in-java/)
- [Program to Convert Primitive Array to Stream in Java](https://www.geeksforgeeks.org/program-to-convert-primitive-array-to-stream-in-java/)
- [Program to Convert a Set to Stream in Java using Generics](https://www.geeksforgeeks.org/program-to-convert-a-set-to-stream-in-java-using-generics/)
- [Program to Convert List to Stream in Java](https://www.geeksforgeeks.org/program-to-convert-list-to-stream-in-java/)
- [Program to Convert Stream to an Array in Java](https://www.geeksforgeeks.org/program-to-convert-stream-to-an-array-in-java/)
- [How to get Slice of a Stream in Java](https://www.geeksforgeeks.org/how-to-get-slice-of-a-stream-in-java/)
- [Flattening Nested Collections in Java](https://www.geeksforgeeks.org/flattening-nested-collections-in-java/)
- [How to Convert a Stream into a Map in Java](https://www.geeksforgeeks.org/how-to-convert-a-stream-into-a-map-in-java/)
- [Find the First Element of a Stream in Java](https://www.geeksforgeeks.org/find-the-first-element-of-a-stream-in-java/)
- [Find the Last Element of a Stream in Java](https://www.geeksforgeeks.org/find-the-last-element-of-a-stream-in-java/)
- [How to Find Duplicate Elements in a Stream in Java](https://www.geeksforgeeks.org/how-to-find-duplicate-elements-in-a-stream-in-java/)
- [Count the Occurrence of a Given Character in a String Using Stream API in Java](https://www.geeksforgeeks.org/count-occurrence-of-a-given-character-in-a-string-using-stream-api-in-java/)
- [Reverse Elements of a Parallel Stream in Java](https://www.geeksforgeeks.org/reverse-elements-of-a-parallel-stream-in-java/)
- [How to Get ArrayList From Stream in Java 8](https://www.geeksforgeeks.org/how-to-get-arraylist-from-stream-in-java-8/)
- [Generate Infinite Stream of Double in Java](https://www.geeksforgeeks.org/generate-infinite-stream-of-double-in-java/)
- [Generate Infinite Stream of Integers in Java](https://www.geeksforgeeks.org/generate-infinite-stream-of-integers-in-java/)
- [Program to Iterate over a Stream with Indices in Java 8](https://www.geeksforgeeks.org/program-to-iterate-over-a-stream-with-indices-in-java-8/)
- [Flatten a Stream of Arrays in Java using forEach loop](https://www.geeksforgeeks.org/flatten-a-stream-of-arrays-in-java-using-foreach-loop/)
- [Flatten a Stream of Lists in Java using forEach loop](https://www.geeksforgeeks.org/flatten-a-stream-of-lists-in-java-using-foreach-loop/)
- [Flatten a Stream of Map in Java using forEach loop](https://www.geeksforgeeks.org/flatten-a-stream-of-map-in-java-using-foreach-loop/)
- [Convert a String to a List of Characters in Java](https://www.geeksforgeeks.org/convert-a-string-to-a-list-of-characters-in-java/)
- [Initialize a List in a Single Line with a Specified Value using Java Stream](https://www.geeksforgeeks.org/initialize-a-list-in-a-single-line-with-a-specified-value-using-java-stream/)

## Java Stream Methods

- [Stream forEach() method in Java with Examples](https://www.geeksforgeeks.org/stream-foreach-method-java-examples/)
- [Stream forEachOrdered() Method in Java with Examples](https://www.geeksforgeeks.org/stream-foreachordered-method-java-examples/)
- [foreach() loop vs Stream foreach() vs Parallel Stream foreach()](https://www.geeksforgeeks.org/foreach-loop-vs-stream-foreach-vs-parallel-stream-foreach/)
- [Stream of() method in Java](https://www.geeksforgeeks.org/stream-of-method-in-java/)
- [Java Stream findAny() with Examples](https://www.geeksforgeeks.org/java-stream-findany-with-examples/)
- [Stream anyMatch() in Java with Examples](https://www.geeksforgeeks.org/stream-anymatch-java-examples/)
- [Stream allMatch() in Java with Examples](https://www.geeksforgeeks.org/stream-allmatch-java-examples/)
- [Stream filter() in Java with Examples](https://www.geeksforgeeks.org/stream-filter-java-examples/)
- [Stream sorted (Comparator comparator) Method in Java](https://www.geeksforgeeks.org/stream-sorted-comparator-comparator-method-java/)
- [Stream sorted() in Java](https://www.geeksforgeeks.org/stream-sorted-in-java/)
- [Stream.distinct() in Java](https://www.geeksforgeeks.org/stream-distinct-java/)
- [Stream.concat() in Java](https://www.geeksforgeeks.org/stream-concat-java/)
- [Stream.reduce() in Java with Examples](https://www.geeksforgeeks.org/stream-reduce-java-examples/)
- [stream.limit() method in Java](https://www.geeksforgeeks.org/stream-limit-method-in-java/)
- [Stream ofNullable(T) method in Java with Examples](https://www.geeksforgeeks.org/stream-ofnullablet-method-in-java-with-examples/)
- [Stream dropWhile() method in Java with Examples](https://www.geeksforgeeks.org/stream-dropwhile-method-in-java-with-examples/)
- [Stream iterate(T,Predicate,UnaryOperator) Method in Java with Examples](https://www.geeksforgeeks.org/stream-iteratetpredicateunaryoperator-method-in-java-with-examples/)
- [Stream takeWhile() method in Java with Examples](https://www.geeksforgeeks.org/stream-takewhile-method-in-java-with-examples/)
- [concat() Method of Stream Interface in Java API](https://www.geeksforgeeks.org/concat-method-of-stream-interface-in-java-api/)
- [Stream findFirst() in Java with Examples](https://www.geeksforgeeks.org/stream-findfirst-java-examples/)
- [DoubleStream mapToObj() in Java](https://www.geeksforgeeks.org/doublestream-maptoobj-in-java/)
- [Stream.Builder accept() Method in Java](https://www.geeksforgeeks.org/stream-builder-accept-method-in-java/)
- [IntStream.Builder add() Method in Java](https://www.geeksforgeeks.org/intstream-builder-add-method-in-java/)
- [DoubleStream.Builder build() in Java](https://www.geeksforgeeks.org/doublestream-builder-build-in-java/)
- [Stream.Builder build() in Java](https://www.geeksforgeeks.org/stream-builder-java-examples/)
- [Collectors.joining() Method with Examples](https://www.geeksforgeeks.org/java-8-streams-collectors-joining-method-with-examples/)
- [Stream builder() in Java with Examples](https://www.geeksforgeeks.org/stream-builder-java-examples/)
- [Stream empty() in Java with Examples](https://www.geeksforgeeks.org/stream-empty-java-examples/)
- [LongStream flatMap(LongFunction mapper) in Java](https://www.geeksforgeeks.org/longstream-flatmaplongfunction-mapper-java/)
- [LongStream filter() in Java with Examples](https://www.geeksforgeeks.org/longstream-filter-java-examples/)

## Comparable and Comparator

- [Comparable vs Comparator in Java](https://www.geeksforgeeks.org/comparable-vs-comparator-in-java/)
- [Comparator Interface in Java with Examples](https://www.geeksforgeeks.org/comparator-interface-java/)
- [Why to Use Comparator Interface Rather than Comparable Interface in Java?](https://www.geeksforgeeks.org/why-to-use-comparator-interface-rather-than-comparable-interface-in-java/)
- [Sort an Array of Triplet using Java Comparable and Comparator](https://www.geeksforgeeks.org/sort-an-array-of-triplet-using-java-comparable-and-comparator/)
- [Java Program to Sort LinkedList using Comparable](https://www.geeksforgeeks.org/java-program-to-sort-linkedlist-using-comparable/)
- [How to Sort HashSet Elements using Comparable Interface in Java?](https://www.geeksforgeeks.org/how-to-sort-hashset-elements-using-comparable-interface-in-java/)
- [Sort LinkedHashMap by Values using Comparable Interface in Java](https://www.geeksforgeeks.org/sort-linkedhashmap-by-values-using-comparable-interface-in-java/)
- [Sort LinkedHashMap by Keys using Comparable Interface in Java](https://www.geeksforgeeks.org/sort-linkedhashmap-by-keys-using-comparable-interface-in-java/)
- [How to Sort LinkedHashSet Elements using Comparable Interface in Java?](https://www.geeksforgeeks.org/how-to-sort-linkedhashset-elements-using-comparable-interface-in-java/)

## Optional Class

- [Java 8 Optional Class](https://www.geeksforgeeks.org/java-8-optional-class/)
- [Optional ofNullable() Method in Java with Examples](https://www.geeksforgeeks.org/optional-ofnullable-method-in-java-with-examples/)
- [Optional orElse() Method in Java with Examples](https://www.geeksforgeeks.org/optional-orelse-method-in-java-with-examples/)
- [Optional ifPresentOrElse() Method in Java with Examples](https://www.geeksforgeeks.org/optional-ifpresentorelse-method-in-java-with-examples/)
- [Optional orElseGet() Method in Java with Examples](https://www.geeksforgeeks.org/optional-orelseget-method-in-java-with-examples/)
- [Optional filter() Method in Java with Examples](https://www.geeksforgeeks.org/optional-filter-method-in-java-with-examples/)
- [Optional empty() Method in Java with Examples](https://www.geeksforgeeks.org/optional-empty-method-in-java-with-examples/)
- [Optional hashCode() Method in Java with Examples](https://www.geeksforgeeks.org/optional-hashcode-method-in-java-with-examples/)
- [Optional toString() Method in Java with Examples](https://www.geeksforgeeks.org/optional-tostring-method-in-java-with-examples/)
- [Optional equals() Method in Java with Examples](https://www.geeksforgeeks.org/optional-equals-method-in-java-with-examples/)
- [Optional stream() Method in Java with examples](https://www.geeksforgeeks.org/optional-stream-method-in-java-with-examples/)
- [Optional or() Method in Java with Examples](https://www.geeksforgeeks.org/optional-or-method-in-java-with-examples/)
- [Optional get() Method in Java with Examples](https://www.geeksforgeeks.org/optional-get-method-in-java-with-examples/)
- [Optional isPresent() Method in Java with Examples](https://www.geeksforgeeks.org/optional-ispresent-method-in-java-with-examples/)
- [Optional orElseThrow() Method in Java with Examples](https://www.geeksforgeeks.org/optional-orelsethrow-method-in-java-with-examples/)
- [Optional of() method in Java with Examples](https://www.geeksforgeeks.org/optional-of-method-in-java-with-examples/)

## Date/Time API

- [Date-Time API in Java 8](https://www.geeksforgeeks.org/new-date-time-api-java8/)
- [java.time.LocalDate Class in Java](https://www.geeksforgeeks.org/java-time-localdate-class-in-java/)
- [java.time.LocalTime Class in Java](https://www.geeksforgeeks.org/java-time-localtime-class-in-java/)
- [java.time.LocalDateTime Class in Java](https://www.geeksforgeeks.org/java-time-localdatetime-class-in-java/)
- [java.time.MonthDay Class in Java](https://www.geeksforgeeks.org/java-time-monthday-class-in-java/)
- [java.time.OffsetTime Class in Java](https://www.geeksforgeeks.org/java-time-offsettime-class-in-java/)
- [java.time.OffsetDateTime Class in Java](https://www.geeksforgeeks.org/java-time-offsetdatetime-class-in-java/)
- [java.time.Clock Class in Java](https://www.geeksforgeeks.org/java-time-clock-class-in-java/)
- [java.time.ZonedDateTime Class in Java](https://www.geeksforgeeks.org/java-time-zoneddatetime-class-in-java/)
- [java.time.ZoneId Class in Java](https://www.geeksforgeeks.org/java-time-zoneid-class-in-java/)
- [java.time.ZoneOffset Class in Java](https://www.geeksforgeeks.org/java-time-zoneoffset-class-in-java/)
- [java.time.Year Class in Java](https://www.geeksforgeeks.org/java-time-year-class-in-java/)
- [java.time.YearMonth Class in Java](https://www.geeksforgeeks.org/java-time-yearmonth-class-in-java/)
- [java.time.Period Class in Java](https://www.geeksforgeeks.org/java-time-period-class-in-java/)
- [java.time.Duration Class in Java](https://www.geeksforgeeks.org/java-time-duration-class-in-java/)
- [java.time.Instant Class in Java](https://www.geeksforgeeks.org/java-time-instant-class-in-java/)
- [Java 8 Clock instant() method with Examples](https://www.geeksforgeeks.org/java-8-clock-instant-method-with-examples/)
- [Java 8 Clock fixed() method with Examples](https://www.geeksforgeeks.org/java-8-clock-fixed-method-with-examples/)

## Miscellaneous

- [Default Methods In Java 8](https://www.geeksforgeeks.org/default-methods-java/)
- [Static method in Interface in Java](https://www.geeksforgeeks.org/static-method-in-interface-in-java/)
- [Can We Override Default Method in Java?](https://www.geeksforgeeks.org/can-we-override-default-method-in-java/)
- [forEach() method in Java](https://www.geeksforgeeks.org/arraylist-foreach-method-in-java/)
- [Nashorn JavaScript Engine in Java with Examples](https://www.geeksforgeeks.org/nashorn-javascript-engine-in-java-with-examples/)
- [MetaSpace in Java 8 with Examples](https://www.geeksforgeeks.org/metaspace-in-java-8-with-examples/)
- [Java class dependency analyzer in Java 8 with Examples](https://www.geeksforgeeks.org/java-class-dependency-analyzer-in-java-8-with-examples/)
- [LongUnaryOperator Interface in Java](https://www.geeksforgeeks.org/longunaryoperator-interface-in-java/)
- [IntUnaryOperator Interface in Java](https://www.geeksforgeeks.org/intunaryoperator-interface-in-java/)
- [DoubleUnaryOperator Interface in Java](https://www.geeksforgeeks.org/doubleunaryoperator-interface-in-java/)
- [UnaryOperator Interface in Java](https://www.geeksforgeeks.org/unaryoperator-interface-in-java/)
- [ObjLongConsumer Interface with Example](https://www.geeksforgeeks.org/java-8-objlongconsumer-interface-with-example/)
- [ObjIntConsumer Interface with Example](https://www.geeksforgeeks.org/java-8-objintconsumer-interface-with-example/)
- [ObjDoubleConsumer Interface with Example](https://www.geeksforgeeks.org/java-8-objdoubleconsumer-interface-with-example/)
- [DoubleSupplier Interface with Examples](https://www.geeksforgeeks.org/java-8-doublesupplier-interface-with-examples/)
- [BooleanSupplier Interface with Examples](https://www.geeksforgeeks.org/java-8-booleansupplier-interface-with-examples/)
- [IntSupplier Interface with Examples](https://www.geeksforgeeks.org/java-8-intsupplier-interface-with-examples/)
- [LongSupplier Interface with Examples](https://www.geeksforgeeks.org/java-8-longsupplier-interface-with-examples/)
- [LongConsumer Interface in Java with Examples](https://www.geeksforgeeks.org/longconsumer-interface-in-java-with-examples/)
- [DoubleConsumer Interface in Java with Examples](https://www.geeksforgeeks.org/doubleconsumer-interface-in-java-with-examples/)
- [IntConsumer Interface in Java with Examples](https://www.geeksforgeeks.org/intconsumer-interface-in-java-with-examples/)
- [LongFunction Interface in Java with Examples](https://www.geeksforgeeks.org/longfunction-interface-in-java-with-examples/)
- [IntFunction Interface in Java with Examples](https://www.geeksforgeeks.org/intfunction-interface-in-java-with-examples/)
- [ToDoubleFunction Interface in Java with Examples](https://www.geeksforgeeks.org/todoublefunction-interface-in-java-with-examples/)
- [DoubleFunction Interface in Java with Examples](https://www.geeksforgeeks.org/doublefunction-interface-in-java-with-examples/)
- [ToIntFunction Interface in Java with Examples](https://www.geeksforgeeks.org/tointfunction-interface-in-java-with-examples/)
- [LongToIntFunction Interface in Java with Examples](https://www.geeksforgeeks.org/longtointfunction-interface-in-java-with-examples/)
- [ToLongFunction Interface in Java with Examples](https://www.geeksforgeeks.org/tolongfunction-interface-in-java-with-examples/)
- [LongToDoubleFunction Interface in Java with Examples](https://www.geeksforgeeks.org/longtodoublefunction-interface-in-java-with-examples/)
- [ToLongBiFunction Interface in Java with Examples](https://www.geeksforgeeks.org/tolongbifunction-interface-in-java-with-examples/)
- [ToIntBiFunction Interface in Java with Examples](https://www.geeksforgeeks.org/tointbifunction-interface-in-java-with-examples/)
- [ToDoubleBiFunction Interface in Java with Examples](https://www.geeksforgeeks.org/todoublebifunction-interface-in-java-with-examples/)
- [DoubleToLongFunction Interface in Java with Examples](https://www.geeksforgeeks.org/java-8-doubletolongfunction-interface-in-java-with-examples/)
- [IntToDoubleFunction Interface in Java with Examples](https://www.geeksforgeeks.org/java-8-inttodoublefunction-interface-in-java-with-examples/)
- [IntToLongFunction Interface in Java with Examples](https://www.geeksforgeeks.org/java-8-inttolongfunction-interface-in-java-with-examples/)
- [DoubleToIntFunction Interface in Java with Example](https://www.geeksforgeeks.org/java-8-doubletointfunction-interface-in-java-with-example/)
- [ArrayDeque removeIf() method in Java with Examples](https://www.geeksforgeeks.org/java-8-arraydeque-removeif-method-in-java-with-examples/)

## FAQs on Java 8

### Q1: **What are the features of java8?**

> default and static methodsFunctional Interfaces and Lambda ExpressionsCollection APIJava Time APIforEach() methodConcurrency APIJava Stream API

### Q2: What advantages does Java 8 bring?

> Code is more concise and readableCode is more reusableCode is more testable and maintainableCode is now both callable and concurrentUsers can write parallel codeUsers can write database-like operationsApplications now perform betterCode is far more productive

### Q3: What is a functional interface?

> A functional interface is an interface that contains just one abstract method.

### Q4: How are functional interfaces and Lambda Expressions related?

> Lambda expressions are applied only to the functional interface’s abstract method.

In Java, Lambda expressions basically express instances of functional interfaces (An interface with a single abstract method is called a functional interface). Lambda Expressions in Java are the same as lambda functions which are the short block of code that accepts input as parameters and returns a resultant value. Lambda Expressions are recently included in Java SE 8.

Lambda Expressions implement the only abstract function and therefore implement functional interfaces lambda expressions are added in Java 8 and provide the below functionalities.

- Enable to treat functionality as a method argument, or code as data.
- A function that can be created without belonging to any class.
- A lambda expression can be passed around as if it was an object and executed on demand.

### Java Lambda Expression Example

- Java

```plain text
// Java program to demonstrate lambda expressions
```

```plain text
// A sample functional interface (An interface with
```

```plain text
interface
```

```plain text
FuncInterface
```

```plain text
// An abstract function
```

```plain text
int
```

```plain text
x);
```

```plain text
default
```

```plain text
void
```

```plain text
normalFun()
```

```plain text
System.out.println(
```

```plain text
);
```

```plain text
}
```

```plain text
{
```

```plain text
{
```

```plain text
// functional interface. This interface
```

```plain text
FuncInterface fobj = (
```

```plain text
2
```

```plain text
// This calls above lambda expression and prints 10.
```

```plain text
5
```

```plain text
}
```

---

**Output**

```plain text
10
```

## Lambda Expression Syntax

![[lambda-expression.jpg]]

```plain text
 lambda operator -> body
```

### Lambda Expression Parameters

There are three Lambda Expression Parameters are mentioned below:

1. Zero Parameter
2. Single Parameter
3. Multiple Parameters

### **1. Lambda Expression with Zero parameter**

```plain text
() -> System.out.println("Zero parameter lambda");
```

### **2. Lambda Expression with Single parameter**

```plain text
(p) -> System.out.println("One parameter: " + p);
```

It is not mandatory to use parentheses if the type of that variable can be inferred from the context

- Java

```plain text
// A Java program to demonstrate simple lambda expressions
```

```plain text
class
```

```plain text
Test {
```

```plain text
{
```

```plain text
// {1, 2, 3, 4}
```

```plain text
new
```

```plain text
ArrayList<Integer>();
```

```plain text
1
```

```plain text
arrL.add(
```

```plain text
);
```

```plain text
3
```

```plain text
arrL.add(
```

```plain text
);
```

```plain text
// of arrL
```

```plain text
// Using lambda expression to print even elements
```

```plain text
arrL.forEach(n -> {
```

```plain text
2
```

```plain text
==
```

```plain text
)
```

```plain text
});
```

```plain text
}
```

---

**Output**

```plain text
1
2
3
4
2
4
```

> Note: that lambda expressions can only be used to implement functional interfaces. In the above example also, the lambda expression implements Consumer Functional Interface.

### **3. Lambda Expression with Multiple parameters**

```plain text
(p1, p2) -> System.out.println("Multiple parameters: " + p1 + ", " + p2);
```

A Java program to demonstrate the working of a lambda expression with two arguments.

- Java

```plain text
// Java program to demonstrate working of lambda expressions
```

```plain text
// operation is implemented using lambda expressions
```

```plain text
int
```

```plain text
operation(
```

```plain text
int
```

```plain text
b);
```

```plain text
// sayMessage() is implemented using lambda expressions
```

```plain text
interface
```

```plain text
FuncInter2 {
```

```plain text
}
```

```plain text
private
```

```plain text
int
```

```plain text
operate(
```

```plain text
int
```

```plain text
b, FuncInter1 fobj)
```

```plain text
return
```

```plain text
fobj.operation(a, b);
```

```plain text
public
```

```plain text
static
```

```plain text
void
```

```plain text
main(String args[])
```

```plain text
// lambda expression for addition for two parameters
```

```plain text
// This expression implements 'FuncInter1' interface
```

```plain text
int
```

```plain text
x,
```

```plain text
// lambda expression multiplication for two
```

```plain text
// 'FuncInter1' interface
```

```plain text
int
```

```plain text
x,
```

```plain text
// Creating an object of Test to call operate using
```

```plain text
// Expressions
```

```plain text
new
```

```plain text
Test();
```

```plain text
System.out.println(
```

```plain text
+ tobj.operate(
```

```plain text
,
```

```plain text
, add));
```

```plain text
System.out.println(
```

```plain text
+ tobj.operate(
```

```plain text
,
```

```plain text
, multiply));
```

```plain text
// This expression implements 'FuncInter2' interface
```

```plain text
-> System.out.println(
```

```plain text
fobj.sayMessage(
```

```plain text
);
```

```plain text
}
```

---

**Output**

```plain text
Addition is 9
Multiplication is 18
Hello Geek
```

> Note: Lambda expressions are just like functions and they accept parameters just like functions.

## Conclusion

Some Important points intake from this article is mentioned below:

- The body of a lambda expression can contain zero, one, or more statements.
- When there is a single statement curly brackets are not mandatory and the return type of the anonymous function is the same as that of the body expression.
- When there is more than one statement, then these must be enclosed in curly brackets (a code block) and the return type of the anonymous function is the same as the type of the value returned within the code block, or void if nothing is returned.

## FAQs in Lambda Expression

### Q1. What type of lambda expression Java?

**Answer:**

> Java Lambda Expressions are the short block of code that accepts input as parameters and returns a resultant value.

### Q2. Is it good to use lambda expressions in Java?

**Answer:**

> Yes, using lambda expressions makes it easier to use and support other APIs.

### Q3. What are the drawbacks of Java lambda?

**Answer:**

> Java lambda functions can be only used with functional interfaces.