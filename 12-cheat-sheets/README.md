# Java & Spring Boot Interview Cheat Sheet

## Spring Boot Quick Facts
- `@SpringBootApplication` = `@Configuration` + `@EnableAutoConfiguration` + `@ComponentScan`
- Spring Boot uses conventions and starter dependencies to reduce boilerplate
- `application.properties` / `application.yml` are externalized configuration
- Profiles allow environment-specific configuration (dev, test, prod)
- Actuator exposes health, metrics, and readiness endpoints

## Java Quick Facts
- `HashMap` is not thread-safe; `ConcurrentHashMap` is
- `final` helps with immutability and thread safety
- `Optional` is best used as a return value, not as a field or parameter
- Streams are good for transformations; avoid side effects inside stream pipelines
- `volatile` gives visibility, not atomicity

## JPA / DB Quick Facts
- N+1 is a fetch pattern issue caused by lazy loading + per-row queries
- `JOIN FETCH` can reduce N+1 queries
- Isolation levels vary by consistency/performance trade-off
- Optimistic locking uses a version field; pessimistic locking uses DB locks

## Security Quick Facts
- Authentication = identity
- Authorization = permissions
- JWT is stateless and common in backend APIs
- Always secure actuator endpoints in production

## Microservices Quick Facts
- Microservices add flexibility but increase operational complexity
- Circuit breakers prevent cascading failures
- Retries without backoff can amplify failures
- Async communication is good for decoupled workflows, but it adds eventual consistency

## Performance Quick Facts
- Check CPU, memory, GC, DB latency, thread dumps, and external calls
- High latency is often caused by poor SQL, thread contention, or blocking I/O
- Monitor queue depth, thread pools, and DB connection pool saturation

## Strong Interview Answer Pattern
When answering a technical question, a strong answer includes:
1. direct definition
2. why it exists
3. trade-offs
4. real-world example
5. operational considerations

## Common follow-up questions from interviewers
- What are the trade-offs?
- What are the edge cases?
- What happens under load?
- How do you test this?
- How would you monitor/observe it?
- How would you debug it in production?
