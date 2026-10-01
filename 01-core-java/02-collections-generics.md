# Collections and Generics

## Question 2: Why are generics important in Java?

**Category:** Core Java  
**Difficulty:** Medium  
**Companies:** Most backend teams  
**Time to Answer:** 10 minutes

### Question
What problem do Java generics solve, and how do type erasure and parameterized types help with safe collection usage?

### Expected Answer Summary
Generics add type safety to collections and APIs, reducing runtime errors and improving code clarity. Java implements generics using type erasure, which means generic type information is removed at runtime but enforced during compilation.

### Detailed Explanation
Without generics, code often uses raw collections like `ArrayList`, leading to `ClassCastException` at runtime. Generics let the compiler enforce type compatibility at compile time.

Example:
```java
List<String> names = new ArrayList<>();
names.add("Alice");
String value = names.get(0);
```

The compiler prevents accidental insertion of non-String values. At runtime, the JVM uses erasure to replace `T` with `Object` or bounds, which is why generic metadata is not preserved at runtime.

### Code Example
```java
public static <T> T first(List<T> values) {
    if (values.isEmpty()) throw new IllegalArgumentException("empty");
    return values.get(0);
}

List<Integer> nums = List.of(1, 2, 3);
Integer firstNum = first(nums);
```

### Key Takeaways
- Generics improve type safety
- They reduce runtime casting issues
- Type erasure keeps JVM compatibility but removes runtime generic metadata

### Sources
- Oracle Java SE Docs: Generics
- Effective Java, Joshua Bloch
