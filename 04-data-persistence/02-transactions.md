# Transactions, Isolation, and Locking

## Question 1: What is transaction isolation, and why does it matter?

**Category:** Data Persistence  
**Difficulty:** Hard  
**Companies:** Backend systems, fintech, payment systems  
**Time to Answer:** 12–20 minutes

### Question
Explain transaction isolation levels and why they matter in concurrent database systems.

### Expected Answer Summary
Isolation defines how transaction changes are visible to other concurrent transactions. It affects consistency and concurrency. Common levels include READ_UNCOMMITTED, READ_COMMITTED, REPEATABLE_READ, and SERIALIZABLE.

### Detailed Explanation
The stronger the isolation, the more consistent the reads but the more locking or serialization overhead you may introduce. For example:
- `READ_COMMITTED` avoids dirty reads but allows non-repeatable reads
- `REPEATABLE_READ` gives stable reads within a transaction
- `SERIALIZABLE` is the strongest and typically enforces stricter locking or serialization

In financial applications, choosing the wrong isolation level can lead to lost updates or duplicate processing.

### Code Example
```java
@Transactional(isolation = Isolation.SERIALIZABLE)
public void processTransfer(Long fromId, Long toId, BigDecimal amount) {
    // safely process balance update under strict isolation
}
```

### Key Takeaways
- Isolation is about visibility between concurrent transactions
- Strong isolation improves consistency but can reduce throughput
- Match isolation level to business requirements

### Sources
- PostgreSQL Documentation: Transaction Isolation
- JPA / Spring Transaction Management docs

---

## Question 2: What are optimistic and pessimistic locking?

**Category:** Data Persistence  
**Difficulty:** Medium  
**Companies:** Most systems with concurrency  
**Time to Answer:** 15 minutes

### Question
Compare optimistic and pessimistic locking and explain when each is appropriate.

### Detailed Explanation
Optimistic locking assumes conflicts are rare. It uses a version column and checks it on update. If the row has changed since it was read, the update fails with an optimistic lock exception.

Pessimistic locking locks the row immediately (via `SELECT ... FOR UPDATE`) so concurrent modifications cannot happen until the lock is released.

### Code Example
```java
@Entity
public class Account {
    @Version
    private Long version;
}
```

```java
@Lock(LockModeType.PESSIMISTIC_WRITE)
@Query("select a from Account a where a.id = :id")
Optional<Account> findForUpdate(@Param("id") Long id);
```

### Key Takeaways
- Optimistic locking is good for low-conflict workloads
- Pessimistic locking is safer under high contention or sensitive updates
- Use locking to prevent lost updates and inconsistent balances

### Sources
- Hibernate Documentation: Optimistic Locking
- Spring Data JPA documentation
