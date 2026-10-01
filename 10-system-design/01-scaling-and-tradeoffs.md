# System Design and Scalability

## Question 1: How would you design a rate-limited API gateway?

**Category:** System Design  
**Difficulty:** Hard  
**Companies:** Platform, backend, fintech, SaaS  
**Time to Answer:** 20–25 minutes

### Question
Design a rate-limited API gateway that protects backend services from overload.

### Expected Answer Summary
A rate-limited gateway should centralize request validation, enforce limits per client or route, and protect backend services from spikes. It typically uses token buckets or leaky bucket algorithms and stores counters in a fast, distributed store like Redis.

### Detailed Explanation
A robust design includes:
- client identification and request classification
- per-route and per-user quotas
- rejection or throttling behavior
- rate-limit state storage in Redis or similar
- observability and alerts for threshold breaches
- fallback behavior when the limit is exceeded

The design must also consider race conditions and distributed lock concerns when multiple nodes enforce the same rate limit.

### Key Takeaways
- Centralized enforcement is better than logic in each service
- Use Redis or a distributed counter store for cross-node enforcement
- Make throttling behavior explicit and observable

### Sources
- NGINX rate limiting docs
- Redis docs on counters and TTLs
- System Design Primer

---

## Question 2: What are the trade-offs between synchronous and asynchronous communication in distributed systems?

**Category:** System Design  
**Difficulty:** Hard  
**Companies:** Senior backend and platform roles  
**Time to Answer:** 15–20 minutes

### Question
Compare synchronous and asynchronous interaction patterns in backend systems, and explain when each is appropriate.

### Detailed Explanation
Synchronous communication (REST, gRPC) is simpler and easier to reason about but creates tighter coupling and waits on downstream latency. Asynchronous communication (queues, events, Kafka) improves resilience and throughput but introduces eventual consistency and more operational complexity.

Use synchronous calls for user-facing interactive operations when latency must be low and a real-time response is required. Use asynchronous patterns for workflows, notifications, long-running tasks, and event-driven integration.

### Key Takeaways
- Sync = simpler, more coupled, lower latency
- Async = more resilient, better scaling, eventual consistency
- The right choice depends on the business requirement and failure model

### Sources
- Designing Data-Intensive Applications, Martin Kleppmann
- System Design Primer
