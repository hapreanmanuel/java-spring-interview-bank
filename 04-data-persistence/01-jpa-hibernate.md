# JPA and Hibernate Fundamentals

## Question 1: What is the difference between JPA and Hibernate?

**Category:** Data Persistence  
**Difficulty:** Medium  
**Companies:** Java backend and enterprise apps  
**Time to Answer:** 10 minutes

### Question
Explain the distinction between JPA and Hibernate and why both are often used together.

### Expected Answer Summary
JPA is the specification that defines the Java standard for object-relational mapping. Hibernate is one of the most popular JPA implementations. In practice, you write application code against the JPA API, while Hibernate provides the actual persistence engine.

### Detailed Explanation
JPA standardizes persistence concepts like entity mappings, transactional behavior, queries, and lifecycle management. Hibernate implements these interfaces and adds additional features such as second-level caching, advanced query capabilities, and optimization options.

In most Spring Boot applications, you depend on `spring-boot-starter-data-jpa`, which eventually uses Hibernate under the hood by default.

### Key Takeaways
- JPA is the specification
- Hibernate is a common implementation
- Spring Data JPA builds on top of JPA and hides boilerplate

### Sources
- Jakarta Persistence Specification
- Hibernate ORM Documentation

---

## Question 2: What is the N+1 query problem, and how do you fix it?

**Category:** Data Persistence  
**Difficulty:** Hard  
**Companies:** Senior backend roles  
**Time to Answer:** 15–20 minutes

### Question
Explain the N+1 problem in JPA/Hibernate and several ways to address it.

### Expected Answer Summary
The N+1 problem occurs when a parent table is queried, and then for each result another query is executed to fetch associated children. This leads to many queries and poor performance.

### Detailed Explanation
Example:
```java
List<Order> orders = entityManager.createQuery("select o from Order o", Order.class).getResultList();
for (Order order : orders) {
    System.out.println(order.getItems().size()); // triggers additional queries
}
```

Solutions:
- Use `JOIN FETCH` for one-to-many relationships in queries
- Use batch fetching (`@BatchSize`, `hibernate.default_batch_fetch_size`)
- Reduce the amount of data loaded immediately
- Optimize mapping with fetch strategies and DTO projections

### Code Example
```java
@Query("select o from Order o join fetch o.items i where o.id in :ids")
List<Order> findOrdersWithItems(@Param("ids") List<Long> ids);
```

### Key Takeaways
- N+1 is a common performance anti-pattern
- Fix by fetching associated data in bulk
- Use profiling tools and SQL logs to verify

### Sources
- Hibernate Documentation: Fetching Strategies
- Vlad Mihalcea: "The N+1 Selects Problem"
