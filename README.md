# uberEmu4j

uberEmu4j is a complete Java port of the Uber Emulator originally written in C#.  
The project reimplements the original emulator in Java while preserving functional parity and introducing architectural improvements aligned with modern Java server development practices.

Original C# implementation:  
https://github.com/Quackster/uberEmu

**This release requires Java 24 runtime**

---

## Overview

The purpose of uberEmu4j is to provide a faithful, maintainable, and extensible Java implementation of the Uber Emulator.  
All core systems from the original C# codebase have been translated to Java, with additional refactoring to improve modularity, performance, and long-term maintainability.

This project should be considered a full port rather than a partial rewrite or re-implementation.

---

## Key Architectural Differences

While maintaining behavioral compatibility with the original emulator, several significant architectural changes were introduced.

### Packet Event System

uberEmu4j implements a centralized event-driven packet handling system.

- Every inbound and outbound packet is dispatched through an event layer
- Packet handlers are decoupled from network transport
- Supports interception, cancellation, and extension of packet logic
- Enables cleaner integration of future features and plugins

This replaces the more tightly coupled packet handling approach used in the original C# implementation.

---

### Repository-Based Database Access

All SQL access in uberEmu4j is consolidated under the `/repository/` package.

- Database queries are isolated from business logic
- Each repository encapsulates a specific domain concern
- Improves readability, testability, and refactoring safety
- Eliminates inline SQL usage throughout the codebase

This structure replaces the scattered SQL access patterns present in the original project.

---

### Networking and Logging Stack

uberEmu4j adopts standard Java infrastructure libraries:

- **Netty** is used for asynchronous, non-blocking network I/O
- **Log4j** is used for logging
