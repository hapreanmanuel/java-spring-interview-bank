# Microservices Fundamentals

## Question 1: What are the trade-offs of a microservices architecture?

**Category:** Microservices  
**Difficulty:** Medium  
**Companies:** Platform and backend companies  
**Time to Answer:** 15 minutes

### Question
Discuss the benefits and downsides of moving from a monolith to a microservices architecture.

### Expected Answer Summary
Microservices allow independent deployment, scaling, and ownership of services, which improves modularity and team autonomy. However, they add operational complexity: network calls, service discovery, observability, retries, data consistency issues, and deployment coordination.

### Detailed Explanation
A monolith may be simpler to build and run initially. Microservices become attractive when teams need independent scaling or service ownership. They require a platform story that includes API gateways, service discovery, logs, traces, metrics, circuit breakers, and deployment tooling.

A common design principle is to move to microservices only when the system’s complexity and operational overhead are worth the benefits.

### Key Takeaways
- Microservices improve modularity but increase distributed-system complexity
- They are not automatically superior to a monolith
- Team maturity and operational capability are critical

### Sources
- Martin Fowler: Microservices
- Spring Cloud documentation

---

## Question 2: What is a circuit breaker, and why is it important?

**Category:** Microservices  
**Difficulty:** Medium  
**Companies:** Backend and platform teams  
**Time to Answer:** 10 minutes

### Question
Explain the circuit breaker pattern and how it helps in distributed systems.

### Detailed Explanation
A circuit breaker prevents repeated calls to a failing downstream service. When failures exceed a threshold, the system transitions to an open state and fails fast instead of continuing to hammer the dependency.

This improves resilience by reducing cascading failures and allowing the failing service to recover. Libraries like Resilience4j often implement this pattern.

### Code Example
```java
CircuitBreaker circuitBreaker = CircuitBreaker.ofDefaults("paymentService");

Supplier<String> decoratedSupplier = CircuitBreaker.decorateSupplier(circuitBreaker, () -> restClient.get());
String result = Try.ofSupplier(decoratedSupplier)
    .recover(ex -> "fallback-value")
    .get();
```

### Key Takeaways
- Circuit breakers protect downstream services from overload and cascading failure
- They provide fail-fast behavior and improve resilience
- Timeouts and retries should be paired with circuit breakers

### Sources
- Resilience4j documentation
- Microservices patterns literature
