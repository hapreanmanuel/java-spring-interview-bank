# Performance Tuning and JVM Internals

## Question 1: What are the main areas of JVM memory, and why do they matter?

**Category:** Performance / JVM  
**Difficulty:** Medium  
**Companies:** Large-scale backend, platform, runtime engineering  
**Time to Answer:** 10 minutes

### Question
Explain the major memory areas in the JVM and how they relate to Java application performance.

### Detailed Explanation
The JVM has several memory regions, including:
- heap memory for object allocation
- young generation and old generation for garbage collection
- Metaspace for class metadata
- stack memory for method invocation frames
- native memory used by the JVM and libraries

Understanding these regions is important because memory pressure, GC tuning, and object retention can directly affect latency and throughput.

### Key Takeaways
- Heap size and GC tuning are critical to stability
- Object retention and high allocation rate often cause latency spikes
- Profiling is essential before changing JVM settings

### Sources
- Oracle JVM Documentation
- Java Performance: The Definitive Guide

---

## Question 2: How would you diagnose a high-latency Java application in production?

**Category:** Performance / JVM  
**Difficulty:** Hard  
**Companies:** Senior backend, platform, cloud roles  
**Time to Answer:** 20 minutes

### Question
Describe your systematic process for diagnosing a production Java application with rising latency.

### Detailed Explanation
A good diagnosis starts with:
- verifying CPU and memory usage
- checking thread dumps and lock contention
- reviewing database query latency and connection pool saturation
- inspecting GC logs and heap usage
- checking external dependency latency and retries
- profiling hot methods

The process is usually iterative: identify the symptom, narrow the scope, confirm the root cause, and then apply a targeted fix.

### Key Takeaways
- Production latency is often caused by slow dependency calls or GC pressure
- Thread dumps and heap diagnostics are essential
- Measurement and evidence matter more than speculation

### Sources
- JVM profiling docs
- Java Performance: The Definitive Guide
