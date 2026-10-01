# Spring Framework: Dependency Injection and Bean Lifecycle

## Question 1: What is dependency injection and how does Spring implement it?

**Category:** Spring Framework  
**Difficulty:** Medium  
**Companies:** Most backend companies  
**Time to Answer:** 10–15 minutes

### Question
Explain dependency injection and how the Spring IoC container resolves and injects dependencies.

### Expected Answer Summary
Dependency injection is a design pattern where objects receive their dependencies from the outside rather than creating them internally. Spring’s IoC container builds objects, resolves dependencies, and injects them using bean definitions and metadata.

### Detailed Explanation
Spring creates and manages application components as beans. When one bean needs another, the container resolves the dependency and injects it based on the bean definition. This reduces coupling and makes code easier to test.

Spring supports several injection styles:
- Constructor injection
- Setter injection
- Field injection (not recommended in production code)

Constructor injection is preferred because it makes dependencies explicit and improves immutability and testability.

### Code Example
```java
@Service
public class OrderService {
    private final PaymentService paymentService;

    public OrderService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

### Key Takeaways
- Spring IoC container manages object creation and wiring
- Constructor injection is usually the best practice
- DI reduces tight coupling and makes testing easier

### Sources
- Spring Framework Documentation: Dependency Injection
- Spring Framework Documentation: IoC Container
