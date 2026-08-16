# Cella — Project Vision

1. Vision
2. Purpose
3. What Cella Is
4. Who Cella Is For
5. What Cella Should Become
6. Core Capabilities
7. Reliability & Quality Goals
8. Learning & Transparency Philosophy
9. Scope
10. Non-Goals
11. Engineering Principles
12. Success Criteria
13. Long-Term Direction

# Cella — Project Vision

## 1. Vision

Cella aims to become a **lightweight, reliable, developer-friendly relational database** that developers can actually use to build small and medium-sized applications and projects.

Cella is also intended to be an unusually transparent database project. Its implementation, design decisions, experiments, benchmarks, documentation, and development history should allow anyone interested in databases to study how a database is built from the ground up and use that knowledge to build their own.

The long-term vision is therefore twofold:

1. Build a genuinely usable database.
2. Make the complete journey of building that database understandable to others.

---

## 2. Why Cella Exists

Cella exists because I genuinely want to build a database.

I have used databases while building applications, but I want to understand what happens underneath the interfaces developers normally interact with.

I want to understand how data moves through a database, how it is stored and retrieved, how memory and storage are involved, how operating-system facilities and system calls are used, how indexes and transactions work, how concurrency is handled, and how all these different systems come together to form a database that other software can actually use.

The project is driven primarily by curiosity and the desire to build something of my own.

I am inspired by engineers who build difficult and useful systems that make other people's lives easier. I want to experience that process myself by building something in my own way and with my own identity.

The benefit Cella may provide to my portfolio or resume is a result of the work, not the primary reason for building it.

---

## 3. What Cella Is

Cella is a **relational database engine**.

Its design is centered around the concepts that make relational databases useful for application development, including:

- databases and schemas
- tables
- rows and columns
- data types
- relationships
- SQL
- indexes
- constraints
- transactions
- persistent storage

Cella is not intended to reproduce every feature of mature systems such as PostgreSQL or MySQL.

Instead, it will provide the core capabilities necessary for developers to build normal applications within Cella's intended scope.

---

## 4. Who Cella Is For

### Primary users

Cella is intended for developers who are building:

- personal projects
- college projects
- prototypes
- small applications
- small and medium-sized services
- projects where a lightweight relational database is appropriate

Cella should provide a simpler and lighter experience for workloads that do not require the operational complexity and scale of mature enterprise database systems.

### Learning audience

Cella is also intended for developers and students who want to understand how databases work internally.

A person should eventually be able to study the repository and understand not only how Cella works, but why its components exist and how the different layers interact.

---

## 5. What Cella Should Eventually Provide

Cella should eventually provide the core capabilities needed to build ordinary applications using a relational database.

These capabilities include, at an appropriate level of maturity:

### Data definition

Developers should be able to define and manage the structure of their data through concepts such as:

- databases
- tables
- columns
- data types
- constraints

### Data manipulation

Developers should be able to:

- insert data
- retrieve data
- update data
- delete data

### Querying

Cella should support useful relational queries, including the fundamental operations required by normal applications.

The exact SQL feature set will be defined progressively as the database architecture develops.

### Relationships and integrity

Cella should support the relational concepts necessary to maintain meaningful and consistent data, including appropriate constraints and relationships.

### Indexing

Developers should be able to use indexes to improve data retrieval without requiring every query to scan an entire dataset.

### Transactions

Cella should provide transactions with clearly defined behavior for committing and rolling back changes.

### Persistence

Data should remain available after the Cella process exits and restarts.

### Recovery

Cella should be able to recover from defined failure scenarios and maintain the integrity of committed data according to its durability guarantees.

### Concurrency

Cella should eventually support safe concurrent access according to clearly defined transaction and isolation semantics.

These capabilities will evolve through the development milestones rather than being implemented all at once.

---

## 6. Reliability and Correctness

Cella should be reliable within its intended scope.

For me, reliability means that users should be able to trust the guarantees Cella makes.

In particular, if Cella reports that a transaction has been successfully committed, the committed data should not mysteriously disappear after an unexpected crash or restart within Cella's defined durability model.

Reliability should therefore be treated as an engineering property that is tested and measured rather than simply claimed.

This will eventually involve areas such as:

- transaction correctness
- durability
- crash recovery
- consistency
- concurrency
- failure testing
- automated tests
- benchmarks and validation

Cella does not initially aim to provide the scale, availability, security, operational maturity, or production guarantees of mature systems such as PostgreSQL.

However, Cella should still strive to be dependable for the workloads it is designed to support.

---

## 7. Learning and Transparency Philosophy

One of the core purposes of Cella is understanding.

Whenever Cella depends on an underlying system, I should understand that system to a level where I can explain:

1. why Cella needs it;
2. what role it plays;
3. what happens underneath it; and
4. how it affects the behavior of Cella.

This may require learning concepts from areas such as:

- C and C++
- operating systems
- computer architecture
- memory
- filesystems
- storage
- system calls
- concurrency
- networking
- database internals
- distributed systems

The project will follow a learning cycle:

```text
Learn
  ↓
Experiment
  ↓
Implement
  ↓
Investigate deeper
  ↓
Document
  ↓
Test
  ↓
Measure
  ↓
Continue
```

The goal is not to learn every possible prerequisite before writing any code. Instead, concepts should be learned when they become relevant, experimented with, implemented, and then studied more deeply as necessary.

---

## 8. Transparency as a Core Feature

Cella should not be treated as a black box.

The project should make its internal behavior understandable through:

- source code
- architecture documentation
- technical explanations
- experiments
- benchmarks
- design decisions
- development history
- debugging tools

Cella should eventually provide developer-oriented tools such as:

```text
cella inspect
cella inspect-page
cella inspect-index
cella stats
cella benchmark
```

and potentially additional inspection and diagnostic tools as the system evolves.

The goal of these tools is not only operational convenience. They should make it possible to see and understand what the database is actually doing internally.

---

## 9. Engineering Principles

### Lightweight First

Cella should prioritize a lightweight and understandable architecture.

When simplicity and performance conflict, Cella should generally prefer the simpler design initially. Performance improvements can be introduced later through measurement and experimentation.

### Minimize External Dependencies

Cella should minimize unnecessary external dependencies.

Libraries may be used when they provide genuine value, but important dependencies should be understood rather than introduced blindly.

The goal of building Cella from scratch is not to recreate every utility that already exists. The focus should remain on understanding and implementing the important database and systems components ourselves.

### Correctness Before Optimization

Cella should prioritize correctness and well-defined behavior before aggressive optimization.

Performance should eventually be improved through measurement rather than assumptions.

### Understand the System Beneath the Abstraction

Important abstractions should not hide the underlying systems from the person building Cella.

When Cella relies on the operating system, memory subsystem, filesystem, networking stack, or other infrastructure, those relationships should be understood and documented.

### Build for Real Users

Cella should not remain only a demonstration or educational toy.

The project should continuously move toward being usable by real developers for real small projects.

### Document the Reasoning

Documentation should explain not only what was implemented, but also:

- why it was needed;
- what alternatives were considered;
- what experiments were performed;
- what failed;
- what was learned; and
- why the final design was chosen.

---

## 10. Scope

### Initial Scope

The initial goal is a **single-node relational database** running on a local machine.

The early system will focus on understanding and implementing the foundations of a database, including:

```text
Persistent storage
Pages
Records
Tables
Indexes
Query processing
Transactions
Recovery
Concurrency
```

The exact feature set will be established through the development roadmap.

### Future Scope

Once the single-node database is sufficiently mature, Cella may expand into:

```text
Client/server architecture
Networking
Replication
Distributed systems
```

Further future possibilities may include:

```text
Sharding
Consensus
Distributed transactions
Cluster management
```

These are long-term directions, not requirements for the initial Cella release.

---

## 11. Non-Goals

Cella is not initially intended to:

- replace PostgreSQL or other mature databases for large production workloads;
- reproduce every feature available in mature relational databases;
- optimize for massive-scale infrastructure from the beginning;
- introduce distributed-system complexity before the single-node system is understood and reliable;
- prioritize performance at the cost of unnecessary architectural complexity;
- hide important database behavior behind excessive abstractions or dependencies.

The scope may expand in the future, but expansion should happen deliberately.

---

## 12. Platform Direction

Cella should initially focus on a well-defined and practical systems environment rather than attempting to solve cross-platform compatibility immediately.

The initial development direction will prioritize **Linux/POSIX concepts and behavior**, because understanding system calls, filesystems, processes, threads, sockets, and related operating-system facilities is an important part of the project's learning goal.

Development may be performed on Windows using an environment such as WSL2.

Native Windows support can be developed later as a deliberate engineering goal rather than a premature constraint on the initial architecture.

---

## 13. What Success Means

Cella will be considered successful when it becomes a genuinely usable lightweight relational database within its intended scope.

Technical success includes:

- developers can build ordinary small applications using Cella;
- core relational operations work correctly;
- persistent data survives normal process restarts;
- committed transactions provide the durability guarantees Cella promises;
- indexes provide useful performance improvements;
- concurrency and recovery have well-defined behavior;
- the system is tested and benchmarked;
- the database is documented well enough for others to understand and use.

Real-world success is equally important.

A meaningful milestone will be when other developers, especially friends who initially test Cella, actually build projects using it and depend on Cella as their database.

The project should be improved based on their real experiences, problems, and feedback.

---

## 14. Educational Outcome

Cella should eventually become a resource from which another person can learn how to build a database.

A person should be able to follow the project from:

```text
Problem
  ↓
Concept
  ↓
Experiment
  ↓
Design
  ↓
Implementation
  ↓
Testing
  ↓
Benchmarking
  ↓
Lessons learned
```

and understand how the individual components eventually become one working database system.

The repository should therefore preserve the journey rather than only the final implementation.

The long-term documentation may eventually become a complete educational book covering the concepts, experiments, implementation decisions, failures, and lessons learned while building Cella.

---

## 15. Personal Definition of Success

Beyond technical achievements, I want to be able to look back at Cella and know that I genuinely enjoyed building it and learned deeply from the process.

I want to see other people using something I built.

Seeing friends build projects with Cella would be one of the clearest signs that the project has become something real beyond my own computer.

Ultimately, I want to be proud not only of the database itself, but of the engineering journey that created it.

---

## 16. Long-Term Direction

The long-term direction of Cella is intentionally broader than its first release.

The immediate goal is to build a strong and understandable single-node relational database.

Once that foundation is mature, Cella can become a platform for exploring increasingly advanced systems concepts, including networking, replication, distributed coordination, sharding, and other distributed database technologies.

The project should grow only when the underlying concepts are understood and there is a clear reason to introduce additional complexity.

Cella is not defined by a fixed feature list.

It is defined by the goal of building a useful database while continuously deepening our understanding of the systems that make databases possible.
