# Concurrency and Threading

## Question 4: What is a deadlock, and how would you prevent it?

**Category:** Core Java  
**Difficulty:** Hard  
**Companies:** High-scale backend companies  
**Time to Answer:** 15–20 minutes

### Question
Explain deadlock in Java, how it occurs, and strategies to prevent or detect it.

### Detailed Explanation
A deadlock occurs when two or more threads block forever because each holds a lock that the other needs. This usually happens in a circular waiting pattern.

Example:
```java
synchronized (lockA) {
    synchronized (lockB) {
        // work
    }
}
```

and another thread does the reverse:
```java
synchronized (lockB) {
    synchronized (lockA) {
        // work
    }
}
```

### Prevention Strategies
- Always acquire locks in a consistent order
- Avoid holding multiple locks longer than necessary
- Use timeout-based locking (`tryLock`) when appropriate
- Prefer higher-level concurrency abstractions such as `ExecutorService` or `BlockingQueue`
- Use thread dumps and JVM tools to detect lock contention

### Code Example
```java
private final Object lockA = new Object();
private final Object lockB = new Object();

public void myMethod() {
    synchronized (lockA) {
        synchronized (lockB) {
            // safe
        }
    }
}
```

### Key Takeaways
- Deadlocks require circular waiting
- Lock ordering is the most effective prevention mechanism
- Proper monitoring and thread dumps are essential in production systems

### Sources
- Java Concurrency in Practice (Goetz et al.)
- Oracle Java Docs: Locks and synchronization
