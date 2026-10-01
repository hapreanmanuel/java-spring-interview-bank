# Spring Boot Properties and Profiles

## Question 1: How do you configure environment-specific behavior in Spring Boot?

**Category:** Spring Boot  
**Difficulty:** Medium  
**Companies:** Most engineering teams  
**Time to Answer:** 10 minutes

### Question
Explain how Spring Boot profiles work and how they help in multi-environment deployments.

### Expected Answer Summary
Spring Boot profiles allow a single application to run with different configurations depending on the environment. This is commonly used to separate local, dev, test, staging, and production properties.

### Detailed Explanation
The application can load properties from files like `application.properties` and `application-dev.properties`, and activation is done through the `spring.profiles.active` property. Profiles also work well with environment variables and deployment configuration.

Example:
```properties
# application.properties
spring.profiles.active=dev
```

```properties
# application-dev.properties
server.port=8081
```

This pattern keeps configuration clear and prevents system-specific settings from being mixed into production defaults.

### Code Example
```java
@Profile("prod")
@Component
public class ProductionMetricsConfig {
    // production-only configuration
}
```

### Key Takeaways
- Profiles separate configuration by environment
- They help keep sensitive or environment-specific settings out of the base configuration
- `@Profile` can selectively activate beans

### Sources
- Spring Boot Documentation: Profiles
- Spring Boot Documentation: Externalized Configuration

---

## Question 2: What is the difference between `application.properties` and `application.yml`?

**Category:** Spring Boot  
**Difficulty:** Easy  
**Companies:** Most backend teams  
**Time to Answer:** 5 minutes

### Question
Explain the difference between properties and YAML configuration in Spring Boot and when you might choose one over the other.

### Detailed Explanation
Both are valid ways to configure Spring Boot. `.properties` is simple and straightforward, while YAML is more readable for nested configuration and structured settings. YAML allows grouping related settings under a single root and is often preferred for readability.

### Example
```yaml
server:
  port: 8080
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/app
```

### Key Takeaways
- Both are supported by Spring Boot
- YAML is often easier to read when configuration is nested
- Properties are straightforward if you want a flat, explicit format

### Sources
- Spring Boot Documentation: Externalized Configuration
