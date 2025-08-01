# sapient-asde-na-july-2025


# Java-Functional Programming 


# Participant’s Guide: Functional Java and JSON Processing

## Functional Style Java - Default Methods
**Concept:** Allow interfaces to provide a default implementation.

**Example:**
```java
interface Calculator {
    int add(int a, int b); // abstract
    default int subtract(int a, int b) {
        return a - b; // default implementation
    }
}
```

**Quick Assignment:** Implement default methods for multiply and divide.

## Functional Interfaces
**Concept:** Interfaces with exactly one abstract method.

**Example:**
```java
@FunctionalInterface
interface Operation {
    int execute(int a, int b);
}
```

**Quick Assignment:** Create functional interfaces for multiplication and division operations.

## Lambda Syntax, Using Lambdas
**Concept:** Concise representation of anonymous methods.

**Example:**
```java
Operation addition = (a, b) -> a + b;
System.out.println(addition.execute(5, 3)); // 8
```

**Quick Assignment:** Use lambdas to implement multiplication and division.

## Function Descriptors, Method References
**Concept:** Shorthand notation to refer to existing methods.

**Example:**
```java
class SimpleCalculator {
    static int add(int a, int b) {
        return a + b;
    }
}
Operation addition = SimpleCalculator::add;
```

**Quick Assignment:** Implement method references for subtraction, multiplication, and division.

## Choosing Functional Interfaces, Constructor References
**Concept:** Constructor references allow instantiation via functional interfaces.

**Example:**
```java
interface CalculatorFactory {
    SimpleCalculator getCalculator();
}
CalculatorFactory factory = SimpleCalculator::new;
SimpleCalculator calc = factory.getCalculator();
```

**Quick Assignment:** Create constructor references for custom calculator objects.

## Streams API - What are Streams?
**Concept:** Streams represent sequences of elements supporting functional operations.

**Example:**
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream().forEach(System.out::println);
```

**Quick Assignment:** Stream integers and print only even numbers.

## Stream Advantages, Stream Operations
**Concept:** Streams enable readability, efficiency, and easy manipulation.

**Example:**
```java
List<Integer> numbers = 
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->
Arrays.asList(1, 2, 3, 4);
List<Integer> squared = numbers.stream().map(n -> n*n).co
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->
llect(Collectors.toList());
```

**Quick Assignment:** Using streams, multiply all numbers by 2.

## Streams vs. Collections
**Concept:** Collections store data; Streams process data.

**Example:**  
- **Collection:** `List<Integer> numbers = Arrays.asList(1,2,3);`  
- **Stream:** `numbers.stream().forEach(System.out::println);`

**Quick Assignment:** Convert a collection to a stream and print elements greater than 2.

## Intermediate Ops: map(), filter(), flatMap()
**Concept:** Intermediate operations transform and filter data.

**Example:**
```java
List<Integer> nums = Arrays.asList(1, 2, 3);
nums.stream()
    .filter(n -> n > 1)
    .map(n -> n * 10)
    .forEach(System.out::println);
```

**Quick Assignment:** Filter even numbers and map to their squares.

## Terminal Ops: forEach(), collect(), reduce()
**Concept:** Terminal operations produce results or side effects.

**Example:**
```java
List<Integer> nums = Arrays.asList(1, 2, 3);
int sum = nums.stream().reduce(0, Integer::sum);
System.out.println(sum);
```

**Quick Assignment:** Use `reduce` to find the product of all elements.

## Numeric Streams: IntStream, LongStream, DoubleStream
**Concept:** Specialized streams for numeric primitive types.

**Example:**
```java
int sum = IntStream.range(1, 5).sum(); // outputs 10
System.out.println(sum);
```

**Quick Assignment:** Generate a DoubleStream and calculate average.

## JSON Processing in Java 

### Introduction to JSON
**Concept:** JSON is a text-based data interchange format.

**Example:**
```json
{"operation":"add","operand1":10,"operand2":5}
```

### JSON Parsing in Java (with Jackson)
**Concept:** Reading JSON into Java objects.

**Example:**
```java
ObjectMapper mapper = new ObjectMapper();
String json = "{"operation":"add","operand1":10,"operand2":5}";
CalculatorRequest req = mapper.readValue(json, CalculatorRequest.class);
```

**Quick Assignment:** Parse JSON with "multiply" and "divide" operations.

### Working with Jackson - Java to JSON and Vice Versa
**Concept:** Converting Java objects to JSON strings and vice versa.

**Example:**
```java
CalculatorResponse resp = new CalculatorResponse(15);
String jsonString = mapper.writeValueAsString(resp);
```

**Quick Assignment:** Convert multiplication result object to JSON.

### Handling JSON Arrays & Complex Data Structures
**Concept:** Managing JSON arrays and nested structures.

**Example JSON:**
```json
{
  "operations": [
    {"type":"add","result":15},
    {"type":"subtract","result":5}
  ]
}
```

**Example Java Parsing:**
```java
class OperationResult {
    public String type;
    public int result;
}

class Operations {
    public List<OperationResult> operations;
}

Operations ops = mapper.readValue(jsonString, Operations.class);
```

**Quick Assignment:** Add multiplication and division operations to the JSON array and parse them into Java.
