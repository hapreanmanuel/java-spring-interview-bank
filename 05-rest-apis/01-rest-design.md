# REST API Design

## Question 1: What makes an API RESTful?

**Category:** REST API Design  
**Difficulty:** Medium  
**Companies:** Most product and platform companies  
**Time to Answer:** 10 minutes

### Question
Explain what REST is, and what characteristics make an API more RESTful.

### Expected Answer Summary
REST is an architectural style built around resources, stateless interactions, standard HTTP verbs, and representational data. A RESTful API uses URIs to represent resources, standard methods for actions, and consistent responses.

### Detailed Explanation
Good RESTful APIs:
- use nouns for resources, not verbs in the URL
- use HTTP methods like `GET`, `POST`, `PUT`, `PATCH`, `DELETE`
- are stateless, meaning no server-side session is required for each request
- return appropriate status codes such as `200`, `201`, `204`, `400`, `404`, and `500`
- handle idempotency carefully

A resource-based design such as `/users/123/orders` is generally better than an RPC-like design such as `/getUserOrders`.

### Code Example
```java
@GetMapping("/users/{id}")
public ResponseEntity<UserDto> getUser(@PathVariable Long id) { ... }
```

### Key Takeaways
- REST favors resource semantics over procedure semantics
- Use standard HTTP semantics and status codes
- Keep APIs stateless and cacheable where possible

### Sources
- Roy Fielding: REST architectural style
- HTTP Semantics (IETF)

---

## Question 2: How do you handle validation and error responses in a REST API?

**Category:** REST API Design  
**Difficulty:** Medium  
**Companies:** Product and backend teams  
**Time to Answer:** 12–15 minutes

### Question
Explain how a well-designed Spring Boot REST API validates input and returns useful error responses.

### Detailed Explanation
Validation should happen at the API boundary using annotations like `@Valid`, `@NotNull`, `@Email`, and `@Size`. The API should return structured error payloads with clear codes and details rather than plain text exceptions.

A good response shape is:
```json
{
  "code": "VALIDATION_ERROR",
  "message": "Request validation failed",
  "details": [
    { "field": "email", "message": "must be a valid email" }
  ]
}
```

Use `@ControllerAdvice` and `@ExceptionHandler` to centralize error mapping.

### Code Example
```java
@PostMapping("/users")
public ResponseEntity<UserDto> createUser(@Valid @RequestBody CreateUserRequest request) {
    return ResponseEntity.status(HttpStatus.CREATED).body(userService.create(request));
}
```

### Key Takeaways
- Validate on entry to the service boundary
- Return standardized error payloads
- Use centralized exception handling to avoid inconsistent responses

### Sources
- Spring Boot Documentation: Validation
- Spring Framework Documentation: @ControllerAdvice
