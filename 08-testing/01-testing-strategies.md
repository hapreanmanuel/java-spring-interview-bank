# Testing Strategies

## Question 1: What is the difference between unit tests and integration tests?

**Category:** Testing  
**Difficulty:** Easy  
**Companies:** Most engineering teams  
**Time to Answer:** 10 minutes

### Question
Explain the purpose of unit tests and integration tests, and why both matter in backend services.

### Detailed Explanation
Unit tests verify isolated logic in a single component or class. They typically mock dependencies and focus on behavior with small inputs. Integration tests validate that multiple components work together, such as JPA repositories, controllers, security, or message listeners.

The ideal test pyramid emphasizes many fast unit tests, fewer integration tests, and a small number of end-to-end tests.

### Code Example
```java
@Test
void shouldCalculateTotalWithTax() {
    PricingService service = new PricingService();
    BigDecimal total = service.calculate(100, 0.2);
    assertEquals(new BigDecimal("120.00"), total);
}
```

### Key Takeaways
- Unit tests are fast and granular
- Integration tests verify real wiring and component interactions
- A balanced pyramid prevents slow, brittle suites

### Sources
- Martin Fowler: Test Pyramid
- JUnit and Mockito documentation

---

## Question 2: What are Testcontainers, and why are they valuable?

**Category:** Testing  
**Difficulty:** Medium  
**Companies:** Teams with real DB and integration concerns  
**Time to Answer:** 12–15 minutes

### Question
Explain what Testcontainers are and why they are useful in Java backend testing.

### Detailed Explanation
Testcontainers lets you run real dependencies like PostgreSQL, MySQL, Kafka, Redis, or Elasticsearch inside lightweight containers during test execution. This is much closer to production behavior than mocking everything out.

It is especially valuable for integration tests where you want to validate actual DB schemas, transaction behavior, message-driven flows, and cross-service contracts.

### Code Example
```java
@Service
@Testcontainers
public class EmployeeRepositoryIT {

    @Container
    static PostgreSQLContainer<?> postgres = new PostgreSQLContainer<>("postgres:15");
}
```

### Key Takeaways
- Testcontainers run real dependencies in isolated containers
- They improve confidence in integration behavior
- They are especially helpful for DB and messaging-heavy applications

### Sources
- Testcontainers Official Documentation
- Spring Boot Testing Documentation
