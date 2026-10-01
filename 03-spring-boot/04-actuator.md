# Spring Boot Actuator and Production Readiness

## Question 1: What is Spring Boot Actuator, and why is it useful?

**Category:** Spring Boot  
**Difficulty:** Medium  
**Companies:** Production backend teams, scale-up companies  
**Time to Answer:** 10–15 minutes

### Question
Describe Spring Boot Actuator and explain how it helps operators monitor and manage applications.

### Expected Answer Summary
Spring Boot Actuator exposes operational endpoints such as health checks, metrics, thread dumps, and environment information. It is useful for production monitoring, load balancing health checks, and diagnosing runtime behavior.

### Detailed Explanation
Actuator adds endpoints like `/actuator/health`, `/actuator/metrics`, `/actuator/info`, and `/actuator/beans`. It integrates naturally with tools like Prometheus, Grafana, Kubernetes liveness/readiness probes, and monitoring dashboards.

Important security considerations are required because some endpoints can expose sensitive runtime data. Production systems typically secure actuator endpoints using Spring Security and selectively expose only the endpoints needed.

### Code Example
```properties
management.endpoints.web.exposure.include=health,info,metrics
management.endpoint.health.show-details=when_authorized
```

### Key Takeaways
- Actuator exposes operational insights for production monitoring
- It is essential for health checks, metrics, and diagnostics
- Secure endpoints in production environments

### Sources
- Spring Boot Documentation: Actuator
- Spring Boot Documentation: Health Indicators

---

## Question 2: How would you secure Spring Boot Actuator endpoints?

**Category:** Spring Boot  
**Difficulty:** Hard  
**Companies:** Senior product and platform roles  
**Time to Answer:** 15 minutes

### Question
How would you restrict and secure exposed actuator endpoints in a production application?

### Detailed Explanation
You would typically:
- add Spring Security
- restrict access to actuator paths with authentication
- expose only a minimal set of endpoints
- set health info to be public while hiding sensitive metrics and env details

Example:
```java
@Bean
SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
    http
        .authorizeHttpRequests(auth -> auth
            .requestMatchers("/actuator/health").permitAll()
            .requestMatchers("/actuator/**").hasRole("ADMIN")
            .anyRequest().authenticated())
        .httpBasic();
    return http.build();
}
```

### Key Takeaways
- Actuator endpoints should not be public by default
- Use role-based or authenticated access control
- Expose only the endpoints needed for monitoring

### Sources
- Spring Security Documentation
- Spring Boot Documentation: Actuator Security
