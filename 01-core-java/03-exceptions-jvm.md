# Exceptions and JVM

## Question 3: What is the difference between checked and unchecked exceptions?

**Category:** Core Java  
**Difficulty:** Easy  
**Companies:** Most companies  
**Time to Answer:** 8 minutes

### Question
Explain the difference between checked and unchecked exceptions and provide a good usage pattern for each.

### Expected Answer Summary
Checked exceptions must be declared or handled at compile time. Unchecked exceptions are runtime exceptions, which usually indicate programming errors or unrecoverable conditions.

### Detailed Explanation
Examples of checked exceptions include `IOException`, `SQLException`, `InterruptedException`. They are used for recoverable conditions that the caller may need to deal with. `throws` or `try/catch` is required.

Unchecked exceptions include `NullPointerException`, `IllegalArgumentException`, and `IllegalStateException`. These generally represent bugs or invalid program state and do not need to be declared.

A good design rule is to use checked exceptions for recoverable external failures such as I/O or network problems, and unchecked exceptions for validation or internal logic issues.

### Code Example
```java
public void readFile(String path) throws IOException {
    Files.readString(Path.of(path));
}

public void validateAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
}
```

### Key Takeaways
- Checked exceptions are recoverable and compile-time enforced
- Unchecked exceptions are usually logic bugs or invalid states
- Use exceptions to communicate error semantics, not for normal control flow

### Sources
- Oracle Java Docs: Exceptions
- Effective Java, Joshua Bloch
