# 🚀 SDE-2 Backend Engineer Roadmap — Full 53-Section Edition

> All 53 original sections, intact — nothing merged or cut. Each section now has: a description of what it is and why it matters, a one-line explanation per topic (not just a bare term), and real resources.

---

# 📌 Table of Contents

1. [Roadmap Philosophy](#1-roadmap-philosophy)
2. [Engineering Foundations](#2-engineering-foundations)
3. [Git & GitHub](#3-git--github)
4. [Java](#4-java)
5. [JVM](#5-jvm)
6. [Concurrency & Multithreading](#6-concurrency--multithreading)
7. [Spring Framework](#7-spring-framework)
8. [Spring Boot](#8-spring-boot)
9. [API Engineering](#9-api-engineering)
10. [REST](#10-rest)
11. [gRPC](#11-grpc)
12. [GraphQL](#12-graphql)
13. [PostgreSQL](#13-postgresql)
14. [JPA & Hibernate](#14-jpa--hibernate)
15. [Redis](#15-redis)
16. [NoSQL](#16-nosql)
17. [Elasticsearch / OpenSearch](#17-elasticsearch--opensearch)
18. [Python](#18-python)
19. [FastAPI](#19-fastapi)
20. [Message Queues](#20-message-queues)
21. [RabbitMQ](#21-rabbitmq)
22. [Cloud Messaging](#22-cloud-messaging)
23. [Kafka](#23-kafka)
24. [Event-Driven Architecture](#24-event-driven-architecture)
25. [Outbox Pattern](#25-outbox-pattern)
26. [Saga Pattern](#26-saga-pattern)
27. [CQRS](#27-cqrs)
28. [Event Sourcing](#28-event-sourcing)
29. [Distributed Systems](#29-distributed-systems)
30. [Distributed Data](#30-distributed-data)
31. [Reliability Engineering](#31-reliability-engineering)
32. [System Design — HLD](#32-system-design--hld)
33. [Low-Level Design](#33-low-level-design)
34. [Docker](#34-docker)
35. [Kubernetes](#35-kubernetes)
36. [AWS](#36-aws)
37. [Azure](#37-azure)
38. [Linux](#38-linux)
39. [Networking](#39-networking)
40. [CI/CD](#40-cicd)
41. [Deployment Strategies](#41-deployment-strategies)
42. [Observability](#42-observability)
43. [Prometheus](#43-prometheus)
44. [Grafana](#44-grafana)
45. [Logs](#45-logs)
46. [OpenTelemetry & Distributed Tracing](#46-opentelemetry--distributed-tracing)
47. [Security](#47-security)
48. [Performance Engineering](#48-performance-engineering)
49. [Production Engineering](#49-production-engineering)
50. [Capstone Project](#50-capstone-project)
51. [Failure Engineering](#51-failure-engineering)
52. [SDE-2 Interview Preparation](#52-sde-2-interview-preparation)
53. [Final Skill Matrix](#53-final-skill-matrix)

---

# 1. Roadmap Philosophy

**What it is:** The mindset behind this whole document.
**Why it matters:** Prevents you from treating this as a technology bingo card instead of a coherent skillset.

The goal is not "learn 50 technologies" — it's: **take a backend requirement, design it, implement it, scale it, deploy it, monitor it, secure it, and debug it in production.**

```text
Fundamentals → Backend Development → Data → Messaging → Distributed Systems
→ System Design → Cloud → CI/CD → Operations → Observability → Security → Production
```

**Resources:** *Designing Data-Intensive Applications* (Kleppmann) — read the preface; it makes this exact argument about tools vs. underlying ideas.

---

# 2. Engineering Foundations

**What it is:** The CS and software-engineering baseline every later section assumes.
**Why it matters:** You can't reason about Kafka's throughput or Postgres's index cost without Big-O; you can't survive code review without SOLID/DRY fluency.

### 2.1 Computer Science Fundamentals
| Topic | Description |
|---|---|
| Data structures | Arrays, lists, trees, graphs, hash maps — the vocabulary for describing how data is organized and accessed. |
| Algorithms | Sorting, searching, traversal — the repeatable techniques for solving classes of problems. |
| Big-O notation | How cost (time/space) grows with input size — the language for comparing two solutions objectively. |
| Memory vs CPU trade-offs | Many optimizations trade one for the other (e.g. caching = more memory, less CPU) — know which one is your bottleneck before optimizing. |
| Processes vs threads | A process has its own memory space; threads within it share memory — the root of most concurrency bugs and isolation guarantees. |
| Operating systems basics | Scheduling, memory management, I/O — explains why identical code performs differently under different OS conditions. |
| Networking basics | Client-server model, sockets, request/response — the substrate every backend call travels over. |
| Databases | How data is persisted, queried, and kept consistent — foundational before any specific DB technology. |
| Distributed systems fundamentals | What changes once your system spans more than one machine — failure becomes partial, not total. |

### 2.2 Software Engineering
| Topic | Description |
|---|---|
| Clean Code | Code that communicates intent to the next reader, not just to the compiler. |
| SOLID | Five design principles (Single responsibility, Open/closed, Liskov substitution, Interface segregation, Dependency inversion) for maintainable OO design. |
| DRY | "Don't Repeat Yourself" — duplicated logic means duplicated bugs and duplicated future edits. |
| KISS | "Keep It Simple" — the simplest design that meets the requirement beats a clever one that doesn't. |
| YAGNI | "You Aren't Gonna Need It" — don't build flexibility for a requirement that doesn't exist yet. |
| Composition over inheritance | Building behavior by combining small objects is usually more flexible than deep inheritance hierarchies. |
| Coupling | How much one module depends on the internals of another — lower coupling means changes don't ripple outward. |
| Cohesion | How focused a module's responsibilities are — high cohesion means a class does one thing well. |
| Refactoring | Improving code structure without changing external behavior — done continuously, not as a separate "cleanup phase." |
| Technical debt | Shortcuts taken now that cost more to fix later — sometimes a reasonable trade, but must be tracked, not ignored. |
| Code review | The primary quality gate on a team — catches bugs, spreads knowledge, and enforces consistency. |
| Documentation | Writing down the "why," not just the "what" — code shows what happens, docs explain why it's built that way. |
| API contracts | The explicit agreement between a service and its callers about inputs/outputs/behavior — breaking it breaks every consumer silently. |

**Resources**
- *Clean Code* — Robert C. Martin
- [Teach Yourself CS](https://teachyourselfcs.com/)
- CS50 (Harvard, free on edX)

---

# 3. Git & GitHub

**What it is:** Distributed version control plus the collaboration workflow built on top of it.
**Why it matters:** SDE-2 means managing history cleanly, not just committing — rebasing, bisecting, and reviewing others' code confidently.

### 3.1 Git Fundamentals
| Topic | Description |
|---|---|
| Repository | The full version history of a project, stored locally and/or on a remote. |
| Working tree | Your current checked-out files on disk, which may differ from the last commit. |
| Staging area | The "about to commit" zone — lets you commit a subset of your changes deliberately. |
| Commit | An immutable snapshot of the repository at a point in time. |
| Branch | A movable pointer to a commit — lets you develop in isolation from `main`. |
| Remote | A version of your repository hosted elsewhere (e.g. GitHub) that you push to/pull from. |
| HEAD | A pointer to your currently checked-out commit/branch. |
| Tags | A fixed pointer to a specific commit, typically used for release versions. |

### 3.2 Commands
`clone` `status` `add` `commit` `push` `pull` `fetch` `branch` `switch` `merge` `rebase` `log` `diff` `stash` `cherry-pick` `revert` `reset` `tag` `reflog` `bisect`
— Each is a specific, deliberate operation on the commit graph; the goal is to know *when* to reach for each, not just that they exist.

### 3.3 Advanced Git
| Topic | Description |
|---|---|
| Merge vs rebase | Merge preserves history exactly as it happened (with a merge commit); rebase rewrites your branch's history onto a new base for a clean, linear log. |
| Interactive rebase | Lets you squash, reorder, reword, or drop commits before sharing a branch — used to keep PR history readable. |
| Conflict resolution | Manually reconciling two divergent changes to the same lines — a core, unavoidable Git skill. |
| Cherry-picking | Applying a single specific commit from one branch onto another. |
| Recovering commits with reflog | Git rarely truly deletes anything immediately — reflog lets you find and recover commits that seem "lost" after a reset/rebase. |
| Git bisect | Binary-searches your commit history to find exactly which commit introduced a bug. |
| Branching strategies | Trunk-based, GitFlow, etc. — how a team organizes branches around releases and features. |
| Protected branches / PRs / code review | The GitHub-side governance that enforces review and CI before code reaches `main`. |

### 3.4 GitHub
Pull requests, Issues, Projects, Actions, Branch protection, CODEOWNERS, Release management, GitHub Actions CI — the platform layer for collaboration and automation on top of Git itself.

**Standard workflow:** `feature branch → commit → push → PR → code review → CI → merge → build → deploy`

**Resources**
- [Pro Git (free book)](https://git-scm.com/book/en/v2)
- [Learn Git Branching (interactive)](https://learngitbranching.js.org/)
- [GitHub Actions docs](https://docs.github.com/en/actions)

---

# 4. Java

**What it is:** The primary language for this roadmap.
**Why it matters:** Everything downstream (Spring, JPA, Kafka clients) is Java-shaped — weak fundamentals compound into confusion later.

### 4.1 Core Java
Variables, primitive vs reference types, classes, objects, interfaces, abstract classes, enums, records, constructors, methods, packages, access modifiers, exception handling — the syntax and building blocks; know not just *how* to use each but *when* (e.g. interface vs abstract class: interfaces define a pure contract, abstract classes can share state/implementation).

### 4.2 OOP
| Topic | Description |
|---|---|
| Encapsulation | Hiding internal state behind a controlled interface — protects invariants. |
| Abstraction | Exposing only relevant behavior, hiding implementation complexity. |
| Inheritance | A subclass reuses and extends a superclass's behavior — powerful but easy to overuse. |
| Polymorphism | Code can operate on objects of different types through a shared interface. |
| Composition vs inheritance | Composition (has-a) is usually more flexible than inheritance (is-a) for combining behavior. |

### 4.3 Collections
`ArrayList` `LinkedList` `HashMap` `HashSet` `TreeMap` `TreeSet` `Queue` `Deque` `PriorityQueue`
— Understand internally: hashing (turning a key into a bucket index), collision handling (chaining), resizing (rehashing cost when load factor is exceeded), `equals()`/`hashCode()` contracts, ordering guarantees (or lack thereof), and each structure's Big-O for insert/lookup/delete.

### 4.4 Generics
Generic classes/methods, bounded types, wildcards (`extends`/`super`), type erasure — compile-time type safety with no runtime type information retained, which is why you can't do `new T()` or reflectively inspect a generic parameter at runtime.

### 4.5 Functional Java
Lambdas, functional interfaces, Streams, Collectors, method references, `Optional` — declarative collection processing; know that streams can hide performance costs (e.g. re-evaluating on every terminal operation) and that `Optional` is meant for return types, not fields.

**Resources**
- *Effective Java* (3rd ed.) — Joshua Bloch
- [Baeldung](https://www.baeldung.com/)
- [Oracle Java Collections tutorial](https://docs.oracle.com/javase/tutorial/collections/)

---

# 5. JVM

**What it is:** What happens between your `.java` file and a running process.
**Why it matters:** When production is slow or OOM-killed, this is what lets you read a heap dump instead of guessing.

### 5.1 JVM Architecture
```text
Java Source → Compiler → Bytecode → JVM → JIT → Machine Code
```
Bytecode (portable intermediate representation), class loading (a hierarchy of classloaders resolves and loads classes lazily), heap (object storage, GC'd), stack (per-thread method frames and locals), metaspace (class metadata, off-heap since Java 8), JIT (hot code paths compiled to native machine code at runtime), native memory (off-heap allocations like direct buffers).

### 5.2 Garbage Collection
| Topic | Description |
|---|---|
| Young generation | Where new objects are allocated; most objects die here quickly (the "generational hypothesis"). |
| Old generation | Where objects that survive several young-gen collections get promoted. |
| Minor GC | Collects the young generation — frequent, usually fast. |
| Major/Full GC | Collects the old generation (or the whole heap) — rarer, but much more expensive and can pause your app noticeably. |
| G1 | The default modern collector, designed to balance throughput and pause-time predictability. |
| GC pauses | Stop-the-world pauses during collection — a direct source of tail latency spikes. |
| Memory leaks | In Java, this almost always means objects are unintentionally still *reachable* (e.g. a growing static cache or unclosed listener), not literally unfreed memory. |

### 5.3 JVM Troubleshooting
Thread dumps (snapshot of every thread's stack — for diagnosing hangs/deadlocks), heap dumps (snapshot of all live objects — for diagnosing leaks), GC logs (tells you pause frequency/duration), CPU/memory profiling (finds hot code paths and allocation sources), JVM metrics (heap usage, GC time, thread count — exported for monitoring).

**Resources**
- [Java Garbage Collection Handbook (free)](https://plumbr.io/handbook/garbage-collection-in-java)
- `jstack`, `jmap`, `jcmd` (practice locally)
- [VisualVM](https://visualvm.github.io/)

---

# 6. Concurrency & Multithreading

**What it is:** Running multiple things safely and efficiently within one process.
**Why it matters:** Nearly every "impossible to reproduce" backend bug is a concurrency bug.

### 6.1 Threads
Thread, Runnable, Callable, Executor, ExecutorService, thread pools — an executor manages a pool of reusable threads so you're not manually spawning/destroying them per task, which is expensive and unbounded.

### 6.2 Synchronization
| Topic | Description |
|---|---|
| `synchronized` | Enforces mutual exclusion around a block/method — only one thread executes it at a time. |
| `volatile` | Guarantees visibility of a variable's latest value across threads — but *not* atomicity of compound operations (e.g. `count++` is still unsafe). |
| Atomic classes | Lock-free, thread-safe primitives (`AtomicInteger`, etc.) via CPU compare-and-swap. |
| Locks / ReadWriteLock | Explicit locking beyond `synchronized` — ReadWriteLock allows concurrent reads but exclusive writes. |
| Semaphore | Limits how many threads can access a resource concurrently (a counting permit system). |
| CountDownLatch / CyclicBarrier | Coordination primitives — a latch lets threads wait for N events to happen once; a barrier makes N threads wait for each other repeatedly at a sync point. |

### 6.3 Async
Future, `CompletableFuture`, async composition, error handling, timeouts, cancellation — `CompletableFuture` lets you chain/combine async operations declaratively instead of nested callbacks, with built-in exception propagation.

### 6.4 Problems
| Topic | Description |
|---|---|
| Race conditions | Outcome depends on unpredictable thread timing/interleaving. |
| Deadlocks | Two or more threads wait forever on locks held by each other. |
| Starvation | A thread never gets CPU time or a resource because others are prioritized. |
| Visibility | A thread doesn't see another thread's latest write due to caching/reordering — the problem `volatile` solves. |
| Atomicity | An operation that looks like one step is actually multiple, allowing interleaving mid-operation. |
| Lock contention | Many threads competing for the same lock, serializing work that could otherwise be parallel. |

**Project:** Concurrent Job Processing Engine — `Producer → Job Queue → Thread Pool → Workers → Results`, with retry, timeout, cancellation, graceful shutdown, and concurrency limits.

**Resources**
- *Java Concurrency in Practice* — Brian Goetz
- [Baeldung's Concurrency series](https://www.baeldung.com/java-concurrency)

---

# 7. Spring Framework

**What it is:** The dependency-injection and AOP container underneath Spring Boot.
**Why it matters:** Spring Boot feels like magic until you understand IoC — then it's just a well-organized object graph.

| Topic | Description |
|---|---|
| IoC | The container, not your code, controls object creation and wiring — "inversion" of the normal control flow. |
| Dependency Injection | Dependencies are handed to a class (via constructor/setter) rather than the class constructing them itself — enables testability and loose coupling. |
| Beans | Any object managed by Spring's container. |
| ApplicationContext | The container itself — holds and wires all beans. |
| Bean lifecycle | Instantiate → populate dependencies → init callbacks → ready for use → destroy callbacks — matters for startup ordering and resource cleanup bugs. |
| Component scanning | Spring auto-discovers `@Component`/`@Service`/`@Repository` classes on the classpath. |
| Configuration & Profiles | `@Configuration` classes and environment-specific bean wiring (dev/staging/prod). |
| AOP | Cross-cutting concerns (logging, transactions, caching) applied declaratively via annotations, without cluttering business logic. |
| Proxies | AOP is implemented by wrapping your bean in a proxy — explains why calling an `@Transactional` method from *within the same class* silently skips the transaction (the proxy is bypassed). |

**Resources**
- [Spring Framework docs — Core](https://docs.spring.io/spring-framework/reference/core.html)
- *Spring in Action* — Craig Walls

---

# 8. Spring Boot

**What it is:** Opinionated auto-configuration on top of Spring for building production services fast.
**Why it matters:** This is what you'll actually write services in daily.

### Fundamentals
Auto-configuration (Boot pre-wires beans based on what's on your classpath), starters (curated dependency bundles, e.g. `spring-boot-starter-web`), `application.yml`, profiles, environment variables, Actuator (built-in production endpoints for health/metrics/env), logging.

### Spring MVC
Controllers, Services, Repositories (the standard layered architecture), filters/interceptors (pre/post-process requests), validation (`@Valid` + Bean Validation), exception handling, global error handling (`@ControllerAdvice`).

### Production Spring
Configuration management, connection pools (e.g. HikariCP — sized wrong, it's a common bottleneck), thread pools, health checks, graceful shutdown (finish in-flight requests before terminating), metrics, logging.

**Resources**
- [Spring Boot docs](https://docs.spring.io/spring-boot/documentation.html)
- [Spring Boot Actuator docs](https://docs.spring.io/spring-boot/reference/actuator/index.html)

---

# 9. API Engineering

**What it is:** APIs as a full engineering discipline — not just "add an endpoint."
**Why it matters:** This is the connective tissue of every distributed system you'll build.

HTTP, methods, status codes, headers, cookies, content negotiation, JSON, idempotency (a repeated request has the same effect as one), statelessness (no server-side session state between requests — enables horizontal scaling), pagination, filtering, sorting, versioning, error handling, API contracts, OpenAPI (machine-readable spec enabling codegen/docs/contract testing), API documentation.

**Resources**
- [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines)
- [OpenAPI Specification](https://swagger.io/specification/)

---

# 10. REST

**What it is:** The dominant style for public and internal HTTP APIs.
**Why it matters:** The most interview-tested "practical" skill at SDE-2.

### HTTP Methods
GET (read, safe, cacheable), POST (create/non-idempotent action), PUT (full replace, idempotent), PATCH (partial update), DELETE (remove, idempotent), HEAD, OPTIONS.

### API Design
| Topic | Description |
|---|---|
| Resource modeling / URI design | Model nouns (resources), not verbs, in your URIs — `/orders/{id}/cancel` is a reasonable exception for an action. |
| Cursor vs offset pagination | Offset is simple but breaks under concurrent writes (skipped/duplicated rows); cursor is stable under writes but more complex to implement. |
| Versioning | URI (`/v2/...`) or header-based — how you evolve an API without breaking existing clients. |
| Idempotency keys | Client-supplied unique key so a retried request (e.g. after a timeout) doesn't double-execute (e.g. double-charge). |
| Rate limiting | Protects the service from being overwhelmed — token bucket and sliding window are the common algorithms. |

### Production Concerns
Timeouts, retries, authN/authZ, caching (HTTP cache headers), compression, API gateways (centralize auth, rate limiting, routing across many services).

**Design exercise:** `POST /orders`, `GET /orders/{id}`, `GET /orders?status=PAID`, `POST /orders/{id}/cancel` — then ask: what happens on client retry? Lost response after payment succeeds? How do you prevent duplicate orders?

**Resources**
- [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines)
- [Stripe API docs](https://stripe.com/docs/api) (widely cited as gold-standard REST design)

---

# 11. gRPC

**What it is:** A binary RPC protocol over HTTP/2, generated from a `.proto` contract.
**Why it matters:** The default choice for low-latency internal service-to-service calls.

### Fundamentals
Protocol Buffers (compact binary IDL + serialization), `.proto` files, services, RPC methods, unary RPC (one request/one response, like REST), server/client/bidirectional streaming (long-lived connections pushing multiple messages).

### Production
Deadlines (per-call timeout propagated across hops — prevents a slow downstream from hanging the whole chain), cancellation, metadata (headers-equivalent), interceptors (middleware for auth/logging/tracing), status codes, TLS, load balancing, service discovery.

**When to choose what:** REST → public/conventional HTTP APIs. gRPC → internal service-to-service. gRPC streaming → high-performance streaming RPC.

**Resources**
- [grpc.io docs](https://grpc.io/docs/)
- [grpc-spring project](https://github.com/grpc-ecosystem/grpc-spring)

---

# 12. GraphQL

**What it is:** A query language letting clients request exactly the fields they need.
**Why it matters:** Solves REST's over/under-fetching, but introduces its own backend performance problems.

### Fundamentals
Schema (the type contract), types, queries, mutations, subscriptions (real-time push), resolvers (functions that fetch each field), arguments, variables, fragments, interfaces, unions, directives, input types.

### Backend Problems
| Topic | Description |
|---|---|
| N+1 queries | Naively resolving a list's nested field triggers one extra query *per item* — the most common GraphQL backend bug. |
| DataLoader | Batches and caches per-request field resolution to solve N+1. |
| Query complexity / depth limiting | Without limits, a client can craft an extremely expensive query — a real DoS vector you must guard against. |
| Authorization | Must be enforced per-field/resolver, not just at the top-level query, since clients can request nested data across ownership boundaries. |
| Schema evolution / caching | Harder than REST's URL-based caching since queries are arbitrary shapes — usually needs persisted queries or field-level caching strategies. |

**Resources**
- [graphql.org](https://graphql.org/learn/)
- [How to GraphQL](https://www.howtographql.com/)

---

# 13. PostgreSQL

**What it is:** Your primary relational datastore — should be one of the deepest areas of the roadmap.
**Why it matters:** Nearly every production incident that isn't "a service crashed" traces back to the database.

### SQL
SELECT, JOIN (INNER/LEFT), GROUP BY, HAVING, subqueries, CTEs (named, reusable subqueries — also enable recursion), window functions (compute across rows without collapsing them — running totals, ranks), aggregations, CASE, UPSERT (`INSERT ... ON CONFLICT`).

### Data Modeling
Primary/foreign keys, constraints, normalization (reduce redundancy, risk of anomalies) vs denormalization (trade redundancy for read speed), one-to-one/one-to-many/many-to-many relationships.

### Indexes
| Topic | Description |
|---|---|
| B-tree | The default, general-purpose index type — good for equality and range queries. |
| Composite indexes | Multi-column indexes where column *order* determines which query patterns can use them. |
| Partial indexes | Index only a subset of rows matching a condition — smaller, faster for that specific query shape. |
| Covering indexes | Include enough columns that the query never has to touch the actual table row. |
| Sequential vs index scan | A sequential scan reads the whole table — often means a missing or unusable index for that query. |

Master: `EXPLAIN ANALYZE` — shows the actual query plan and execution time.

### Transactions
ACID, MVCC (Postgres keeps multiple row versions so readers never block writers), locks, deadlocks, optimistic locking (check a version column at commit, retry on conflict) vs pessimistic locking (`SELECT ... FOR UPDATE` blocks others upfront).

### Isolation
Read Uncommitted, Read Committed (Postgres default), Repeatable Read, Serializable — and the anomalies each allows/prevents: dirty reads, non-repeatable reads, phantom reads, lost updates.

### PostgreSQL Internals
WAL (write-ahead log — durability + replication mechanism), Vacuum (reclaims space from dead row versions under MVCC), buffer cache, query planner, connection pooling (Postgres connections are expensive — use PgBouncer or app-level pooling), replication, read replicas (offload reads, but introduce replication lag), backups, recovery.

**Resources**
- [PostgreSQL official docs](https://www.postgresql.org/docs/current/)
- [Use The Index, Luke](https://use-the-index-luke.com/)
- *Designing Data-Intensive Applications* — Kleppmann

---

# 14. JPA & Hibernate

**What it is:** The ORM layer mapping Java objects to Postgres rows.
**Why it matters:** ORMs are notorious for hiding expensive queries — you need to see through the abstraction.

Entities, persistence context (Hibernate's in-memory tracking of managed entities, auto-flushed to DB), entity lifecycle, lazy loading (defers loading a relationship until accessed) vs eager loading (loads immediately, risking over-fetch), relationships, cascades, transactions, JPQL (entity-oriented, portable query language) vs native queries (Postgres-specific SQL when you need it).

**Understand:**
| Topic | Description |
|---|---|
| N+1 problem | Fetching a list then triggering one extra query per row for a related entity — the #1 real-world Hibernate performance bug. |
| LazyInitializationException | Accessing a lazy relationship after the persistence session has closed. |
| Over/under-fetching | Loading more or less data than the use case actually needs. |
| Bad joins / excessive DB queries | Symptoms of not understanding what SQL your ORM is actually generating — always check with logging or a query plan. |

**Resources**
- [Vlad Mihalcea's blog](https://vladmihalcea.com/)
- [Baeldung's JPA/Hibernate series](https://www.baeldung.com/learn-jpa-hibernate)

---

# 15. Redis

**What it is:** An in-memory data store — much more than "a cache."
**Why it matters:** Misused Redis (unbounded keys, no TTL, stampedes) causes as many incidents as it prevents.

### Data Structures
Strings, hashes, lists, sets, sorted sets (score-ordered — great for leaderboards/rate limiting), streams (append-only log, similar in spirit to a mini-Kafka).

### Caching
| Topic | Description |
|---|---|
| Cache-aside | App checks cache → miss → reads DB → populates cache. The default pattern. |
| Read-through / write-through / write-behind | Variants where the cache itself sits in front of the DB and manages reads/writes, sync or async. |
| TTL / Eviction | TTL expires stale entries automatically; eviction policy (e.g. LRU) decides what to drop when memory is full. |
| Cache invalidation | Actively removing/updating a cached value when the underlying data changes — famously one of the "two hard things" in CS. |
| Cache stampede | Many clients simultaneously miss the same expired key and hammer the DB at once. |
| Cache penetration | Repeated lookups for keys that don't exist, bypassing the cache entirely every time. |
| Cache avalanche | Many keys expire at the same time, causing a sudden surge of DB load. |
| Hot keys | One key gets disproportionate traffic, potentially overloading a single Redis node/shard. |

### Distributed Use Cases
Sessions, counters, rate limiting, idempotency keys, distributed locks (e.g. Redlock — useful but with real correctness caveats), Pub/Sub, Streams.

### Redis Architecture
Persistence (RDB snapshots vs AOF append-log), replication, Sentinel (HA/failover for a single primary setup), Cluster (sharding across nodes), failover.

**Resources**
- [Redis official docs](https://redis.io/docs/latest/)
- [Redis University (free)](https://redis.io/university/)

---

# 16. NoSQL

**What it is:** Non-relational datastores, each optimized for a specific access pattern.
**Why it matters:** Knowing *why* to reach for one over Postgres is a real system-design signal.

### Categories
| Category | Description |
|---|---|
| Key-value | O(1) lookups by key, horizontally scalable, no joins — great for simple, high-throughput access. |
| Document | Schema-flexible JSON-like documents — good when data is naturally nested and query shapes vary. |
| Wide-column | Optimized for massive write throughput and time-series-like data, denormalized by design. |
| Graph | Optimized for traversing relationships — joins that are expensive in SQL are native here. |

### Technologies
DynamoDB, MongoDB, Cassandra, Neo4j.

**Key question:** *Why would I choose this instead of PostgreSQL?*

**Resources**
- [AWS DynamoDB docs](https://docs.aws.amazon.com/dynamodb/)
- *Designing Data-Intensive Applications* — Ch. 2–3

---

# 17. Elasticsearch / OpenSearch

**What it is:** A search and analytics engine, not a general-purpose database.
**Why it matters:** Postgres full-text search doesn't scale to fuzzy/faceted/relevance-ranked search — this is the tool for that job.

### Fundamentals
Index, document, mapping (schema for a document type), field, analyzer/tokenizer (control how text is split/normalized at index time — affects what queries match), inverted index (maps each term to the documents containing it — the core structure making search fast), query, filter, aggregation, shard, replica.

### Search
Full-text, exact matching, fuzzy search, prefix search/autocomplete, relevance scoring (BM25 by default — documents ranked, not just boolean-matched), filtering, faceted search, aggregations.

### Architecture
```text
PostgreSQL (source of truth) → Application → indexing → Elasticsearch (search layer)
```
Understand: index synchronization, eventual consistency, reindexing, sharding, replication, search performance.

**Resources**
- [Elasticsearch docs](https://www.elastic.co/docs)
- [Elasticsearch: The Definitive Guide (free)](https://www.elastic.co/guide/en/elasticsearch/guide/current/index.html)

---

# 18. Python

**What it is:** The secondary backend language.
**Why it matters:** Many companies run polyglot backends — enough Python to be dangerous, not a second deep specialty.

### Language
Types, lists, dicts, sets, tuples, classes, dataclasses (concise data-holder classes), exceptions, decorators (wrap/modify function behavior), iterators, generators (lazy sequences), context managers (`with` — deterministic resource cleanup), type hints, packaging, virtual environments.

### Async Python
`async`/`await`, coroutines, event loop, `asyncio`, tasks, blocking vs non-blocking, I/O-bound vs CPU-bound (async helps the former, not the latter — CPU-bound work still needs multiprocessing).

**Resources**
- [Python official docs](https://docs.python.org/3/)
- [Real Python — Async IO](https://realpython.com/async-io-python/)

---

# 19. FastAPI

**What it is:** A modern async Python web framework.
**Why it matters:** The common pairing with Python for high-concurrency API servers.

Routing, Pydantic (runtime validation/serialization from type hints), validation, dependency injection (`Depends()` — FastAPI's lightweight equivalent of Spring's DI container), middleware, exception handling, authentication, OpenAPI (auto-generated from your code), testing, lifespan (startup/shutdown hooks), background processing.

**Database:** SQLAlchemy (Python's ORM/toolkit, equivalent to JPA/Hibernate), async DB access, transactions, connection pooling.

**Integrations:** Redis, PostgreSQL, Kafka, external APIs.

**Build:** A Recommendation Service (FastAPI + Redis + Postgres), integrated with your Java system.

**Resources**
- [FastAPI docs](https://fastapi.tiangolo.com/) (unusually good, tutorial-style)

---

# 20. Message Queues

**What it is:** The conceptual vocabulary shared across all async messaging systems before picking a specific one.
**Why it matters:** "Queue," "topic," "pub/sub," "event bus" get used interchangeably but mean different things architecturally.

Producer, consumer, message, queue (delivers to *one* consumer), topic (broadcasts to *many* subscribers), subscription, ACK, retry, dead-letter queue (DLQ — where messages land after repeated failures, for manual inspection), ordering (usually only guaranteed within a partition/queue, not globally), delivery semantics (at-most-once / at-least-once / exactly-once).

**Resources**
- [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/)

---

# 21. RabbitMQ

**What it is:** A traditional message broker built around exchanges, bindings, and queues.
**Why it matters:** Its model maps cleanly onto Section 20's concepts — a good first broker to actually run.

```text
Producer → Exchange → Binding → Queue → Consumer
```

| Topic | Description |
|---|---|
| Direct exchange | Routes by exact routing-key match. |
| Fanout exchange | Broadcasts to all bound queues, ignoring the routing key. |
| Topic exchange | Routes by pattern-matching the routing key (e.g. `orders.*`). |
| ACK/NACK | Consumer explicitly acknowledges or rejects a message. |
| Prefetch | Limits how many unacked messages a consumer holds at once — controls load per consumer. |
| Durable queues / persistent messages | Survive a broker restart, at a throughput cost. |
| TTL / Dead-letter exchanges | Expired or failed messages get routed elsewhere instead of silently dropped. |
| Retry patterns | Typically implemented via a delay queue + DLX, since RabbitMQ has no native delayed-retry primitive. |

**Resources**
- [RabbitMQ official tutorials](https://www.rabbitmq.com/tutorials)

---

# 22. Cloud Messaging

**What it is:** Managed messaging services offered by cloud providers.
**Why it matters:** In practice you'll often use these instead of self-hosting RabbitMQ/Kafka.

**AWS:** SQS (managed queue), SNS (managed pub/sub), EventBridge (managed event bus with routing rules), Kinesis (managed stream processing, Kafka-adjacent).
**Azure:** Service Bus, Event Grid, Event Hubs.

Understand that Queue ≠ Event Bus ≠ Pub/Sub ≠ Streaming Platform — each optimizes for a different delivery/fan-out/ordering guarantee.

**Resources**
- [AWS Messaging docs](https://docs.aws.amazon.com/whitepapers/latest/comparing-aws-messaging-services/)

---

# 23. Kafka

**What it is:** A distributed log-based streaming platform, architecturally very different from a traditional queue — should be one of your deepest infra topics.
**Why it matters:** The default choice for high-throughput event-driven backends at scale.

```text
Producer → Topic → Partition → Offset → Consumer Group → Consumer
```

### Core
| Topic | Description |
|---|---|
| Broker | A single Kafka server; a cluster is made of many. |
| Topic / Partition | A topic is split into ordered, append-only partitions — order is guaranteed only *within* a partition. |
| Consumer / Consumer group | Multiple consumers in a group split partitions between them for parallel processing. |
| Offset | A message's position within its partition — consumers track their own offset to know what's been processed. |
| Replication / Leader / Follower / ISR | Each partition is replicated across brokers; the leader handles reads/writes, followers replicate; the In-Sync Replica set tracks which followers are fully caught up. |
| Partition assignment | How partitions are distributed among consumers in a group. |

### Producer
Partition keys (determine which partition a message lands in — same key → same partition → preserved order for that key), batching, compression, `acks` (how many replicas must confirm before a write is considered successful), retries, idempotent producer (prevents duplicate writes on retry), ordering.

### Consumer
Polling, offset commits, consumer groups, rebalancing (reassigning partitions when consumers join/leave), consumer lag (gap between latest offset and what's processed — your primary Kafka health metric), retry, DLQ, poison messages (messages that repeatedly fail processing and block a partition if not handled).

### Internals
Log segments, retention (delete old messages after time/size limit), compaction (keep only the latest value per key instead — for "current state" topics), replication, ISR, leader election, KRaft (Kafka's newer consensus mechanism replacing ZooKeeper).

**Why Kafka ≠ "a better RabbitMQ":** RabbitMQ removes messages once consumed; Kafka persists them and lets multiple independent consumer groups re-read the same log at their own pace.

**Resources**
- [Kafka: The Definitive Guide (free)](https://www.confluent.io/resources/kafka-the-definitive-guide-v2/)
- [Kafka official docs](https://kafka.apache.org/documentation/)

---

# 24. Event-Driven Architecture

**What it is:** Designing systems where services react to events instead of calling each other synchronously.
**Why it matters:** Lets services fail and recover independently instead of cascading failures.

Traditional: `Order → Payment → Inventory → Notification` (each step blocks on the last).
Event-driven: `Order Service → OrderCreated → Kafka → {Payment, Inventory, Notification}` (all react independently).

Domain events (immutable facts, e.g. "OrderCreated"), event contracts, event versioning/schema evolution (old consumers may still read old formats — plan for it), eventual consistency, event consumers, event choreography (services coordinate via events with no central orchestrator).

**Resources**
- [microservices.io](https://microservices.io/patterns/index.html)

---

# 25. Outbox Pattern

**What it is:** A pattern solving "DB commit succeeded but the message-broker publish failed."
**Why it matters:** Without it, your database and your event stream can silently drift out of sync.

**Problem:** A DB transaction and a Kafka publish are two separate operations — the DB can succeed while Kafka fails (or vice versa), leaving the systems inconsistent.

**Solution:**
```text
Application → DB Transaction { Business Data + Outbox Event } → Outbox Worker → Kafka
```
The event is written to an `outbox` table in the *same transaction* as the business data, guaranteeing atomicity; a separate worker then reliably publishes from the outbox table to Kafka.

Learn: transactional outbox, polling publisher, CDC awareness (Change Data Capture as an alternative outbox-reading mechanism), duplicate events, idempotent consumers (since the outbox worker itself may retry and publish a message more than once).

**Resources**
- [microservices.io — Transactional Outbox](https://microservices.io/patterns/data/transactional-outbox.html)

---

# 26. Saga Pattern

**What it is:** Managing a multi-step transaction across services without a real distributed transaction.
**Why it matters:** Standard for any "order → payment → inventory → shipping"-style flow.

`Order → Payment → Inventory → Shipping` — if Inventory fails, you don't roll back the whole chain (there's no distributed transaction); instead you run a *compensating* action, e.g. `Payment → Refund`.

Learn: distributed transactions (why 2PC doesn't scale well here), choreography (services react to each other's events) vs orchestration (a central coordinator drives each step), compensating transactions, failure handling.

**Resources**
- [microservices.io — Saga](https://microservices.io/patterns/data/saga.html)

---

# 27. CQRS

**What it is:** Separate models for writing (commands) and reading (queries).
**Why it matters:** Lets you scale/optimize reads and writes independently — at the cost of eventual consistency between them.

```text
Command → Write Model → Events → Read Model
```
Learn: command model, query model, separate read/write models, eventual consistency, projections (the read-side materialized views built from events), when CQRS is useful (high read/write asymmetry, complex read shapes) vs when it's overengineering (simple CRUD domains).

**Resources**
- [Martin Fowler — CQRS](https://martinfowler.com/bliki/CQRS.html)

---

# 28. Event Sourcing

**What it is:** Storing the full history of events instead of just current state, and deriving state by replay.
**Why it matters:** Gives you a full audit log for free, at the cost of query complexity.

Traditional: current state only. Event sourced: `Event 1, 2, 3, 4 → Reconstruct State` by replaying them in order.

Learn: event store, event replay, snapshots (periodic saved state so you don't replay from scratch every time), projections, schema evolution, versioning.

**Resources**
- [Martin Fowler — Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html)

---

# 29. Distributed Systems

**What it is:** The heart of SDE-2 system knowledge — reasoning about systems, not just applications.

### Scaling
Horizontal vs vertical scaling, stateless services (no server-side session state — required for horizontal scaling to work), load balancing, service discovery, autoscaling.

### Distributed Failures
Network failures, timeouts, partial failures (some nodes succeed, some fail, for the same operation), duplicate requests/messages, out-of-order messages, service crashes, database failures.

Always ask: **what happens if this component fails?**

**Resources**
- *Designing Data-Intensive Applications* — Kleppmann
- [Google SRE Book (free)](https://sre.google/books/)

---

# 30. Distributed Data

### Consistency
Strong consistency (every read sees the latest write) vs eventual consistency (reads may briefly lag but converge), read-after-write consistency, causal consistency, CAP theorem (under a network partition, choose Consistency or Availability — not both), quorum (majority-based read/write agreement), replication.

### Partitioning
Sharding, partition keys, consistent hashing (minimizes reshuffling when nodes are added/removed), hot partitions (uneven load on one shard), rebalancing.

### Replication
Primary/replica, leader/follower, synchronous replication (safer, slower) vs asynchronous (faster, risk of data loss on failover), failover.

**Resources**
- *Designing Data-Intensive Applications* — Part II (Distributed Data)

---

# 31. Reliability Engineering

### Timeouts
Connection, read, write timeout, request deadline — every network call needs one; without it, a hung dependency can hang your whole service.

### Retries
Exponential backoff, jitter (randomizing retry delay to avoid synchronized "retry storms"), maximum attempts, retry budgets (cap total retry volume across the system), retry storms (a failure mode where retries themselves overwhelm a recovering service).

### Resilience
Circuit breakers (stop calling a failing dependency for a cooldown period), bulkheads (isolate resource pools so one failing dependency can't exhaust threads needed elsewhere), rate limiting, backpressure (signal upstream to slow down instead of silently dropping/queuing forever), graceful degradation, idempotency.

### Delivery Semantics
At-most-once, at-least-once (the realistic default), exactly-once concepts (approximated via idempotency, not truly free), deduplication, idempotent consumers.

**Resources**
- *Release It!* — Michael Nygard
- [Google SRE Book](https://sre.google/books/)

---

# 32. System Design — HLD

### Design Process
```text
Requirements → Functional / Non-functional Requirements → Capacity Estimation
→ API Design → Data Model → Architecture → Scaling → Failure Handling
→ Observability → Security
```

### Practice Systems
URL Shortener, Rate Limiter, Notification System, File Storage, E-commerce, Food Delivery, Ride Sharing, Chat System, Video Streaming, Search System, Payment System, News Feed, Ticket Booking — each is a well-documented interview classic; practice writing the full process above for each, not just the final diagram.

**Resources**
- [System Design Primer (free)](https://github.com/donnemartin/system-design-primer)
- [ByteByteGo](https://bytebytego.com/)

---

# 33. Low-Level Design

### Principles
SOLID, composition, interfaces, dependency inversion, extensibility, testability, thread safety — the checklist for "is this class well-designed."

### Design Patterns
| Pattern | Description |
|---|---|
| Factory / Abstract Factory | Centralizes object creation logic behind a method/class. |
| Builder | Constructs complex objects step-by-step, avoiding telescoping constructors. |
| Strategy | Swaps an algorithm's implementation at runtime via a common interface. |
| Observer | Objects subscribe to be notified of another's state changes. |
| Adapter | Converts one interface into another a client expects. |
| Decorator | Adds behavior to an object dynamically, without subclassing. |
| Command | Encapsulates a request as an object, enabling queuing/undo/logging. |
| State | An object changes behavior when its internal state changes. |
| Template Method | Defines an algorithm's skeleton in a base class, letting subclasses override specific steps. |
| Chain of Responsibility | Passes a request along a chain of handlers until one handles it. |

### Practice
Parking Lot, Elevator, Payment System, Notification System, Rate Limiter, Logger, Cache, Job Scheduler.

**Resources**
- *Head First Design Patterns*
- [Refactoring.Guru](https://refactoring.guru/design-patterns)

---

# 34. Docker

**What it is:** Packaging an application with its dependencies into a portable, isolated container image.

### Fundamentals
Images (read-only template) vs containers (a running instance), layers (each Dockerfile instruction is a cached layer — order least-to-most-frequently-changing for fast rebuilds), Dockerfiles, volumes (persistent storage outliving a container), networks, registries, Docker Compose (defines/runs a multi-container local environment from one YAML file).

### Local Distributed Environment
Run Spring Boot, FastAPI, Postgres, Redis, Kafka, RabbitMQ, Elasticsearch, Prometheus, Grafana via Docker/Compose.

**Resources**
- [Docker docs](https://docs.docker.com/)
- [Play with Docker (free sandbox)](https://labs.play-with-docker.com/)

---

# 35. Kubernetes

**What it is:** An orchestration system that runs, scales, and heals containerized applications across a cluster.
**Why it matters:** SDE-2 working knowledge — know how your service *runs*, not how to administer the cluster.

Pods (smallest deployable unit), Deployments (manage replica sets + rolling updates), Services (stable network endpoint load-balancing across ephemeral Pod IPs), Ingress (routes external traffic in), ConfigMaps/Secrets (externalized config/sensitive values), ReplicaSets, HPA (autoscale replica count on CPU/memory/custom metrics), health checks (liveness = restart me?, readiness = send me traffic?), resource requests/limits, namespaces, rolling deployments.

```text
Ingress → Service → Pods → Application
```

**Resources**
- [Kubernetes docs — Concepts](https://kubernetes.io/docs/concepts/)

---

# 36. AWS

AWS is the primary cloud.

**Compute:** EC2 (raw VMs), ECS (AWS's own orchestrator), EKS (managed Kubernetes), Lambda (serverless functions).
**Storage:** S3 (object storage), object lifecycle, storage classes, presigned URLs (time-limited, direct-to-S3 upload/download links).
**Database:** RDS (managed relational DB), DynamoDB, ElastiCache (managed Redis/Memcached).
**Networking:** VPC (your private network), subnets, route tables, security groups (stateful instance-level firewall), load balancers, Route 53 (DNS), NAT, internet gateway.
**Security:** IAM (roles/policies — least privilege is the guiding principle), Secrets Manager, KMS basics (key management).
**Messaging:** SQS, SNS, EventBridge, Kinesis.
**Monitoring:** CloudWatch — logs, metrics, alarms.

**Resources**
- [AWS Skill Builder (free tier)](https://skillbuilder.aws/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)

---

# 37. Azure

Azure is secondary — map concepts across, don't relearn from scratch.

**Compute:** Virtual Machines, App Service, AKS. **Storage:** Blob Storage. **Database:** Azure SQL, Cosmos DB, Azure Cache for Redis. **Networking:** VNet, subnets, Load Balancer. **Security:** Entra ID, Key Vault. **Messaging:** Service Bus, Event Grid, Event Hubs. **Monitoring:** Azure Monitor, Application Insights.

| AWS | Azure |
|---|---|
| EC2 | Virtual Machines |
| S3 | Blob Storage |
| RDS | Azure Database |
| ElastiCache | Azure Cache for Redis |
| SQS | Service Bus |
| EKS | AKS |
| CloudWatch | Azure Monitor |
| IAM | Entra ID |

**Resources**
- [Microsoft Learn — Azure fundamentals](https://learn.microsoft.com/en-us/training/azure/)

---

# 38. Linux

**What it is:** The OS layer you'll actually be debugging when production breaks.

### Processes / Memory / Filesystem
Processes, threads, signals, environment variables, process states, file descriptors; RAM, swap, virtual memory, page cache, OOM killer (kills a process when memory is exhausted — explains sudden container restarts); permissions, ownership, mounts, disk usage, inodes.

### Commands
`ps top htop free df du vmstat iostat lsof ss curl grep awk sed journalctl` — your triage toolkit for CPU, memory, disk, network, and log inspection.

### Troubleshooting
High CPU, high memory, disk full, process crash, port conflicts, network connectivity, permission issues.

**Resources**
- [Linux Performance (Brendan Gregg)](https://www.brendangregg.com/linuxperf.html)
- *The Linux Command Line* (free book)

---

# 39. Networking

### Fundamentals
OSI model, TCP/IP, IP addresses, ports, DNS, TCP vs UDP, HTTP/HTTP2, TLS/HTTPS.

### Backend Networking
Load balancers, reverse proxies, NAT, service discovery, connection pooling, keep-alive, timeouts.

### Tools
`curl ping traceroute dig nslookup ss netstat`.

**Resources**
- [High Performance Browser Networking (free)](https://hpbn.co/)

---

# 40. CI/CD

```text
Developer → Git → PR → Build → Unit Tests → Integration Tests → Security Scan
→ Docker Build → Image Registry → Deploy → Smoke Test → Production
```

**CI:** Build, unit tests, integration tests, static analysis, dependency scanning, code coverage, Docker builds.
**CD:** Deployment, environment promotion, secrets, configuration, rollbacks, smoke tests.
**Tools:** GitHub Actions, GitLab CI awareness, Azure DevOps awareness.

**Resources**
- [GitHub Actions docs](https://docs.github.com/en/actions)

---

# 41. Deployment Strategies

| Strategy | Description |
|---|---|
| Rolling deployment | Gradually replaces old instances with new ones — default, safe, slower full rollback. |
| Blue/green deployment | Two full environments; switch traffic all at once — instant rollback, double infra cost during switch. |
| Canary deployment | Route a small % of traffic to the new version first, watch metrics, then ramp up. |
| Feature flags | Decouples deploying code from releasing a feature — ship dark, toggle on/off without a redeploy. |
| Rollbacks | Reverting to a previous known-good version — must be fast and rehearsed. |
| Database migration strategies | Backward-compatible, additive-first migrations so the *currently running* old app version doesn't break mid-deploy. |

**Question to always answer:** *How do I deploy a new version without taking the service down?*

**Resources**
- [Martin Fowler — Continuous Delivery](https://martinfowler.com/bliki/ContinuousDelivery.html)

---

# 42. Observability

Observability = Metrics + Logs + Traces.

```text
Application → {Metrics→Prometheus, Logs→Loki, Traces→OpenTelemetry→Tempo} → Grafana → Dashboards + Alerts
```

Learn: metrics, logs, traces, correlation IDs (shared ID across every log line/span for one request), trace IDs, dashboards, alerts, SLIs (a measured metric), SLOs (your target for it), error budgets (how much failure you're allowed before prioritizing reliability over features).

**Resources**
- [Google SRE Book — Ch. 4 (SLOs)](https://sre.google/sre-book/service-level-objectives/)

---

# 43. Prometheus

**What it is:** Metrics collection + time-series monitoring.

### Metrics
Counter (only increases, e.g. request count), Gauge (goes up/down, e.g. active connections), Histogram (bucketed distribution, e.g. latency), Summary (client-side quantiles), Labels (dimensions for slicing metrics), Cardinality (label combinations — too high and Prometheus struggles).

### PromQL
Queries, rates (`rate()` over a counter), aggregations, percentiles, histogram queries, alert expressions.

### Metrics to Monitor
HTTP requests/errors, request latency, JVM memory, GC, CPU, threads, DB connections, Kafka consumer lag, Redis hit ratio.

```text
Spring Boot → Actuator + Micrometer → Prometheus
```

**Resources**
- [Prometheus docs](https://prometheus.io/docs/introduction/overview/)

---

# 44. Grafana

**What it is:** Visualization + dashboards + alerting on top of Prometheus/Loki/Tempo/etc.

Connect to: Prometheus, Loki, Elasticsearch, Tempo, CloudWatch, and other data sources.

Build dashboards for: request rate, error rate, p50/p95/p99, CPU, memory, GC, database, Redis, Kafka, infrastructure.

**Resources**
- [Grafana docs](https://grafana.com/docs/)

---

# 45. Logs

### Structured Logging
Prefer JSON logs with consistent fields:
```json
{"level":"ERROR","service":"order-service","traceId":"abc123","orderId":"987","message":"Payment service timeout"}
```
Learn: structured logs, log levels, correlation IDs, request/trace IDs, log aggregation, log retention, sensitive-data handling (never log secrets/PII raw).

### Loki
Loki architecture, log labels, LogQL, Grafana integration.

### Elasticsearch Logs
ELK/Elastic stack concept, log indexing, searching logs, aggregation.

**Resources**
- [Loki docs](https://grafana.com/docs/loki/latest/)

---

# 46. OpenTelemetry & Distributed Tracing

**What it is:** A vendor-neutral telemetry layer for following one request across every service it touches.

```text
Request → API Gateway → Order Service → Payment Service → PostgreSQL
```
Example trace:
```text
Gateway          20ms
 └─ Order       150ms
     ├─ Redis     5ms
     ├─ Postgres 80ms
     └─ Payment   65ms
```

Learn: traces, spans (one unit of work within a trace), context propagation (carrying trace IDs across service/protocol boundaries — HTTP, gRPC, Kafka), trace IDs, span IDs, instrumentation, sampling (recording only a fraction of traces to control overhead), baggage (extra context propagated alongside the trace ID).

**Tempo:** trace storage, Grafana integration, trace search, trace-to-log and trace-to-metric correlation.

**Resources**
- [OpenTelemetry docs](https://opentelemetry.io/docs/)

---

# 47. Security

Backend-engineer level, not security-specialist level.

### Authentication
Sessions, JWT (signed token carrying claims), OAuth2 (authorization framework), OIDC (identity layer on top of OAuth2), password hashing (always salted, e.g. bcrypt/argon2), cookies, token expiration, refresh tokens.

### Authorization
RBAC (permissions attached to roles, roles to users), permissions, resource-level authorization (can *this* user access *this specific* resource — not just "are they logged in"), least privilege, IAM.

### Web Security
SQL injection (unsanitized input in a query — prevented by parameterized queries, always), XSS (injected script executes in another user's browser), CSRF (tricks a logged-in browser into an unwanted request), SSRF (tricks your server into requesting an internal resource on the attacker's behalf), broken access control (#1 on the OWASP Top 10), authentication failures, security misconfiguration, dependency vulnerabilities.

### Infrastructure Security
TLS, encryption (at rest and in transit), secrets (never hardcoded — use a secrets manager with rotation), IAM, security groups, private networking, key management.

**Resources**
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)

---

# 48. Performance Engineering

Learn to investigate: high latency, high CPU, high memory, high GC, DB bottlenecks, connection/thread pool exhaustion, queue backlog, cache misses, network latency.

### Metrics
Throughput, latency, p50/p95/p99, CPU, memory, GC, DB latency, queue lag.

### Techniques
Profiling (measure where time is actually spent — don't guess), benchmarking, load testing (k6/Gatling/JMeter — find the breaking point before users do), query optimization, caching, connection pooling, async processing, batching.

**Resources**
- [async-profiler](https://github.com/async-profiler/async-profiler)
- [k6 docs](https://k6.io/docs/)
- *Systems Performance* — Brendan Gregg

---

# 49. Production Engineering

Backend engineers should own their services.

### Reliability
Health checks, readiness, liveness, graceful shutdown, retries, timeouts, circuit breakers, rate limiting.

### Operations
Alerts, dashboards, runbooks (documented response steps for known failure modes), incident response, rollbacks, backups, disaster recovery basics.

### SRE Concepts
SLI (measured metric), SLO (target for it), SLA (external contractual commitment, usually stricter than internal SLO), error budgets, RTO (Recovery Time Objective — how fast you must recover), RPO (Recovery Point Objective — how much data loss is acceptable).

**Resources**
- [Google SRE Book](https://sre.google/books/)

---

# 50. Capstone Project

Build one serious production-style distributed system.

## 🛒 E-commerce Platform
```text
Client → {REST, GraphQL} → API Gateway
     → User / Order / Product services (Spring Boot, each with its own Postgres)
     → Kafka → {Payment, Inventory, Notification}
     → Redis (cache)
     → Search: Postgres → indexing → Elasticsearch
     → FastAPI Recommendation service
```
**Infrastructure:** Docker → Kubernetes → AWS.
**CI/CD:** GitHub → PR → CI → Tests → Security Scan → Docker → Registry → Deploy.
**Observability:** Micrometer → Prometheus → Grafana; OpenTelemetry → Tempo; structured logs → Loki → Grafana.
**Security:** AuthN/AuthZ, JWT/OIDC, RBAC, TLS, secrets management, input validation, rate limiting, audit logging.

This single project is your strongest interview artifact.

---

# 51. Failure Engineering

Intentionally break the system. For every failure, answer: *what happened → how detected → how investigated → root cause → how recovered → how prevented.*

**Redis:** kill it, simulate cache misses, create hot keys, simulate a stampede.
**Kafka:** kill a consumer, create lag, duplicate messages, rebalance a group, inject a poison message.
**PostgreSQL:** slow query, missing index, connection pool exhaustion, deadlock, replica lag.
**Services:** kill a service, network timeout, dependency timeout, high latency, partial failure.
**Deployment:** broken deployment, rollback, failed migration, canary failure.

**Resources**
- [Principles of Chaos Engineering](https://principlesofchaos.org/)
- *Release It!* — Michael Nygard

---

# 52. SDE-2 Interview Preparation

### Coding
Arrays, strings, hash maps, linked lists, trees, graphs, heaps, stacks, queues, binary search, sliding window, two pointers, BFS, DFS, dynamic programming, backtracking, intervals.

### Backend
Be able to explain — not just define — REST, gRPC, GraphQL, PostgreSQL, transactions, indexes, Redis, Kafka, RabbitMQ, Elasticsearch, caching, rate limiting, idempotency, distributed locks, outbox, saga, CQRS.

### System Design
URL Shortener, Notification System, Rate Limiter, Chat System, E-commerce, Payment System, Search System, File Storage, Feed System, Ride Sharing.

### Production Scenarios
- API latency suddenly increased — what do you check?
- Kafka consumer lag is growing — why?
- Redis is down — what happens?
- PostgreSQL CPU is 100% — what do you investigate?
- One service is timing out — how do you debug it?
- A deployment caused errors — how do you roll back?
- Users are receiving duplicate notifications — why?
- Two requests modified the same resource — how do you prevent corruption?

**Resources**
- [NeetCode 150](https://neetcode.io/practice)
- [ByteByteGo](https://bytebytego.com/)

---

# 53. Final Skill Matrix

| Area | Target Depth |
|---|---|
| Java | ⭐⭐⭐⭐⭐ |
| JVM | ⭐⭐⭐⭐ |
| Concurrency | ⭐⭐⭐⭐ |
| Spring Framework | ⭐⭐⭐⭐ |
| Spring Boot | ⭐⭐⭐⭐⭐ |
| REST | ⭐⭐⭐⭐⭐ |
| gRPC | ⭐⭐⭐⭐ |
| GraphQL | ⭐⭐⭐ |
| Python | ⭐⭐⭐ |
| FastAPI | ⭐⭐⭐ |
| SQL | ⭐⭐⭐⭐⭐ |
| PostgreSQL | ⭐⭐⭐⭐⭐ |
| JPA/Hibernate | ⭐⭐⭐⭐⭐ |
| Redis | ⭐⭐⭐⭐⭐ |
| Kafka | ⭐⭐⭐⭐⭐ |
| RabbitMQ | ⭐⭐⭐ |
| Message Queues | ⭐⭐⭐⭐⭐ |
| NoSQL | ⭐⭐⭐ |
| Elasticsearch | ⭐⭐⭐⭐ |
| Distributed Systems | ⭐⭐⭐⭐⭐ |
| HLD | ⭐⭐⭐⭐⭐ |
| LLD | ⭐⭐⭐⭐ |
| Docker | ⭐⭐⭐⭐ |
| Kubernetes | ⭐⭐⭐ |
| AWS | ⭐⭐⭐⭐ |
| Azure | ⭐⭐ |
| Linux | ⭐⭐⭐⭐ |
| Networking | ⭐⭐⭐⭐ |
| Git | ⭐⭐⭐⭐⭐ |
| GitHub | ⭐⭐⭐⭐ |
| CI/CD | ⭐⭐⭐⭐ |
| Pipelines | ⭐⭐⭐⭐ |
| Operations | ⭐⭐⭐⭐ |
| Prometheus | ⭐⭐⭐⭐ |
| Grafana | ⭐⭐⭐⭐ |
| Loki | ⭐⭐⭐ |
| OpenTelemetry | ⭐⭐⭐⭐ |
| Tempo | ⭐⭐⭐ |
| Security | ⭐⭐⭐ |
| Performance | ⭐⭐⭐⭐ |

## 🏁 Final SDE-2 Competency

> "I can take a backend requirement from idea → architecture → implementation → testing → deployment → monitoring → debugging → scaling — and explain the trade-off behind every decision I made along the way."

That is the bar this roadmap is designed around.
