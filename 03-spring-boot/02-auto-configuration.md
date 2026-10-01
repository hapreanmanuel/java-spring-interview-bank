# Spring Boot Auto-Configuration

## Question 2: How does Spring Boot auto-configuration work?

**Category:** Spring Boot  
**Difficulty:** Medium  
**Companies:** Senior-level backend interviews  
**Time to Answer:** 12–15 minutes

### Question
Explain how Spring Boot automatically configures beans and why it matters for application startup.

### Expected Answer Summary
Spring Boot auto-configuration uses `@Conditional` annotations and the classpath to decide which configuration classes should be applied. It analyzes dependencies, environment properties, and beans to create a working application with minimal manual setup.

### Detailed Explanation
The `@SpringBootApplication` annotation includes `@EnableAutoConfiguration`. During startup, Spring Boot scans the classpath and loads auto-configuration classes, such as JDBC, web, security, and caching setups. It checks whether a relevant bean is already present and if conditions are satisfied before creating additional beans.

This process reduces boilerplate while keeping customization possible through `application.properties`, custom beans, or `@ConditionalOnMissingBean` logic.

### Code Example
```java
@Configuration
@EnableAutoConfiguration
public class AppConfig {
}
```

### Key Takeaways
- `@EnableAutoConfiguration` is the key entry point
- Auto-configuration uses condition checks and classpath inspection
- Custom beans can override default auto-configured beans

### Sources
- Spring Boot Documentation: Auto-Configuration
- Spring Boot Documentation: Conditional Annotations
