# Spring Framework: Configuration and AOP

## Question 2: What is the difference between @Component, @Service, @Repository, and @Controller?

**Category:** Spring Framework  
**Difficulty:** Easy  
**Companies:** Most backend companies  
**Time to Answer:** 5–10 minutes

### Question
Describe the purpose of Spring stereotype annotations and explain the differences between them.

### Expected Answer Summary
These annotations are all specializations of `@Component` and are used to mark classes for component scanning. `@Service`, `@Repository`, and `@Controller` carry semantic meaning, but all are treated as beans by Spring.

### Detailed Explanation
- `@Component`: general-purpose annotation for any managed component
- `@Service`: used for service layer business logic
- `@Repository`: used for data access layer; Spring may translate persistence exceptions
- `@Controller`: used in MVC controllers to handle HTTP requests

The main difference is semantic clarity, not runtime behavior. They make the code easier to understand and help with AOP and architecture boundaries.

### Sources
- Spring Framework Documentation: Bean Scopes and Stereotypes
