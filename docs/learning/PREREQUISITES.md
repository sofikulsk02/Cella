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

### 5.2 Memory Hierarchy

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Registers
- CPU cache
- L1/L2/L3 cache
- RAM
- Storage
- Memory latency
- Cache lines
- Locality of reference
- Temporal locality
- Spatial locality

**Why Cella needs it:**
Database performance depends heavily on how data moves between CPU, cache, RAM, and persistent storage.

**Cella connection:**
Buffer pool, page layout, indexes, query execution, and performance optimization.

**Current status:** Not assessed

### 5.3 Cache Behavior

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Cache hits
- Cache misses
- Cache lines
- Sequential access
- Random access
- Cache locality
- False sharing

**Why Cella needs it:**
The physical organization of database data can significantly affect performance even when two algorithms have similar theoretical complexity.

**Cella connection:**
Page layout, indexes, buffer pool, and query execution.

**Current status:** Not assessed

### 5.4 Virtual Memory

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Virtual addresses
- Physical addresses
- Pages
- Page tables
- Address translation
- Memory protection
- Page faults
- Memory-mapped files

**Why Cella needs it:**
Cella runs as a user-space process and relies on the operating system's virtual memory system. Understanding this is important for understanding memory usage and later concepts such as `mmap`.

**Cella connection:**
Memory management, buffer pool, and possible future memory-mapped storage.

**Current status:** Not assessed

### 5.5 I/O and Storage Hardware

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- HDD
- SSD
- NVMe
- Sequential I/O
- Random I/O
- I/O latency
- Throughput
- IOPS
- Storage hierarchy

**Why Cella needs it:**
A database is fundamentally a system that manages data between memory and persistent storage. Understanding storage behavior is essential for making sensible storage-engine decisions.

**Cella connection:**
Persistent storage, page management, WAL, recovery, and benchmarking.

**Current status:** Not assessed

### 5.6 DMA and Device I/O Concepts

**Required depth:** Level 1 — Familiarity

**Topics:**

- Device controllers
- DMA
- CPU involvement in I/O
- Basic device-to-memory data movement

**Why Cella needs it:**
Provides context for understanding how data moves between hardware and memory without requiring detailed hardware implementation knowledge.

**Cella connection:**
Storage and I/O understanding.

**Current status:** Not assessed

### 5.7 Endianness and Data Representation

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Little-endian
- Big-endian
- Byte order
- Integer representation
- Binary representation
- Portable data formats

**Why Cella needs it:**
Cella's persistent file format must have a clearly defined representation for stored values.

**Cella connection:**
Serialization, page format, record format, indexes, and database files.

**Current status:** Not assessed

### 5.8 Atomicity at the Hardware Level

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Atomic operations
- Atomic reads/writes
- CPU atomic instructions
- Memory ordering concepts
- Relationship between hardware atomicity and software synchronization

**Why Cella needs it:**
Later Cella components will involve concurrent access to shared state. Understanding what hardware can guarantee is necessary before reasoning about higher-level synchronization.

**Cella connection:**
Concurrency control, locks, transaction management, and server components.

**Current status:** Not assessed

### 5.9 Memory Ordering

**Required depth:** Level 2 initially, deeper when concurrency is implemented

**Topics:**

- Compiler reordering
- CPU reordering
- Memory visibility
- Acquire/release concepts
- Sequential consistency
- Happens-before relationship

**Why Cella needs it:**
Concurrent database components must reason correctly about when one thread's changes become visible to another thread.

**Cella connection:**
Concurrency, buffer management, transaction processing, and future multi-threaded execution.

**Current status:** Not assessed

### 5.10 Performance Fundamentals

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Latency
- Throughput
- CPU utilization
- Memory bandwidth
- Cache effects
- I/O bottlenecks
- CPU-bound vs I/O-bound workloads
- Basic profiling concepts

**Why Cella needs it:**
Cella's goal includes being lightweight and reasonably fast. Performance claims should eventually be based on measurement rather than assumptions.

**Cella connection:**
Benchmarking, query execution, storage engine, and developer tools.

**Current status:** Not assessed

### Do not need to study

❌ Digital circuit design
❌ Verilog/VHDL
❌ CPU microarchitecture implementation
❌ Designing your own processor
❌ Advanced assembly programming
❌ GPU architecture
❌ Compiler backend implementation

## 6. Operating Systems

### 6.1 Processes

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Process concept
- Process creation
- Process lifecycle
- Process states
- Process termination
- Parent and child processes
- Process isolation
- Process address space

**Why Cella needs it:**
Cella runs as a process and must understand the environment in which its database engine executes. Later, the database server will also need to manage process-related behavior.

**Cella connection:**
Database process, crash behavior, server architecture, and operating-system interaction.

**Current status:** Not assessed

### 6.2 Threads

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Thread concept
- Thread lifecycle
- User threads vs kernel threads
- Shared address space
- Thread-local state
- Context switching
- Thread creation and termination

**Why Cella needs it:**
Cella will eventually perform concurrent work and support multiple simultaneous operations or clients.

**Cella connection:**
Concurrency, query execution, background tasks, buffer management, and server architecture.

**Current status:** Not assessed

### 6.3 System Calls

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- User mode
- Kernel mode
- System calls
- System-call interface
- System-call overhead
- How library functions interact with system calls

**Why Cella needs it:**
Database operations such as reading, writing, synchronizing, creating files, and communicating over sockets ultimately cross the boundary between user space and the operating system.

**Cella connection:**
File I/O, persistence, recovery, networking, and process management.

**Current status:** Not assessed

### 6.4 File Descriptors

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- File descriptors
- Standard input/output/error
- File descriptor tables
- Opening and closing descriptors
- Descriptor lifetime
- Relationship between descriptors and files/sockets

**Why Cella needs it:**
Cella's persistent storage and future networking stack will interact with the operating system through file descriptors.

**Cella connection:**
Storage engine, database files, WAL, sockets, and server implementation.

**Current status:** Not assessed

### 6.5 Virtual Memory

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Virtual address space
- Pages
- Page tables
- Address translation
- Protection
- Page faults
- Copy-on-write
- Memory mapping
- Shared memory
- Memory-mapped files

**Why Cella needs it:**
Cella's in-memory structures exist inside a virtual address space managed by the operating system. Understanding this is necessary for reasoning about memory behavior and future storage techniques such as memory mapping.

**Cella connection:**
Buffer management, memory usage, storage, and possible future `mmap` usage.

**Current status:** Not assessed

### 6.6 Scheduling

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- CPU scheduling
- Time slicing
- Context switching
- Scheduling policies
- Runnable and blocked threads

**Why Cella needs it:**
Concurrent database operations do not execute in isolation. Understanding scheduling helps explain why concurrent code behaves differently from sequential code.

**Cella connection:**
Concurrency, server workloads, transactions, and performance analysis.

**Current status:** Not assessed

### 6.7 Synchronization

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Critical sections
- Mutexes
- Semaphores
- Condition variables
- Read/write locks
- Atomic operations
- Race conditions
- Data races
- Deadlocks
- Starvation

**Why Cella needs it:**
A database cannot safely allow multiple operations to modify shared state without synchronization and clearly defined concurrency rules.

**Cella connection:**
Buffer pool, transaction manager, locking, query execution, and server.

**Current status:** Not assessed

### 6.8 Inter-Process Communication

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- Pipes
- Shared memory
- Signals
- Basic IPC concepts
- Process communication vs thread communication

**Why Cella needs it:**
IPC provides useful background for understanding process boundaries and server architecture, even if the initial Cella implementation does not rely heavily on IPC.

**Cella connection:**
Future server/process architecture and systems understanding.

**Current status:** Not assessed

### 6.9 Signals and Process Failure

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Signals
- Signal handlers
- Process termination
- `SIGINT`
- `SIGTERM`
- `SIGKILL`
- Unexpected process termination
- Core dumps

**Why Cella needs it:**
Cella must eventually be tested under abrupt process termination to understand what happens to in-memory state and persistent data.

**Cella connection:**
Crash testing, recovery, debugging, and shutdown behavior.

**Current status:** Not assessed

### 6.10 File Systems

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Files and directories
- File metadata
- Inodes
- File allocation concepts
- Blocks
- Journaling
- Filesystem caching
- File permissions
- Filesystem consistency

**Why Cella needs it:**
A database stores persistent information using the filesystem or operating-system storage interfaces. Understanding how files are represented and maintained is essential for understanding database persistence.

**Cella connection:**
Database files, WAL, persistence, recovery, and storage design.

**Current status:** Not assessed

### 6.11 Page Cache and Buffered I/O

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- OS page cache
- Buffered I/O
- Direct I/O concepts
- Cache interaction
- Dirty pages
- Writeback
- Relationship between application buffers and OS cache

**Why Cella needs it:**
A database may maintain its own buffer/cache while the operating system also caches filesystem data. Understanding both layers is critical for reasoning about performance and durability.

**Cella connection:**
Buffer pool, storage engine, performance, and durability.

**Current status:** Not assessed

### 6.12 Persistence and Durability

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `write`
- `fsync`
- `fdatasync`
- Flush semantics
- Dirty data
- Persistent vs volatile state
- Crash consistency
- Storage durability

**Why Cella needs it:**
One of Cella's reliability goals is that successfully committed data should remain recoverable after a crash according to Cella's durability guarantees.

**Cella connection:**
Transactions, WAL, commit, crash recovery, and persistent storage.

**Current status:** Not assessed

### 6.13 Crash Consistency

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Partial writes
- Torn updates
- Ordering of writes
- Crash points
- Recovery requirements
- Atomicity of persistent operations
- Filesystem and storage failure behavior

**Why Cella needs it:**
Databases must remain correct despite failures occurring at inconvenient points during updates.

**Cella connection:**
WAL, transactions, recovery, checkpoints, and durability testing.

**Current status:** Not assessed

### 6.14 Kernel and User-Space Boundary

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- User space
- Kernel space
- Privileged operations
- Kernel-managed resources
- System-call boundary
- Why applications cannot directly control hardware

**Why Cella needs it:**
This provides the mental model for understanding how Cella interacts with operating-system-managed resources.

**Cella connection:**
I/O, memory, processes, networking, and storage.

**Current status:** Not assessed

### we do not currently need deep study of:

- CPU scheduling algorithms inside a production kernel
- kernel driver development
- Linux kernel module development
- advanced virtual-machine internals
- kernel networking internals
- filesystem driver implementation

## 7. Filesystems & Storage

### 7.1 Files and Directories

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Files
- Directories
- Paths
- File metadata
- File permissions
- File creation
- File deletion
- File renaming
- File size
- File ownership

**Why Cella needs it:**
Cella's database files must be created, located, managed, and persisted correctly by the operating system.

**Cella connection:**
Database creation, storage files, WAL files, metadata files, and backups.

**Current status:** Not assessed

### 7.2 File Descriptors and File Handles

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- File descriptors
- Open file state
- Descriptor lifetime
- File offsets
- Descriptor duplication
- Files vs file descriptors
- Relationship between descriptors and sockets

**Why Cella needs it:**
Cella's low-level storage layer will communicate with the operating system through file descriptors.

**Cella connection:**
File manager, pager, storage engine, WAL, and later networking.

**Current status:** Not assessed

### 7.3 File Offsets and Random Access

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- File offsets
- Sequential access
- Random access
- `lseek`
- Seeking
- Reading from specific locations
- Writing at specific locations

**Why Cella needs it:**
A database cannot treat its storage file as a simple stream. It needs to locate and update specific pages and structures inside the file.

**Cella connection:**
Page manager, database pages, record storage, indexes, and recovery.

**Current status:** Not assessed

### 7.4 Blocks and Storage Units

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Storage blocks
- Filesystem blocks
- Logical vs physical storage
- Block addressing
- Relationship between blocks and files

**Why Cella needs it:**
Database systems organize data into fixed-size units that eventually interact with lower-level storage units.

**Cella connection:**
Page design, storage layout, buffering, and I/O.

**Current status:** Not assessed

### 7.5 Database Pages

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Fixed-size pages
- Page identifiers
- Page layout
- Page headers
- Free space
- Page boundaries
- Page alignment
- Page serialization
- Page reads/writes

**Why Cella needs it:**
Pages will be one of the fundamental units of Cella's storage engine.

**Cella connection:**
Pager, buffer pool, records, B+ trees, indexes, and persistent storage.

**Current status:** Not assessed

### 7.6 Record Layout

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Fixed-length records
- Variable-length records
- Field offsets
- Null values
- Record headers
- Slot directories
- Slotted pages
- Record serialization

**Why Cella needs it:**
Cella must decide exactly how rows are represented inside database pages.

**Cella connection:**
Tables, tuples, updates, deletes, scans, and storage engine design.

**Current status:** Not assessed

### 7.7 Free Space Management

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Free space
- Free pages
- Free lists
- Allocation
- Reuse of deleted space
- Fragmentation

**Why Cella needs it:**
Cella needs a way to determine where new records can be stored and how deleted or freed space can be reused.

**Cella connection:**
Table storage, page allocation, inserts, and deletes.

**Current status:** Not assessed

### 7.8 Filesystem Caching

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- OS page cache
- Buffered writes
- Read caching
- Dirty pages
- Writeback
- Cache eviction
- Application cache vs OS cache

**Why Cella needs it:**
Cella may maintain its own buffer pool while the operating system also caches file data. Understanding both layers is essential for reasoning about performance and durability.

**Cella connection:**
Buffer pool, storage engine, performance, and persistence.

**Current status:** Not assessed

### 7.9 Persistence and Flush Semantics

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `write`
- `fsync`
- `fdatasync`
- Flush operations
- Dirty data
- Persistence guarantees
- Volatile vs durable state
- Write ordering

**Why Cella needs it:**
Cella must understand when data written by the database is merely in memory or OS caches and when it can be considered durable according to its guarantees.

**Cella connection:**
Transactions, WAL, commit, checkpoints, and recovery.

**Current status:** Not assessed

### 7.10 Crash Consistency

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Partial writes
- Torn writes
- Write ordering
- Crash points
- Atomicity of updates
- Recovery requirements
- Filesystem behavior during crashes

**Why Cella needs it:**
A database must remain logically correct even when the process or machine fails during an update.

**Cella connection:**
WAL, transactions, recovery, checkpoints, and durability testing.

**Current status:** Not assessed

### 7.11 Journaling and Filesystem Journals

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Filesystem journaling
- Metadata journaling
- Ordered writes
- Journal vs database WAL
- What filesystem journaling does and does not guarantee

**Why Cella needs it:**
Cella's WAL and recovery mechanisms operate on top of a filesystem. Understanding filesystem journaling helps distinguish database-level durability from filesystem-level guarantees.

**Cella connection:**
WAL, crash recovery, and durability.

**Current status:** Not assessed

### 7.12 SSDs, HDDs, and Persistent Storage

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- HDD characteristics
- SSD characteristics
- Flash storage
- NVMe
- Random vs sequential I/O
- Latency
- Throughput
- IOPS
- Storage endurance

**Why Cella needs it:**
Storage characteristics influence page layout, buffering, write strategies, indexing, and performance.

**Cella connection:**
Storage engine, buffer pool, WAL, and benchmarking.

**Current status:** Not assessed

### 7.13 Storage Reliability

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Data corruption
- Bad sectors / media errors
- Checksums
- Redundancy concepts
- Backup
- Restore
- Integrity verification

**Why Cella needs it:**
A reliable database must eventually consider not only application crashes but also storage-level corruption and integrity verification.

**Cella connection:**
Database pages, WAL, checksums, recovery, and future backup tooling.

**Current status:** Not assessed

### 7.14 Memory-Mapped Files

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `mmap`
- `munmap`
- Memory-mapped files
- Shared mappings
- Page faults
- Advantages and disadvantages of memory mapping

**Why Cella needs it:**
Memory mapping is an important database/storage technique and provides another way to understand the relationship between files and virtual memory.

**Cella connection:**
Possible future storage strategies and systems experiments.

**Current status:** Not assessed

### 7.15 Storage Layout and Locality

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Sequential layout
- Random layout
- Spatial locality
- Data clustering
- Fragmentation
- Read amplification
- Write amplification
- I/O locality

**Why Cella needs it:**
How data is physically arranged can strongly affect database performance.

**Cella connection:**
Pages, records, indexes, table scans, query execution, and benchmarking.

**Current status:** Not assessed

### 7.16 Checksums and Data Integrity

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Checksums
- Hash-based integrity checks
- Detecting corrupted pages
- Verification during reads
- Error detection vs error correction

**Why Cella needs it:**
Cella may eventually need to detect corrupted database pages or WAL records rather than silently using invalid data.

**Cella connection:**
Persistent storage, WAL, recovery, and diagnostics.

**Current status:** Not assessed

### 7.17 Backup and Restore Concepts

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- Database backups
- Full backups
- Incremental backups
- Restore
- Consistent snapshots
- Backup validation

**Why Cella needs it:**
Once Cella becomes usable by other developers, protecting persistent application data becomes an important operational concern.

**Cella connection:**
Future administration and reliability tooling.

**Current status:** Not assessed

### Do not need to study deeply:

- NAND flash transistor design
- SSD controller firmware
- NVMe controller implementation
- RAID controller hardware design
- filesystem kernel implementation

## 8. Concurrency

### 8.1 Concurrency Fundamentals

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Concurrency vs parallelism
- Processes vs threads
- Shared state
- Critical sections
- Interleavings
- Scheduling effects
- Deterministic vs nondeterministic behavior

**Why Cella needs it:**
Multiple database operations may execute concurrently and interact with the same in-memory and persistent state.

**Cella connection:**
Query execution, buffer pool, transactions, and server architecture.

**Current status:** Not assessed

### 8.2 Race Conditions and Data Races

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Race conditions
- Data races
- Lost updates
- Check-then-act problems
- Read-modify-write
- Timing-dependent bugs

**Why Cella needs it:**
Incorrect concurrent access can corrupt database state or produce incorrect query results.

**Cella connection:**
Buffer pool, transaction management, indexes, and shared metadata.

**Current status:** Not assessed

### 8.3 Mutual Exclusion

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Mutexes
- Critical sections
- Lock ownership
- Lock scope
- Lock granularity
- Contention

**Why Cella needs it:**
Shared database structures need controlled access when multiple operations modify them concurrently.

**Cella connection:**
Buffer pool, page management, transaction manager, and indexes.

**Current status:** Not assessed

### 8.4 Reader-Writer Synchronization

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Reader locks
- Writer locks
- Shared vs exclusive access
- Reader-writer contention
- Lock promotion/demotion concepts

**Why Cella needs it:**
Database workloads often contain many readers and fewer writers. Different access patterns can benefit from different synchronization strategies.

**Cella connection:**
Pages, indexes, table metadata, and future concurrent query execution.

**Current status:** Not assessed

### 8.5 Semaphores and Condition Variables

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Semaphores
- Condition variables
- Waiting and signaling
- Producer-consumer patterns
- Blocking vs spinning

**Why Cella needs it:**
Database components may need to wait for resources such as free buffer frames, locks, I/O completion, or background tasks.

**Cella connection:**
Buffer pool, background workers, transaction manager, and server.

**Current status:** Not assessed

### 8.6 Atomics

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Atomic operations
- Atomic variables
- Compare-and-swap
- Fetch-and-add
- Lock-free concepts
- Atomic counters

**Why Cella needs it:**
Some database metadata and statistics may require efficient concurrent updates without using a full mutex.

**Cella connection:**
Statistics, counters, transaction state, and low-level concurrency.

**Current status:** Not assessed

### 8.7 Memory Ordering

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Memory visibility
- Compiler reordering
- CPU reordering
- Acquire
- Release
- Relaxed ordering
- Sequential consistency
- Happens-before

**Why Cella needs it:**
Correct synchronization requires understanding when updates made by one thread become visible to another.

**Cella connection:**
Concurrent data structures, lock implementations, atomics, and transaction state.

**Current status:** Not assessed

### 8.8 Deadlocks

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Deadlock conditions
- Circular wait
- Lock ordering
- Deadlock prevention
- Deadlock detection
- Deadlock recovery

**Why Cella needs it:**
A database may require multiple locks during operations. Incorrect lock acquisition can cause the entire system to stop making progress.

**Cella connection:**
Transactions, locking, buffer pool, indexes, and concurrent queries.

**Current status:** Not assessed

### 8.9 Starvation and Fairness

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Starvation
- Fairness
- Priority inversion
- Lock fairness
- Scheduling interactions

**Why Cella needs it:**
A system can be technically correct but still unusable if certain operations are continually prevented from making progress.

**Cella connection:**
Locking, transactions, query scheduling, and server behavior.

**Current status:** Not assessed

### 8.10 Locking Concepts for Databases

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Shared locks
- Exclusive locks
- Lock granularity
- Row-level locking
- Page-level locking
- Table-level locking
- Lock compatibility
- Lock acquisition and release

**Why Cella needs it:**
Database concurrency requires stronger semantics than simply protecting individual C++ objects.

**Cella connection:**
Transactions, isolation, concurrent reads/writes, and recovery.

**Current status:** Not assessed

### 8.10 Locking Concepts for Databases

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Shared locks
- Exclusive locks
- Lock granularity
- Row-level locking
- Page-level locking
- Table-level locking
- Lock compatibility
- Lock acquisition and release

**Why Cella needs it:**
Database concurrency requires stronger semantics than simply protecting individual C++ objects.

**Cella connection:**
Transactions, isolation, concurrent reads/writes, and recovery.

**Current status:** Not assessed

### 8.11 Transaction Concurrency

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Concurrent transactions
- Interleaved operations
- Serial execution
- Serializability
- Conflicting operations
- Read/write conflicts
- Lost updates
- Dirty reads
- Non-repeatable reads
- Phantom reads

**Why Cella needs it:**
Cella must eventually define what users can expect when multiple transactions execute at the same time.

**Cella connection:**
Transaction manager, query execution, locking, isolation, and recovery.

**Current status:** Not assessed

### 8.12 Isolation Levels

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Read uncommitted
- Read committed
- Repeatable read
- Serializable
- Isolation anomalies
- Trade-offs between isolation and concurrency

**Why Cella needs it:**
Developers need predictable semantics when multiple transactions operate concurrently.

**Cella connection:**
Transaction system and SQL behavior.

**Current status:** Not assessed

### 8.13 MVCC Concepts

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Multi-version concurrency control
- Versioned records
- Snapshots
- Visibility
- Transaction IDs
- Old-version cleanup
- MVCC vs locking

**Why Cella needs it:**
MVCC is a major approach used by relational databases to allow concurrent readers and writers while maintaining transaction isolation.

**Cella connection:**
Future transaction and concurrency architecture.

**Current status:** Not assessed

### 8.14 Thread Pools and Worker Models

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Worker threads
- Thread pools
- Task queues
- Work distribution
- Background workers

**Why Cella needs it:**
A future Cella server may need worker threads for client requests, background flushing, checkpointing, or maintenance tasks.

**Cella connection:**
Database server and background services.

**Current status:** Not assessed

### 8.15 Concurrent Data Structures

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Thread-safe containers
- Concurrent queues
- Lock-based structures
- Lock-free concepts
- Atomic counters

**Why Cella needs it:**
Some internal database components may be shared by multiple threads and require safe concurrent access.

**Cella connection:**
Buffer management, statistics, task queues, and server components.

**Current status:** Not assessed

### 8.16 Concurrency Testing

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Stress testing
- Repeated concurrent execution
- Race detection
- Thread sanitization
- Deterministic reproduction of concurrency bugs
- Randomized scheduling
- Fault injection

**Why Cella needs it:**
Concurrency bugs can be rare, timing-dependent, and difficult to reproduce. Cella will need deliberate testing rather than relying on ordinary unit tests.

**Cella connection:**
Concurrency subsystem, transaction system, buffer pool, and server.

**Current status:** Not assessed

### 8.17 Synchronization Performance

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Lock contention
- Critical-section size
- Lock granularity
- Throughput vs contention
- Scalability
- Amdahl's law

**Why Cella needs it:**
A concurrency mechanism can be correct but still perform poorly if threads spend too much time waiting on each other.

**Cella connection:**
Transaction processing, buffer pool, query execution, and benchmarking.

**Current status:** Not assessed

### Not initially required:

- Advanced lock-free algorithms
- Advanced wait-free algorithms
- CPU-specific synchronization optimizations
- Kernel scheduler implementation
- Advanced formal verification

## 9. Networking

### 9.1 Networking Fundamentals

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Network basics
- Hosts
- Clients and servers
- IP addresses
- Ports
- Packets
- Network interfaces
- Localhost

**Why Cella needs it:**
Cella may eventually provide a client-server architecture where applications communicate with a Cella server over a network connection.

**Cella connection:**
Cella server and client architecture.

**Current status:** Not assessed

### 9.2 OSI and TCP/IP Models

**Required depth:** Level 1 — Familiarity

**Topics:**

- OSI model
- TCP/IP model
- Application layer
- Transport layer
- Network layer
- Link layer
- Relationship between layers

**Why Cella needs it:**
Provides the conceptual model for understanding where Cella's database protocol sits within the networking stack.

**Cella connection:**
Database client/server communication.

**Current status:** Not assessed

### 9.3 IP and Basic Routing

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- IPv4
- IPv6 concepts
- IP addresses
- Subnets
- Routing basics
- Loopback address
- Local network vs remote network

**Why Cella needs it:**
Cella clients eventually need to connect to database servers running locally or on another machine.

**Cella connection:**
Server configuration and client connections.

**Current status:** Not assessed

### 9.4 TCP

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- TCP connection
- Three-way handshake
- Reliable byte stream
- Ordering
- Retransmission
- Flow control
- Congestion control
- Connection termination
- TCP states

**Why Cella needs it:**
A database server needs a reliable communication channel between clients and the database engine.

**Cella connection:**
Cella client/server protocol.

**Current status:** Not assessed

### 9.5 UDP

**Required depth:** Level 1 — Familiarity

**Topics:**

- Datagram communication
- Connectionless communication
- Differences between TCP and UDP
- Reliability trade-offs

**Why Cella needs it:**
Useful for understanding why TCP is more appropriate for the initial Cella database protocol.

**Cella connection:**
Networking fundamentals and protocol design.

**Current status:** Not assessed

### 9.6 Sockets

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Socket abstraction
- `socket`
- `bind`
- `listen`
- `accept`
- `connect`
- `send`
- `recv`
- `send`
- `recv`
- Socket lifecycle
- Blocking vs non-blocking sockets

**Why Cella needs it:**
Sockets are the operating-system interface that will allow Cella clients and servers to communicate.

**Cella connection:**
Database server and client implementation.

**Current status:** Not assessed

### 9.7 Client-Server Architecture

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Client
- Server
- Requests
- Responses
- Connections
- Connection lifecycle
- Multiple clients
- Server-side processing

**Why Cella needs it:**
Cella eventually needs to operate as an actual database server that external applications can connect to.

**Cella connection:**
Cella server architecture.

**Current status:** Not assessed

### 9.8 Network Protocol Design

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Protocol design
- Messages
- Requests
- Responses
- Message framing
- Headers
- Payloads
- Versioning
- Error messages
- Protocol compatibility

**Why Cella needs it:**
Cella will eventually need a well-defined protocol through which clients can send commands and receive results.

**Cella connection:**
Cella wire protocol and client libraries.

**Current status:** Not assessed

### 9.9 Serialization and Deserialization Over the Network

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Binary serialization
- Text serialization
- Message encoding
- Byte ordering
- Length-prefixed messages
- Framing
- Protocol parsing

**Why Cella needs it:**
Cella must convert database requests and responses into bytes that can safely travel across a network connection.

**Cella connection:**
Client/server protocol.

**Current status:** Not assessed

### 9.10 Blocking and Non-Blocking I/O

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Blocking I/O
- Non-blocking I/O
- I/O waiting
- Readiness
- Blocking sockets
- Basic event-driven concepts

**Why Cella needs it:**
The server must eventually handle clients without unnecessarily blocking the entire system.

**Cella connection:**
Cella server and concurrent client handling.

**Current status:** Not assessed

### 9.11 Multiplexing and Event Loops

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `select`
- `poll`
- `epoll`
- Event loops
- Readiness notifications
- Connection management

**Why Cella needs it:**
As Cella supports multiple clients, it will need a strategy for handling many connections efficiently.

**Cella connection:**
Future server architecture.

**Current status:** Not assessed

### 9.12 Connection Management

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Connection establishment
- Connection termination
- Idle connections
- Connection timeouts
- Connection limits
- Keep-alive
- Error handling

**Why Cella needs it:**
A database server must manage the lifecycle of client connections safely and predictably.

**Cella connection:**
Cella server.

**Current status:** Not assessed

### 9.13 Network Errors and Partial I/O

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Partial reads
- Partial writes
- Connection reset
- Disconnects
- Timeouts
- Interrupted operations
- Retry behavior
- Error propagation

**Why Cella needs it:**
Network operations cannot assume that one send or receive operation transfers an entire logical database message.

**Cella connection:**
Cella protocol and client/server reliability.

**Current status:** Not assessed

### 9.14 Security Fundamentals for Database Networking

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- Authentication
- Authorization
- Encryption
- TLS concepts
- Credential handling
- Trust boundaries
- Network exposure

**Why Cella needs it:**
Once Cella accepts connections from other applications, exposing a database over a network creates security considerations.

**Cella connection:**
Future Cella server and authentication system.

**Current status:** Not assessed

### 9.15 DNS and Service Discovery

**Required depth:** Level 1 — Familiarity

**Topics:**

- DNS basics
- Hostnames
- Name resolution
- Service discovery concepts

**Why Cella needs it:**
Useful for understanding how applications locate network services, although the initial Cella deployment can simply use IP addresses or localhost.

**Cella connection:**
Future server deployment.

**Current status:** Not assessed

### 9.16 Network Performance

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Latency
- Throughput
- Bandwidth
- Round-trip time
- Serialization overhead
- Network bottlenecks

**Why Cella needs it:**
A client-server database introduces network overhead that must eventually be understood when benchmarking Cella.

**Cella connection:**
Server performance and benchmarking.

**Current status:** Not assessed

### 9.17 Database Client Libraries

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Database client APIs
- Connection pools
- Query submission
- Result handling
- Client-side errors
- Prepared statements concepts

**Why Cella needs it:**
A usable database should eventually be accessible from applications through a client library or driver.

**Cella connection:**
Future Cella client libraries.

**Current status:** Not assessed

### Do not need deep knowledge of:

- BGP
- OSPF
- advanced routing protocols
- network hardware design
- packet switching hardware
- wireless protocols
- advanced congestion-control research

## 10. Database Fundamentals

### 10.1 What Is a Database?

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Purpose of a database
- Database vs file storage
- Structured data
- Persistent state
- Queryable data
- Database engine
- Database management system concepts

**Why Cella needs it:**
Cella must be designed around a clear understanding of the problems databases solve instead of simply implementing isolated features.

**Cella connection:**
Overall architecture and project scope.

**Current status:** Not assessed

### 10.2 Relational Model

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Relations
- Tuples
- Attributes
- Domains
- Tables
- Rows
- Columns
- Relational operations
- Keys

**Why Cella needs it:**
Cella is a relational database, so its core data model must be based on the relational model rather than a generic storage abstraction.

**Cella connection:**
Tables, rows, schema, SQL, indexes, and query execution.

**Current status:** Not assessed

### 10.3 Database Schema

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Schema
- Tables
- Columns
- Data types
- Constraints
- Relationships
- Schema metadata
- Schema changes

**Why Cella needs it:**
Cella must know the structure and rules of the data it stores and must preserve this metadata persistently.

**Cella connection:**
Catalog, table creation, query validation, storage, and SQL execution.

**Current status:** Not assessed

### 10.4 Data Types

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Integers
- Floating-point values
- Boolean values
- Strings
- Fixed-width types
- Variable-length values
- Null values
- Type representation
- Type conversion

**Why Cella needs it:**
Cella must define how SQL values are represented both in memory and on disk.

**Cella connection:**
Records, serialization, expressions, SQL execution, and indexes.

**Current status:** Not assessed

### 10.5 Keys

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Candidate keys
- Primary keys
- Composite keys
- Foreign keys
- Natural vs surrogate keys
- Key constraints

**Why Cella needs it:**
Keys are fundamental to relational identity, indexing, and relationships between tables.

**Cella connection:**
Schema, constraints, indexes, and relationships.

**Current status:** Not assessed

### 10.6 Constraints and Data Integrity

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `NOT NULL`
- `UNIQUE`
- `PRIMARY KEY`
- `FOREIGN KEY`
- `CHECK`
- Referential integrity
- Constraint validation
- Constraint enforcement

**Why Cella needs it:**
A relational database must protect the integrity of the data instead of simply storing arbitrary values.

**Cella connection:**
Insert/update/delete operations, schema enforcement, and transactions.

**Current status:** Not assessed

### 10.7 SQL Fundamentals

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `CREATE`
- `ALTER`
- `DROP`
- `INSERT`
- `SELECT`
- `UPDATE`
- `DELETE`
- `WHERE`
- `ORDER BY`
- `GROUP BY`
- `HAVING`
- `LIMIT`
- Expressions
- Predicates

**Why Cella needs it:**
SQL will become the primary interface through which developers interact with Cella.

**Cella connection:**
Parser, query planner, executor, storage engine.

**Current status:** Not assessed

### 10.8 Joins and Relationships

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Inner join
- Left join
- Right join
- Full join concepts
- Cross join
- Join predicates
- Nested-loop joins
- Join execution concepts

**Why Cella needs it:**
Relational applications often store related information across multiple tables and require combining that information in queries.

**Cella connection:**
Query execution and future query optimization.

**Current status:** Not assessed

### 10.9 Aggregation

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `COUNT`
- `SUM`
- `AVG`
- `MIN`
- `MAX`
- Grouping
- Aggregate expressions

**Why Cella needs it:**
Applications frequently need summary queries over stored data.

**Cella connection:**
Query executor and SQL engine.

**Current status:** Not assessed

### 10.10 Query Processing

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Query parsing
- Logical query representation
- Query planning
- Query execution
- Operators
- Expression evaluation
- Tuple processing
- Execution pipelines

**Why Cella needs it:**
Cella must transform a SQL statement into actual operations over stored data.

**Cella connection:**
SQL parser, query planner, executor, indexes, and storage engine.

**Current status:** Not assessed

### 10.11 Query Execution Operators

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Sequential scan
- Index scan
- Filter
- Projection
- Sort
- Join
- Aggregate
- Limit
- Operator composition

**Why Cella needs it:**
The query executor needs a set of well-defined operations that can transform stored tuples into query results.

**Cella connection:**
Execution engine.

**Current status:** Not assessed

### 10.12 Query Planning

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Logical plans
- Physical plans
- Query cost
- Alternative execution strategies
- Sequential scan vs index scan
- Join strategy
- Basic cost estimation
- Plan selection

**Why Cella needs it:**
The same SQL query can be executed in different ways. Cella should eventually choose a reasonable execution strategy.

**Cella connection:**
Query optimizer and execution engine.

**Current status:** Not assessed

### 10.13 Indexes

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Why indexes exist
- Clustered vs non-clustered concepts
- B-tree indexes
- B+ tree indexes
- Hash indexes
- Index lookup
- Index maintenance
- Selectivity
- Covering index concepts

**Why Cella needs it:**
Indexes are fundamental to making relational queries efficient as datasets grow.

**Cella connection:**
B+ tree implementation, query planner, storage engine, and benchmarks.

**Current status:** Not assessed

### 10.14 Transactions

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Transaction
- `BEGIN`
- `COMMIT`
- `ROLLBACK`
- Atomicity
- Consistency
- Isolation
- Durability
- Transaction lifecycle

**Why Cella needs it:**
Transactions provide the reliability guarantees required by normal applications and are central to Cella's definition of correctness.

**Cella connection:**
Transaction manager, WAL, recovery, locking, and MVCC.

**Current status:** Not assessed

### 10.15 ACID

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Atomicity
- Consistency
- Isolation
- Durability
- Practical meaning of each property
- Failure scenarios

**Why Cella needs it:**
Cella's reliability goals depend on understanding what transaction guarantees actually mean.

**Cella connection:**
Transactions, recovery, concurrency, and storage.

**Current status:** Not assessed

### 10.16 Concurrency Control

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Concurrent transactions
- Locking
- MVCC
- Serializability
- Conflict detection
- Isolation anomalies
- Transaction scheduling

**Why Cella needs it:**
Multiple users or threads must be able to work with the database without producing incorrect results or corrupting state.

**Cella connection:**
Transaction manager and concurrency subsystem.

**Current status:** Not assessed

### 10.17 Write-Ahead Logging

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- WAL concept
- Log records
- Log sequence numbers
- Ordering
- Flush requirements
- Redo concepts
- Undo concepts
- Checkpoints
- WAL replay

**Why Cella needs it:**
WAL is one of the main mechanisms used to make database changes recoverable after crashes.

**Cella connection:**
Transactions, persistence, recovery, and durability.

**Current status:** Not assessed

### 10.18 Crash Recovery

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Failure scenarios
- Recovery
- Redo
- Undo concepts
- Checkpoints
- Recovery metadata
- Crash testing
- Recovery correctness

**Why Cella needs it:**
Cella must be able to restore a consistent database state after unexpected failures.

**Cella connection:**
WAL, transaction manager, storage engine, and reliability.

**Current status:** Not assessed

### 10.19 Buffer Pool and Buffer Management

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Buffer pool
- Buffer frames
- Page pinning
- Page unpinning
- Dirty pages
- Eviction
- LRU and replacement policies
- Flush behavior

**Why Cella needs it:**
The database cannot efficiently operate directly on disk for every operation. It needs an in-memory layer for frequently used pages.

**Cella connection:**
Storage engine, query executor, indexes, transactions, and performance.

**Current status:** Not assessed

### 10.20 Storage Engine Concepts

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Heap storage
- Pages
- Records
- Slotted pages
- Free-space management
- Table files
- Index files
- Catalog metadata
- Buffer management

**Why Cella needs it:**
This is the layer responsible for turning relational data structures into persistent storage structures.

**Cella connection:**
Core Cella storage engine.

**Current status:** Not assessed

### 10.21 Database Catalog and Metadata

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- System catalog
- Table metadata
- Column metadata
- Schema metadata
- Index metadata
- Type metadata
- Persistent database metadata

**Why Cella needs it:**
Cella needs to know what tables and indexes exist, what columns they contain, and how stored data should be interpreted.

**Cella connection:**
Schema management, SQL execution, storage engine, and query planning.

**Current status:** Not assessed

### 10.22 Query Optimization Fundamentals

**Required depth:** Level 2 initially, Level 3 later

**Topics:**

- Query cost
- Selectivity
- Cardinality
- Scan cost
- Index selection
- Join ordering
- Basic statistics
- Cost-based optimization concepts

**Why Cella needs it:**
As Cella matures, choosing a good execution strategy will become important for performance.

**Cella connection:**
Query planner and future optimizer.

**Current status:** Not assessed

### 10.23 Prepared Statements and Parameterized Queries

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Prepared statements
- Parameters
- Query plan reuse
- Parameter binding
- SQL injection concept

**Why Cella needs it:**
A practical database used by applications should eventually provide a safe way to execute parameterized queries.

**Cella connection:**
SQL interface and client libraries.

**Current status:** Not assessed

### 10.24 Database Security Fundamentals

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- Authentication
- Authorization
- Privileges
- Roles
- SQL injection
- Credential handling
- Trust boundaries

**Why Cella needs it:**
A database intended for real users needs basic security concepts even if its initial security model is intentionally simpler than mature production databases.

**Cella connection:**
Future client/server architecture and access control.

**Current status:** Not assessed

### 10.25 Database Observability

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Database statistics
- Metrics
- Query timing
- Cache hit rate
- I/O statistics
- Transaction statistics
- Logging
- Diagnostic information

**Why Cella needs it:**
Cella should expose enough information for developers to understand what the database is doing internally and investigate performance or correctness problems.

**Cella connection:**
`cella inspect`, `cella stats`, logging, debugging, and benchmarking.

**Current status:** Not assessed

## 11. Linux / POSIX

### 11.1 Linux Command Line

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Shell basics
- `pwd`
- `ls`
- `cd`
- `mkdir`
- `cp`
- `mv`
- `rm`
- `cat`
- `less`
- `head`
- `tail`
- pipes
- redirection
- environment variables

**Why Cella needs it:**
Cella development and debugging will rely heavily on the command line and Linux tooling.

**Cella connection:**
Development, testing, debugging, experiments, and server operation.

**Current status:** Not assessed

### 11.2 Processes and Process Inspection

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `ps`
- `top`
- `htop`
- process IDs
- parent processes
- process signals
- process termination
- basic process inspection

**Why Cella needs it:**
Cella will run as a process and will eventually need to be investigated under normal and abnormal conditions.

**Cella connection:**
Debugging, crash testing, server operation, and performance analysis.

**Current status:** Not assessed

### 11.3 File and Directory Operations

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Absolute and relative paths
- Permissions
- Ownership
- File creation
- File deletion
- File metadata
- Symbolic links
- Hard links
- `chmod`
- `chown`
- `stat`

**Why Cella needs it:**
Database files, WAL files, logs, and other persistent resources need to be managed correctly by the operating system.

**Cella connection:**
Storage engine, database files, logs, and administration.

**Current status:** Not assessed

### 11.4 POSIX File APIs

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- `open`
- `read`
- `write`
- `close`
- `lseek`
- `fsync`
- `fdatasync`
- `stat`
- `fstat`
- file descriptor behavior
- POSIX error handling

**Why Cella needs it:**
These interfaces provide a direct and understandable boundary between Cella and the operating system's storage facilities.

**Cella connection:**
File manager, pager, persistence, WAL, and recovery.

**Current status:** Not assessed

### 11.5 POSIX Process APIs

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `fork`
- `exec`
- `wait`
- `waitpid`
- process exit
- environment inheritance
- signals

**Why Cella needs it:**
Provides the foundation for understanding process creation and lifecycle, especially for future server and testing tools.

**Cella connection:**
Development tooling, crash testing, server architecture, and process management.

**Current status:** Not assessed

### 11.5 POSIX Process APIs

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `fork`
- `exec`
- `wait`
- `waitpid`
- process exit
- environment inheritance
- signals

**Why Cella needs it:**
Provides the foundation for understanding process creation and lifecycle, especially for future server and testing tools.

**Cella connection:**
Development tooling, crash testing, server architecture, and process management.

**Current status:** Not assessed

### 11.6 POSIX Threading

**Required depth:** Level 2 initially, Level 3 when concurrency is implemented

**Topics:**

- POSIX threads
- thread creation
- thread joining
- mutexes
- condition variables
- read/write locks
- thread attributes

**Why Cella needs it:**
Cella's concurrency model ultimately depends on operating-system threads and synchronization primitives.

**Cella connection:**
Buffer pool, transactions, query execution, and server.

**Current status:** Not assessed

### 11.7 Signals and Interrupt Handling

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `SIGINT`
- `SIGTERM`
- `SIGKILL`
- signal delivery
- signal handlers
- graceful shutdown
- abnormal termination

**Why Cella needs it:**
Cella should eventually distinguish between controlled shutdown and unexpected termination and provide appropriate shutdown behavior.

**Cella connection:**
Server lifecycle, testing, crash experiments, and recovery.

**Current status:** Not assessed

### 11.8 Memory Mapping

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `mmap`
- `munmap`
- memory-mapped files
- shared mappings
- protection flags
- page faults

**Why Cella needs it:**
Memory mapping provides an important connection between virtual memory and persistent files and may be useful in future Cella experiments.

**Cella connection:**
Storage experiments and possible future storage implementations.

**Current status:** Not assessed

### 11.9 System Tracing

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `strace`
- system-call tracing
- process tracing
- observing file I/O
- observing signals
- tracing network calls

**Why Cella needs it:**
Tracing allows you to see what Cella actually asks the operating system to do.

**Cella connection:**
Storage experiments, debugging, performance analysis, and learning.

**Current status:** Not assessed

### 11.10 Binary and File Inspection

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `xxd`
- `hexdump`
- `od`
- file type inspection
- binary file analysis

**Why Cella needs it:**
Cella's database files will eventually need to be inspected at the raw-byte level.

**Cella connection:**
Database file format, pages, records, WAL, and debugging.

**Current status:** Not assessed

### 11.11 Build and Toolchain Environment

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `g++` / `clang++`
- compiler flags
- `make`
- CMake
- linker behavior
- environment variables
- executable permissions

**Why Cella needs it:**
Cella is a systems-level C++ project and needs a predictable build environment.

**Cella connection:**
Entire development workflow.

**Current status:** Not assessed

### 11.12 Networking Tools

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- `ping`
- `ss`
- `netstat` familiarity
- `curl`
- `nc`
- localhost testing
- basic port inspection

**Why Cella needs it:**
These tools will help investigate and validate Cella's future network server.

**Cella connection:**
Client/server development and debugging.

**Current status:** Not assessed

### 11.13 Resource and Performance Inspection

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- CPU utilization
- memory usage
- process resource usage
- open files
- thread counts
- basic system monitoring

**Why Cella needs it:**
Cella should eventually be benchmarked and observed under real workloads.

**Cella connection:**
Performance analysis, benchmarking, and server operation.

**Current status:** Not assessed

### 11.14 POSIX Error Handling

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- return values
- `errno`
- `perror`
- error categories
- interrupted system calls
- retry behavior
- partial operations

**Why Cella needs it:**
Low-level system calls can fail in ways that must be handled explicitly by a database engine.

**Cella connection:**
Storage, networking, concurrency, and recovery.

**Current status:** Not assessed

### 11.15 Shell Scripting

**Required depth:** Level 1–2 — Familiarity to Working Knowledge

**Topics:**

- shell variables
- loops
- conditions
- command substitution
- exit codes
- simple automation scripts

**Why Cella needs it:**
Shell scripts can automate builds, tests, benchmarks, experiments, and database setup.

**Cella connection:**
Development workflow and experiment automation.

**Current status:** Not assessed

### Not initially required:

- Linux kernel administration
- systemd internals
- advanced shell programming
- kernel module development
- advanced package management
- Linux distribution engineering

## 12. Debugging & Performance

### 12.1 Debugging Fundamentals

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Debugging methodology
- Reproducing bugs
- Minimal reproduction
- Breakpoints
- Stepping
- Call stacks
- Stack frames
- Variables and memory inspection
- Watchpoints
- Conditional breakpoints

**Why Cella needs it:**
Cella will contain multiple interacting low-level components. Bugs may appear far away from the original cause, so systematic debugging will be essential.

**Cella connection:**
All implementation stages.

**Current status:** Not assessed

### 12.2 GDB / LLDB

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Starting programs under a debugger
- Breakpoints
- Conditional breakpoints
- Stepping
- Stack traces
- Inspecting variables
- Inspecting memory
- Threads
- Watchpoints
- Debugging crashes

**Why Cella needs it:**
A database engine will eventually involve complex state, pointer-heavy structures, storage metadata, and concurrent execution.

**Cella connection:**
Storage engine, indexing, transactions, concurrency, and server.

**Current status:** Not assessed

### 12.3 Core Dumps and Crash Analysis

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Core dumps
- Segmentation faults
- Crash signals
- Stack traces after crashes
- Post-mortem debugging

**Why Cella needs it:**
Cella must be investigated when it crashes unexpectedly, especially when the crash occurs after the original bug has already corrupted state.

**Cella connection:**
Low-level debugging and crash testing.

**Current status:** Not assessed

### 12.4 Assertions and Invariants

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Assertions
- Preconditions
- Postconditions
- Internal invariants
- Defensive programming
- State validation

**Why Cella needs it:**
Database components have strict structural rules. Assertions can detect invalid internal states close to the point where they occur.

**Cella connection:**
Pages, B+ trees, buffer pool, transactions, query execution, and recovery.

**Current status:** Not assessed

### 12.5 AddressSanitizer

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- AddressSanitizer
- Out-of-bounds access
- Use-after-free
- Double-free
- Stack and heap corruption
- Memory error reports

**Why Cella needs it:**
Cella will manipulate raw memory, pages, buffers, and low-level data structures where memory errors can corrupt persistent state or produce extremely difficult bugs.

**Cella connection:**
Storage engine, buffer pool, page management, and records.

**Current status:** Not assessed

### 12.6 UndefinedBehaviorSanitizer

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Undefined behavior
- Integer overflow
- Invalid shifts
- Misaligned access
- Invalid casts
- Runtime UB detection

**Why Cella needs it:**
Low-level C++ code can silently enter undefined behavior that later causes incorrect database state or crashes.

**Cella connection:**
All low-level components.

**Current status:** Not assessed

### 12.7 ThreadSanitizer

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- ThreadSanitizer
- Data race detection
- Race reports
- Thread synchronization analysis

**Why Cella needs it:**
Concurrent database components may contain race conditions that normal tests fail to reproduce.

**Cella connection:**
Concurrency, transactions, buffer pool, and server.

**Current status:** Not assessed

### 12.8 Logging

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Log levels
- Structured logs
- Debug logs
- Error logs
- Contextual information
- Log rotation concepts
- Logging performance

**Why Cella needs it:**
A database needs useful diagnostic information for understanding failures and observing internal behavior.

**Cella connection:**
All subsystems, especially server, transactions, storage, and recovery.

**Current status:** Not assessed

### 12.9 Tracing and Observability

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Tracing
- Events
- Timings
- Request tracing
- Internal operation visibility
- Trace correlation

**Why Cella needs it:**
Cella's goal includes transparent internals. Developers should eventually be able to understand what happens during database operations.

**Cella connection:**
Developer tools, query execution, transactions, and server operations.

**Current status:** Not assessed

### 12.10 Profiling

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- CPU profiling
- Sampling profilers
- Hot paths
- Call graphs
- CPU-bound workloads
- Profiling methodology

**Why Cella needs it:**
Performance improvements should come from measured bottlenecks rather than assumptions.

**Cella connection:**
Query engine, indexing, storage engine, and benchmarks.

**Current status:** Not assessed

### 12.11 Memory Profiling

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Memory usage
- Heap allocation
- Allocation patterns
- Memory leaks
- Memory fragmentation
- Peak memory usage

**Why Cella needs it:**
Cella should remain lightweight, so memory usage must eventually be measured and understood.

**Cella connection:**
Buffer pool, query execution, indexes, and server.

**Current status:** Not assessed

### 12.12 I/O Profiling

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Disk I/O
- Read/write throughput
- I/O latency
- Random vs sequential I/O
- IOPS
- I/O wait
- System-call frequency

**Why Cella needs it:**
Databases are heavily influenced by storage I/O. Understanding where I/O time is spent is essential for storage-engine design.

**Cella connection:**
Pages, buffer pool, WAL, storage engine, and recovery.

**Current status:** Not assessed

### 12.13 Benchmarking Fundamentals

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Benchmark design
- Warm-up
- Cold vs warm cache
- Repetitions
- Variance
- Latency
- Throughput
- Percentiles
- Workload design
- Benchmark fairness

**Why Cella needs it:**
Cella should eventually make measurable performance claims instead of relying on intuition.

**Cella connection:**
`cella benchmark`, storage, indexing, queries, transactions, and server.

**Current status:** Not assessed

### 12.14 Query Benchmarking

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Query execution time
- Sequential scan benchmarks
- Index lookup benchmarks
- Insert/update/delete workloads
- Join benchmarks
- Aggregation benchmarks
- Dataset scaling

**Why Cella needs it:**
Cella must be tested with realistic workloads to understand how performance changes as data grows.

**Cella connection:**
Query engine, indexes, storage engine, and optimizer.

**Current status:** Not assessed

### 12.15 Storage Benchmarking

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Sequential writes
- Random writes
- Sequential reads
- Random reads
- Page-size effects
- Buffer-pool effects
- WAL overhead
- Flush overhead

**Why Cella needs it:**
Storage decisions should be validated experimentally rather than assumed to be optimal.

**Cella connection:**
Storage engine, page manager, buffer pool, WAL, and recovery.

**Current status:** Not assessed

### 12.16 Scalability Testing

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Dataset scaling
- Concurrent clients
- Thread scaling
- Throughput scaling
- Memory scaling
- Performance bottlenecks
- Saturation points

**Why Cella needs it:**
Cella's behavior should be understood as workloads grow, even if it is not intended to compete with large production databases.

**Cella connection:**
Real-world validation and future releases.

**Current status:** Not assessed

### 12.17 Fault Injection

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Simulated crashes
- Forced process termination
- I/O failure simulation
- Partial operation failures
- Network failures
- Fault injection methodology

**Why Cella needs it:**
Reliability cannot be established only through successful-path testing. Cella must eventually be tested under failures.

**Cella connection:**
Transactions, WAL, recovery, networking, and reliability.

**Current status:** Not assessed

### 12.18 Regression Testing

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Regression tests
- Test suites
- Reproducing historical bugs
- Automated testing
- Continuous integration
- Test coverage concepts

**Why Cella needs it:**
As Cella grows, changes to one subsystem may break another. Previously fixed bugs should remain fixed.

**Cella connection:**
Entire project and GitHub CI.

**Current status:** Not assessed

### 12.19 Performance Regression Testing

**Required depth:** Level 2 — Working Knowledge

**Topics:**

- Baseline benchmarks
- Performance comparisons
- Detecting regressions
- Benchmark automation
- Historical performance tracking

**Why Cella needs it:**
Optimizing one part of Cella should not silently make another workload significantly slower.

**Cella connection:**
Benchmarking and release validation.

**Current status:** Not assessed

### 12.20 Debugging Methodology

**Required depth:** Level 3 — Deep Understanding

**Topics:**

- Hypothesis-driven debugging
- Binary search through changes
- Minimizing reproductions
- Instrumentation
- Reading stack traces
- Examining system state
- Separating symptoms from root causes

**Why Cella needs it:**
Systems bugs are often indirect and difficult to reproduce. A disciplined debugging methodology is as important as knowledge of individual tools.

**Cella connection:**
Entire project.

**Current status:** Not assessed

### Not initially required:

- Kernel-level performance analysis
- Advanced CPU performance counters
- Hardware tracing
- Advanced distributed tracing infrastructure
- Production observability platforms

## 13. Dependency Map

## 14. Prerequisite Completion Criteria
