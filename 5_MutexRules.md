# Mutex Locking Rules in Thread Synchronization 🧵🔒

## Introduction 🌟
Mutexes are used for providing thread synchronization by granting access to critical sections to one thread at a time. This document elaborates on the key rules you should follow when using mutexes for thread synchronization.

## Rules to Follow 📜

### Rule 1: Ownership of Mutex Lock and Unlock 🔐
- **Rule**: If a thread (say T1) locks a mutex (say M), then only that thread (T1) should unlock the mutex (M).
- **Implication**: No other thread can unlock the mutex on behalf of the thread that locked it.

### Rule 2: Don't Unlock an Unlocked Mutex 🛑
- **Rule**: A thread should not attempt to unlock a mutex that is already in an unlocked state.
- **Implication**: Doing so will lead to undefined behavior and indicates faulty code.

### Rule 3: Blocked Threads on Locked Mutex ⛔
- **Rule**: If a mutex is locked by a thread (say T1), other threads (say T2, T3) will be blocked if they try to lock the same mutex.
- **Implication**: This establishes mutual exclusivity among threads for accessing critical sections.

### Rule 4: OS Scheduling Policy for Blocked Threads ⚙️
- **Rule**: If multiple threads are blocked because they tried to lock an already locked mutex, the OS scheduling policy determines which thread gets the lock when the mutex is unlocked.
- **Implication**: The granting of the lock among blocked threads is OS-dependent.

### Rule 5: Self Deadlock Through Double Locking 🔄
- **Rule**: If a thread attempts to lock a mutex it has already locked, it will enter a self-deadlock state.
- **Implication**: Care must be taken to avoid re-locking an already locked mutex by the same thread.

### Rule 6: Unlock Mutexes in LIFO Order 🔄
- **Rule**: Mutexes should be unlocked in the reverse order in which they were locked.
- **Implication**: Helps in avoiding deadlocks and ensures proper flow control.

## Interview Questions and Answers ❓🤔

### Q1: What should you do if you own a mutex lock?
**A1**: If you own a mutex lock, you should be the one to unlock it. No other thread can unlock it for you.

### Q2: What happens if you try to unlock an already unlocked mutex?
**A2**: Trying to unlock an already unlocked mutex leads to undefined behavior and indicates that your program has a bug.

### Q3: What is the role of OS scheduling policy in mutex locking?
**A3**: The OS scheduling policy decides which thread among the blocked threads gets the lock when a mutex is unlocked by its current owner.

### Q4: Can a thread lock a mutex it has already locked?
**A4**: No, if a thread tries to lock a mutex it has already locked, it will enter into a self-deadlock situation.

### Q5: In what order should mutexes be unlocked if you have locked multiple mutexes?
**A5**: Mutexes should be unlocked in the reverse order in which they were locked to avoid potential deadlocks.

---

By keeping these rules in mind, you can effectively implement thread synchronization using mutexes.

📚 Happy Learning! 🌈
