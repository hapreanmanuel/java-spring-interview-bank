# Spring AOP and Proxying

## Question 1: What is AOP, and how does Spring use it?

**Category:** Spring Framework  
**Difficulty:** Medium  
**Companies:** Java backend and platform teams  
**Time to Answer:** 12–15 minutes

### Question
Explain Aspect-Oriented Programming and how Spring implements it through proxies and advice.

### Expected Answer Summary
AOP separates cross-cutting concerns like logging, tracing, validation, security, and transaction boundaries from the business logic itself. Spring implements AOP using proxies and advice, so code can be executed before, after, or around a target method call.

### Detailed Explanation
Spring AOP is proxy-based, not bytecode weaving in the same way as full AspectJ. It creates proxies around beans to intercept method calls. Main concepts include:
- `@Aspect` to define cross-cutting concerns
- `@Before`, `@AfterReturning`, `@AfterThrowing`, `@Around` advice
- `@Pointcut` to select where the advice executes

Common use cases include transaction management, audit logs, security checks, and metrics collection.

### Code Example
```java
@Aspect
@Component
public class LoggingAspect {

    @Before("execution(* com.example.service.*.*(..))")
    public void logBefore(JoinPoint joinPoint) {
        System.out.println("Calling: " + joinPoint.getSignature().getName());
    }
}
```

### Key Takeaways
- AOP helps isolate cross-cutting concerns
- Spring AOP is proxy-based
- It is often used for transactions, security, and observability

### Sources
- Spring Framework Documentation: AOP
- Spring Framework Documentation: Proxy-based AOP

---

## Question 2: What is the difference between JDK dynamic proxies and CGLIB proxies in Spring?

**Category:** Spring Framework  
**Difficulty:** Hard  
**Companies:** Senior backend interviews  
**Time to Answer:** 15 minutes

### Question
When Spring creates proxies for beans, what are the differences between JDK dynamic proxies and CGLIB proxies, and why does it matter?

### Detailed Explanation
Spring uses JDK dynamic proxies when the target class implements an interface. It uses CGLIB subclass proxies when the target class does not implement an interface or when configured to do so.

JDK proxies work through interfaces and are limited to interface-based method interception. CGLIB creates a subclass of the target class and can intercept class methods even when no interface exists, but it may have more overhead and can be limited by final classes/methods.

In practice, Spring’s choice depends on the runtime environment and configuration. For clean API design, interface-based contracts are usually preferred, especially when using AOP and testing.

### Key Takeaways
- JDK proxies require interfaces
- CGLIB proxies work on classes directly
- Interface-based design tends to be simpler and more maintainable

### Sources
- Spring Framework Documentation: AOP Proxying
- Spring AOP reference documentation
