## High Level Overview

```
                          Cella
                            │
              ┌─────────────┴─────────────┐
              │                           │
              ▼                           ▼
        Application              Developer Tools
              │                           │
              └─────────────┬─────────────┘
                            │
                ┌───────────┼───────────┐
                │           │           │
                ▼           ▼           ▼
             inspect      stats     benchmark
                            │
                            ▼
                    Database Engine
```

## Cella's Use

```
                    Cella
                 │
     ┌───────────┴───────────┐
     │                       │
Small applications       Learning
Personal projects        Experiments
College projects         DB research
Small services



PostgreSQL / MySQL / etc.
          ↓
Large production systems
Complex workloads
High availability
Large teams
Mature operational requirements



Development machine
        │
        ▼
Windows
        │
        ├──────────────┐
        │              │
        ▼              ▼
   Cella on         Cella on
   Windows          Linux

```
