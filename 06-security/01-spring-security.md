# Spring Security Fundamentals

## Question 1: What is the difference between authentication and authorization?

**Category:** Security  
**Difficulty:** Easy  
**Companies:** Most backend teams  
**Time to Answer:** 5–10 minutes

### Question
Explain the difference between authentication and authorization and provide a realistic example.

### Detailed Explanation
Authentication answers: “Who are you?” Authorization answers: “What are you allowed to do?”

Example: a user logs in with a username and password (authentication). Once authenticated, the application checks whether the user has `ADMIN` rights to access a route or resource (authorization).

In Spring Security, this is commonly implemented with `AuthenticationManager`, `UserDetailsService`, and access rules with `hasRole()` or `hasAuthority()`.

### Key Takeaways
- Authentication confirms identity
- Authorization checks access rights
- Both are essential for secure backend systems

### Sources
- Spring Security Documentation

---

## Question 2: How do you secure a REST API with JWT in Spring Boot?

**Category:** Security  
**Difficulty:** Hard  
**Companies:** Senior backend, fintech, SaaS companies  
**Time to Answer:** 15–20 minutes

### Question
Describe how to configure JWT-based authentication in Spring Boot and why it is commonly used for stateless APIs.

### Detailed Explanation
A JWT-based system issues a signed token after successful login. The token typically contains identity and role information. The server verifies the signature and uses claims to authorize requests without server-side session state.

Typical flow:
1. Client sends credentials to `/login`
2. Server validates credentials
3. Server creates JWT with issuer, subject, roles, expiry, etc.
4. Client sends token in the `Authorization` header
5. Spring Security validates token and resolves the authenticated principal

### Code Example
```java
http
    .authorizeHttpRequests(auth -> auth
        .requestMatchers("/auth/**").permitAll()
        .anyRequest().authenticated())
    .sessionManagement(session -> session.sessionCreationPolicy(SessionCreationPolicy.STATELESS))
    .oauth2ResourceServer(oauth2 -> oauth2.jwt());
```

### Key Takeaways
- JWT is stateless and scalable for API gateways and microservices
- It should be signed and validated cryptographically
- Expiry and rotation are important operational concerns

### Sources
- Spring Security OAuth2 Resource Server docs
- JWT RFC 7519
