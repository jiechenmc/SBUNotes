---
layout: post
title: Concurrent Programming
tags: java
---

# Processes
	- A process will have a complete set of basic runtime resources. 
	- A thread exists within a process, and every process has at least one thread.
	- Most JVM instance runs as a process
	- Threads share the process's resources

# Concurrency and Parallelism
	Concurrency is about handling asynchronous tasks, sometimes with non-deterministic behavior.
	- async await

	Parallelism is about the asymptotic efficiency of a program with deterministic behavior.
	- It's like running fetch updates as the user loads into the page
	- The deterministic behavior can be broken into subtasks

### Asynchronous Workers Model
	Producers create tasks and the delegator distribute tasks to asynchronous workers. Each worker runs on a different thread.

An **atomic operation** is something that cannot be broken down into smaller sub-operations. It either runs completely, or not at all. The operation is *final* and can not be interrupted.

A **memory inconsistency error** occurs when different threads have inconsistent views of what should be the same data.

A **race condition** is a situation that occurs when a program attempts to perform multiple operations at the same time to produce unexpected behaviors.

A program's **liveness** is defined by its ability to work concurrently.

A **deadlock** is a state in which each member of a group is waiting for another member (including itself) to take action, such as sending a message or releasing a lock.

**Starvation** is a situation where a thread is unable to gain regular access to shared resources and is unable to make progress.

**Livelock** is a special type of starvation caused by over- communication, where the threads are so busy conveying messages to each other that they are not doing their actual job!

A **persistent data structure** is one that preserves its own immediately previous version upon modification.
- if t1 makes change, it will have a reference to the new version while t2 will have reference to the old version

### Assembly Line Model
	After t1 is done work is passed to t2 and so on

### Functional Parallelism
	Implement the program using function calls, where each function is seen as an “agent” who is sending a message to another one (implemented as a function call).
	All parameters passed to a function are copied, so no outside entity can modify the data. This automatically avoids race conditions on shared data.
	- Note that this effectively makes each function an atomic operation.
	- Therefore, a function call can be executed completely independent of another function call, which in turn means that an algorithm implemented functionally can be parallelized on, say, multiple CPUs.
	- Coordinating function calls across CPUs has a performance overhead

# Threads in Java
The major difference is that `wait()` releases the lock or monitor while `sleep()` doesn’t releases the lock or monitor while waiting

> [!info] When a thread is created by another, it inherits the priority of the creator thread.

### Thread States
- NEW
- RUNNABLE
- BLOCKED
- WAITING
- TIMED_WAITING
- TERMINATED

# Synchronization
- It is used to acquire a lock on any object.
- You can then use wait(), notify(), and join().

```java
synchronization(object){
/*expression*/
}
```

**thread confinement** where only one thread can access the thread-unsafe part of the code.
