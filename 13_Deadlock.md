## Deadlocks in Thread Synchronization: README.md Notes 📝

### Overview 🌐

This note provides an in-depth look at deadlocks in thread synchronization, a situation where all participating threads are blocked indefinitely, unable to make any progress. Once a deadlock occurs, the only way out is to terminate and restart the program.

### Key Terminology 📚

- **Deadlock**: A situation where none of the threads in a process make progress, leading to an infinite blockage. This is a permanent state.

### Causes of Deadlock 💀

1. **Resource Ownership**: A deadlock may occur when multiple threads are competing for the same resources but are unable to access them.
2. **Wrong Synchronization**: Poorly synchronized threads can lead to deadlock situations.

### Deadlock Example Scenario 🛑

- **Resources**: Let's consider two resources, R1 and R2.
- **Threads**: Two threads, T1 and T2, are operating within the same process (P).

#### The Sequence of Events 🎬

1. **Thread T1** locks Resource R2 by invoking `pthread_mutex_lock` on R2's mutex. Resource R2 is now unavailable to other threads.
2. **Thread T2** locks Resource R1 by invoking `pthread_mutex_lock` on R1's mutex. Resource R1 is now unavailable to other threads.
3. **Thread T2** tries to lock Resource R2 but is blocked because T1 has already locked it.
4. **Thread T1** tries to lock Resource R1 but is blocked because T2 has already locked it.

#### The Result 🚫

Both threads are now in a deadlock situation, waiting indefinitely for the other to release their respective resources.

### Key Points to Remember 📌

- Mutex is a property of a resource, not of a thread.
- Resources have their unique mutex, often compared to a key that locks or unlocks the resource (locker).

### Interview Questions About this Topic 🤔💡

1. **What is a deadlock in the context of thread synchronization?**

    *Answer*: A deadlock is a state where all participating threads in a process are blocked and can't make any progress. This is a permanent state that can only be resolved by terminating and restarting the program.

2. **What can cause a deadlock?**

    *Answer*: Deadlocks can occur due to competition for shared resources among multiple threads and improper synchronization mechanisms.

3. **Describe the properties of a resource and a mutex.**

    *Answer*: A mutex is a property of a resource and not of a thread. It acts like a key to a locker (resource). Each resource has its own unique mutex for thread-safe access.

4. **Can you explain the example given in the video about how a deadlock occurred?**

    *Answer*: In the example, two threads T1 and T2 are operating within the same process and are competing for two resources R1 and R2. T1 locks R2, and T2 locks R1. Then T2 tries to lock R2 and is blocked because T1 already owns it, and similarly, T1 tries to lock R1 but is blocked because T2 owns it. Both threads are now in a deadlock state.

5. **Is there a way to resolve a deadlock once it has occurred?**

    *Answer*: Once a deadlock has occurred, it is a permanent state. The only way to resolve it is to terminate and restart the affected program.

6. **What do you mean by "Wrong Synchronization"?**

    *Answer*: Wrong synchronization refers to a poorly implemented thread synchronization mechanism that can lead to adverse conditions like deadlocks.

7. **Is it possible for a thread to require multiple locks at the same time?**

    *Answer*: Yes, it is possible for a thread to require locks on multiple resources simultaneously, as shown in the example. However, this can increase the risk of a deadlock.

8. **What are the dangers of having threads compete for multiple resources?**

    *Answer*: The main danger is the increased risk of deadlocks, where each thread is waiting for the other to release a resource, thus blocking all progress.

9. **How does the video suggest we'll learn about avoiding or dealing with deadlocks?**

    *Answer*: The video hints that the next lecture will discuss the conditions required for a deadlock to occur, suggesting that understanding these conditions could be the first step in avoiding or resolving deadlocks.

10. **Why is deadlock considered a "permanent" state?**

    *Answer*: Deadlock is considered a permanent state because once threads enter a deadlock, they can't make any progress and remain blocked indefinitely. The only solution is to terminate and restart the program.

---
