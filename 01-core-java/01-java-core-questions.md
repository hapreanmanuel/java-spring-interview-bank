# Core Java Question Bank

## Question 1: What is the difference between HashMap and ConcurrentHashMap?

**Category:** Core Java  
**Difficulty:** Medium  
**Companies:** Amazon, Netflix, startup backend teams  
**Time to Answer:** 10–15 minutes

### Question
Explain the difference between `HashMap` and `ConcurrentHashMap`, and when each should be used.

### Expected Answer Summary
`HashMap` is not thread-safe and is suitable for single-threaded or effectively immutable use. `ConcurrentHashMap` is designed for concurrent access; it provides thread-safe reads and writes without using synchronized on the entire map.

### Detailed Explanation
`HashMap` stores data in buckets and provides O(1) average-time access. However, it is not safe for concurrent mutation. If multiple threads mutate the same map without synchronization, you can get lost updates, stale reads, and even infinite loops under certain resize conditions.

`ConcurrentHashMap` partitions the map internally for better concurrency and uses volatile and CAS-based mechanisms to avoid locking the entire structure. It allows many threads to read and write concurrently while preserving thread safety. It does not support `null` keys or values.

Use `HashMap` for local or single-threaded data structures, and `ConcurrentHashMap` for caches, shared registries, or concurrent request processing.

### Code Example
```java
Map<String, Integer> map = new HashMap<>();
Map<String, Integer> concurrentMap = new ConcurrentHashMap<>();

concurrentMap.put("user-1", 10);
concurrentMap.computeIfAbsent("user-2", key -> 20);
```

### Key Takeaways
- `HashMap` is fast but not thread-safe
- `ConcurrentHashMap` is optimized for multi-threaded access
- `ConcurrentHashMap` should be chosen for shared mutable state across threads

### Sources
- Oracle Java Documentation: `HashMap` and `ConcurrentHashMap` classes
- Java Concurrency in Practice (Goetz et al.)
