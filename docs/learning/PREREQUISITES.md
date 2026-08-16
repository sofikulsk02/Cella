# Cella — Learning Prerequisites

## 1. How to Read This Document

## 2. Learning Depth Levels

### Level 1 — FamiliarPity

### Level 2 — Working Knowledge

### Level 3 — Deep Understanding

## 3. C++ & Systems Programming

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Variables and types
- Functions
- References
- Pointers
- `const`
- Structs/classes
- Constructors/destructors
- Namespaces
- Enums
- Basic templates

**Why Cella needs it:**
Used throughout the database engine.

**Cella connection:**
All implementation stages

### 3.2 Memory and Object Lifetime

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Stack vs heap
- Object lifetime
- Ownership
- Dangling pointers
- Memory layout
- Alignment
- RAII
- Smart pointers
- Copy/move semantics

**Why Cella needs it:**
Required for pages, buffers, records, resource ownership, etc.

**Cella connection:**
Storage engine and buffer management.

### 3.3 C++ Standard Library

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `std::vector`
- `std::array`
- `std::string`
- `std::string_view`
- `std::span`
- `std::unordered_map`
- `std::map`
- `std::set`
- `std::deque`
- `std::queue`
- `std::stack`
- `std::priority_queue`

**Why Cella needs it:**
Cella will constantly work with collections of pages, records, keys, metadata, buffers, and internal structures. The standard library provides the basic containers and utilities needed to represent these structures safely and efficiently.

**Cella connection:**
Used throughout the storage engine, indexes, query engine, transaction system, and internal tooling.

### 3.4 Iterators and Algorithms

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Iterators
- Range-based iteration
- `std::sort`
- `std::find`
- `std::binary_search`
- `std::lower_bound`
- `std::upper_bound`
- Basic ranges concepts

**Why Cella needs it:**
Cella will frequently search, sort, and traverse collections of records, keys, page identifiers, index entries, and other internal data.

**Cella connection:**
Storage structures, indexes, query execution, and internal utilities.

### 3.5 Copy and Move Semantics

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- lvalues and rvalues
- copy constructor
- copy assignment
- move constructor
- move assignment
- `std::move`
- when objects are copied
- when objects are moved

**Why Cella needs it:**
Database systems manipulate large amounts of structured data in memory. Understanding copying and moving is necessary to avoid unnecessary work and to reason about ownership and performance.

**Cella connection:**
Pages, records, buffers, query objects, and internal data structures.

### 3.6 RAII and Resource Ownership

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- RAII
- ownership
- resource lifetime
- deterministic cleanup
- smart pointers
- `std::unique_ptr`
- `std::shared_ptr`
- `std::weak_ptr`
- custom resource wrappers

**Why Cella needs it:**
Cella will manage resources such as files, memory, locks, buffers, and eventually sockets. These resources must have clear ownership and predictable lifetimes.

**Cella connection:**
File management, buffer management, concurrency, networking, and transaction resources.

### 3.7 Error Handling and Invariants

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- exceptions
- error codes
- `std::optional`
- `std::expected`
- assertions
- preconditions
- postconditions
- invariants
- failure propagation
- partial failure

**Why Cella needs it:**
A database must deal with failures safely. Operations can fail because of invalid input, I/O errors, corrupted data, concurrency problems, or unexpected process termination.

**Cella connection:**
All major subsystems, especially storage, transactions, recovery, and networking.

### 3.8 C++ File I/O

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `std::fstream`
- `std::ifstream`
- `std::ofstream`
- binary file I/O
- file positioning
- buffering
- interaction between C++ file APIs and lower-level OS APIs

**Why Cella needs it:**
Cella must persist database information to disk and retrieve it correctly after restarting the process.

**Cella connection:**
File manager, page manager, persistent storage, and recovery.

### 3.9 Binary Data and Serialization

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- bits and bytes
- binary representation
- integer representation
- signed and unsigned values
- endianness
- byte offsets
- serialization
- deserialization
- fixed-size and variable-size data
- binary file formats

**Why Cella needs it:**
Cella must represent records, pages, metadata, indexes, and other structures as persistent bytes.

**Cella connection:**
Storage engine, pages, records, indexes, database file format, WAL.

### 3.10 Object Representation and Memory Layout

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `sizeof`
- `alignof`
- alignment
- padding
- object representation
- `memcpy`
- raw memory
- safe byte-level access
- why C++ objects cannot always be written directly to disk

**Why Cella needs it:**
Database storage depends on predictable representations of data. Cella must distinguish between an in-memory C++ object and its persistent on-disk representation.

**Cella connection:**
Page layout, record format, serialization, buffer management.

### 3.11 Templates and Generic Programming

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- function templates
- class templates
- type parameters
- generic programming
- basic template specialization concepts

**Why Cella needs it:**
Generic code may be useful for reusable internal database components and data structures.

**Cella connection:**
Internal utilities and reusable storage/index components.

**Out of scope initially:**
Advanced template metaprogramming, heavy compile-time programming, and complex template techniques unless Cella genuinely requires them.

### 3.12 Compilation and Linking

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- preprocessing
- compilation
- translation units
- header files
- object files
- linking
- static libraries
- dynamic libraries
- debug builds
- release builds
- compiler flags

**Why Cella needs it:**
Cella will grow into a multi-component C++ codebase. Understanding how source code becomes an executable is necessary for debugging and maintaining the project.

**Cella connection:**
Project build system and all implementation stages.

### 3.13 Build Systems

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- CMake
- targets
- libraries
- executables
- include paths
- compiler/linker configuration
- Debug/Release configurations
- dependency management

**Why Cella needs it:**
Cella will eventually contain multiple components, tests, benchmarks, and developer tools that need a reproducible build system.

**Cella connection:**
Entire project structure and development workflow.

### 3.14 Debugging and Memory Analysis

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- debugger basics
- breakpoints
- watchpoints
- stack traces
- stepping
- inspecting memory
- core dumps
- AddressSanitizer
- UndefinedBehaviorSanitizer
- ThreadSanitizer

**Why Cella needs it:**
Low-level database bugs can involve memory corruption, invalid pointers, race conditions, or incorrect state that may only appear much later than the original mistake.

**Cella connection:**
All low-level components, especially storage, buffer management, and concurrency.

### 3.15 C++ Concurrency Fundamentals

**Required depth:** Level 2 initially, Level 3 when Cella reaches concurrency

**Topics:**

- `std::thread`
- `std::mutex`
- `std::lock_guard`
- `std::unique_lock`
- `std::condition_variable`
- atomics
- critical sections
- race conditions
- data races
- deadlocks
- happens-before

**Why Cella needs it:**
Cella will eventually need to support concurrent operations and multiple clients safely.

**Cella connection:**
Buffer pool, transaction manager, locking, query execution, and server.

### 3.16 Low-Level File and POSIX APIs

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- file descriptors
- `open`
- `read`
- `write`
- `close`
- `lseek`
- `fsync`
- `mmap`
- `munmap`
- system calls
- error codes such as `errno`

**Why Cella needs it:**
These APIs form an important boundary between Cella and the operating system. Understanding them is necessary for understanding persistence, I/O, and recovery.

**Cella connection:**
Storage engine, pager, persistence, recovery, and later memory-mapped or advanced I/O features.

### 3.17 C Fundamentals Relevant to Cella

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- structs
- pointers
- pointer arithmetic
- arrays
- C strings
- `malloc`
- `free`
- `memcpy`
- `memset`
- basic POSIX interfaces

**Why Cella needs it:**
Some operating-system and POSIX interfaces are exposed through C APIs. Understanding the C model makes these interfaces easier to reason about and helps expose what C++ abstractions are doing underneath.

**Cella connection:**
Low-level system interfaces and systems programming.

### 3.18 Linux/POSIX Development Environment

**Required depth:** Level 2 initially, deeper as required

**Topics:**

- processes
- threads
- environment variables
- file permissions
- standard input/output/error
- basic shell usage
- process inspection
- `ps`
- `top` / `htop`
- `lsof`
- `strace`
- `hexdump`
- `xxd`
- basic filesystem commands

**Why Cella needs it:**
Cella will initially focus on Linux/POSIX concepts because they provide a clear environment for learning operating-system interfaces, storage, processes, concurrency, and networking.

**Cella connection:**
Development, debugging, storage experiments, performance analysis, and server development.

## 4. Data Structures

### 4.1 Arrays and Dynamic Arrays

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Arrays
- Dynamic arrays
- Contiguous memory
- Resizing
- Indexing
- Time complexity of common operations

**Why Cella needs it:**
Database pages, buffers, records, keys, and internal collections often rely on contiguous memory and efficient indexed access.

**Cella connection:**
Pages, buffer pool, records, internal data structures.

**Current status:** Not assessed

### 4.2 Linked Lists

**Required depth:** Level 1 — Familiarity

**Topics:**

- Singly linked lists
- Doubly linked lists
- Node-based storage
- Pointer-based traversal
- Insertion and deletion

**Why Cella needs it:**
Linked lists are useful for understanding pointer-based structures and may appear in some internal structures, although they are unlikely to be central to Cella's storage engine.

**Cella connection:**
Internal utilities and general systems knowledge.

**Current status:** Not assessed

### 4.3 Stacks and Queues

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Stack
- Queue
- Deque
- LIFO
- FIFO
- Basic implementation and complexity

**Why Cella needs it:**
Stacks and queues appear in parsing, execution, buffering, scheduling, and other internal algorithms.

**Cella connection:**
Query processing, execution, buffering, and internal algorithms.

**Current status:** Not assessed

### 4.4 Hash Tables

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Hash functions
- Buckets
- Collisions
- Chaining
- Open addressing
- Load factor
- Resizing
- Average and worst-case complexity

**Why Cella needs it:**
Hash-based structures can be useful for metadata lookup, caches, internal maps, and potentially hash indexes.

**Cella connection:**
Buffer management, metadata, internal lookup structures, possible future indexes.

**Current status:** Not assessed

### 4.5 Trees

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Tree terminology
- Binary trees
- Binary search trees
- Tree traversal
- Balanced trees
- Search complexity

**Why Cella needs it:**
Trees provide the conceptual foundation for understanding database indexes and B-trees.

**Cella connection:**
Indexing.

**Current status:** Not assessed

### 4.6 Heaps and Priority Queues

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Binary heap
- Min heap
- Max heap
- Heap operations
- Priority queues
- Complexity

**Why Cella needs it:**
Priority queues can be useful in query processing, scheduling, and other algorithms.

**Cella connection:**
Query execution and internal scheduling where applicable.

**Current status:** Not assessed

### 4.7 B-Trees

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Multi-way trees
- Node structure
- Search
- Insertion
- Splitting
- Deletion
- Merging
- Balancing
- Height
- Disk/page-oriented design

**Why Cella needs it:**
B-trees are a fundamental database indexing structure and connect in-memory tree concepts with storage-oriented data structures.

**Cella connection:**
Database indexes and storage engine.

**Current status:** Not assessed

### 4.8 B+ Trees

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- B-tree vs B+ tree
- Internal nodes
- Leaf nodes
- Leaf-level links
- Range scans
- Search
- Insertion
- Splitting
- Deletion
- Page-oriented implementation

**Why Cella needs it:**
Cella will need an efficient indexing structure suitable for persistent storage and range queries.

**Cella connection:**
Primary indexing system.

**Current status:** Not assessed

### 4.9 LRU and Cache Replacement Concepts

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Cache locality
- LRU
- MRU
- Eviction
- Hit rate
- Miss rate
- Basic replacement strategies

**Why Cella needs it:**
Cella will eventually keep frequently used database pages in memory through a buffer pool.

**Cella connection:**
Buffer pool and page cache.

**Current status:** Not assessed

### 4.10 Complexity and Performance Analysis

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Big-O
- Big-Theta
- Big-Omega
- Amortized analysis
- Time complexity
- Space complexity
- I/O complexity
- Trade-offs between memory and storage

**Why Cella needs it:**
Database design decisions are heavily influenced by the cost of CPU operations, memory access, and especially disk/storage I/O.

**Cella connection:**
Storage, indexes, query execution, caching, and benchmarking.

**Current status:** Not assessed

## 5. Computer Architecture

## 5. Computer Architecture

### 5.1 CPU Fundamentals

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- CPU
- Instruction execution
- Registers
- Program counter
- Instruction cycle
- CPU cores
- Threads
- Basic instruction execution

**Why Cella needs it:**
Understanding how Cella's code executes on the CPU helps explain performance, concurrency, and the difference between CPU-bound and I/O-bound operations.

**Cella connection:**
Query execution, serialization, indexing, concurrency, and benchmarking.

**Current status:** Not assessed

## 6. Operating Systems

## 7. Filesystems & Storage

## 8. Concurrency

## 9. Networking

## 10. Database Fundamentals

## 11. Linux / POSIX

## 12. Debugging & Performance

## 13. Dependency Map

## 14. Prerequisite Completion Criteria
