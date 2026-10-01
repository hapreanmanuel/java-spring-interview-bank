# Java 8+ Features

## Question 1: What are the main benefits of the Java Stream API?

**Category:** Core Java  
**Difficulty:** Medium  
**Companies:** Most backend companies  
**Time to Answer:** 10–15 minutes

### Question
Explain how the Java Stream API works, and when it is a good fit versus when it can be harmful.

### Expected Answer Summary
The Stream API enables declarative processing of collections and supports operations like filter, map, reduce, and collect. It is useful for data transformations and data pipelines, but it can hurt readability or performance if used with side effects or complex nested logic.

### Detailed Explanation
Streams are lazy, support functional programming patterns, and allow composition without mutating data structures. They help express operations like:
```java
List<String> names = users.stream()
    .map(User::getName)
    .filter(name -> name != null)
    .collect(Collectors.toList());
```

A stream should be used for pipelines of data processing. Avoid mutating shared state inside stream operations; this breaks the functional expectation and can lead to concurrency issues. For expensive or blocking operations, streams can also hide performance problems when used over large collections.

### Code Example
```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);
int sum = numbers.stream()
    .filter(n -> n % 2 == 0)
    .mapToInt(Integer::intValue)
    .sum();
System.out.println(sum); // 6
```

### Key Takeaways
- Streams are good for pipeline-style data transformation
- They are lazy and can be composed
- Avoid side effects and blocking operations inside streams

### Sources
- Oracle Java Documentation: Streams
- Java SE 8 Documentation: Functional Interfaces and Lambda Expressions

---

## Question 2: What is the purpose of Optional, and when should it not be used?

**Category:** Core Java  
**Difficulty:** Medium  
**Companies:** Most backend teams  
**Time to Answer:** 10 minutes

### Question
What is `Optional`, and what are the trade-offs of using it in Java APIs?

### Expected Answer Summary
`Optional` is a container type for values that may be absent. It makes null-handling more explicit and helps prevent accidental null dereferences, especially in APIs returning optional values.

### Detailed Explanation
The key idea is that `Optional` is a value type representing “maybe there is a value.” It encourages explicit checks like `isPresent()` or `orElse()`. It is especially useful in methods like `findById()` that can return no result.

However, `Optional` should not be overused as a field type or as an argument. It is not a replacement for all null checks, and it is not meant for serialization or as a general-purpose substitute for control flow.

### Code Example
```java
Optional<String> name = Optional.ofNullable(user.getName());
String displayName = name.orElse("Anonymous");
```

### Key Takeaways
- `Optional` is useful for return values and data access
- Avoid using `Optional` for fields, constructor parameters, or deep control flow
- It should communicate absence clearly, not hide it silently

### Sources
- Oracle Java Documentation: Optional
- Effective Java, Joshua Bloch
