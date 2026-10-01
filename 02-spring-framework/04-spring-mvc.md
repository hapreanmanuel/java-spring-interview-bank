# Spring MVC and Request Handling

## Question 1: How does Spring MVC process an HTTP request?

**Category:** Spring Framework  
**Difficulty:** Medium  
**Companies:** Most backend engineering teams  
**Time to Answer:** 10–15 minutes

### Question
Walk through the path of an incoming HTTP request through the Spring MVC components.

### Expected Answer Summary
A request enters the DispatcherServlet, which consults handler mappings to find the relevant controller, invokes the handler method, resolves view or response rendering, and returns the HTTP response. The request passes through relevant interceptors, validation, argument resolution, and exception handling layers.

### Detailed Explanation
The main flow is:
1. Request arrives at `DispatcherServlet`
2. `HandlerMapping` selects the controller based on URL, method, and other conditions
3. `HandlerAdapter` invokes the handler method
4. Controller method parameters are resolved and model data is prepared
5. `ViewResolver` selects a view or the method returns a response body
6. `HttpMessageConverter` serializes the response
7. Response is sent back to the client

Spring can also handle exceptions via `@ControllerAdvice` and `@ExceptionHandler`.

### Code Example
```java
@RestController
public class UserController {

    @GetMapping("/users/{id}")
    public User getUser(@PathVariable Long id) {
        return userService.getUser(id);
    }
}
```

### Key Takeaways
- `DispatcherServlet` is the front controller
- Mappings, adapters, converters, and resolvers coordinate request handling
- MVC is designed to be flexible and testable

### Sources
- Spring Framework Documentation: DispatcherServlet
- Spring MVC Documentation

---

## Question 2: What is the difference between @Controller and @RestController?

**Category:** Spring Framework  
**Difficulty:** Easy  
**Companies:** Most Java backend interviews  
**Time to Answer:** 5 minutes

### Question
Explain the difference between `@Controller` and `@RestController`, and when to use each.

### Detailed Explanation
`@Controller` is used for MVC controllers that typically return a view name or use model attributes. In contrast, `@RestController` is a specialization that combines `@Controller` and `@ResponseBody`, meaning that every method response is written directly to the body as JSON/XML rather than resolved as a server-side view.

Use `@RestController` for REST APIs and `@Controller` for traditional web applications that render templates.

### Code Example
```java
@Controller
public class PageController {
    @GetMapping("/login")
    public String login() {
        return "login";
    }
}

@RestController
public class ApiController {
    @GetMapping("/health")
    public String health() {
        return "OK";
    }
}
```

### Sources
- Spring Framework Documentation: MVC
- Spring Boot REST documentation
