# Mutex Locking Types: Code Locking vs Object Locking 🧵🔒

## Introduction 🌟
Mutex locking can be broadly categorized into two types: **Code Locking** and **Object Locking**. This document explains these two types with examples, highlighting their use-cases and functionalities.

## Types of Mutex Locking 🔒

### Code Locking 📜

#### What is it? 🤔
- **Definition**: Code Locking is used to protect a section of code against concurrent, thread-unsafe access.
  
#### Example & Explanation 🌈
- Imagine you have a C file, say `file.c`, which contains a global mutex object whose scope is within the file.
- The mutex object is used to protect all the critical sections in the file. 
- For instance, if there is a function `foo()` in `file.c` containing a critical section, that section would be sandwiched between `pthread_mutex_lock()` and `pthread_mutex_unlock()` calls.
  
#### Characteristics 📌
- The mutex is usually defined at the source file level.
- Critical sections are easily identifiable by programmers just by looking at the code.
- Since the mutex is global within the file, it can protect multiple critical sections in the file.

### Object Locking 🖇️

#### What is it? 🤔
- **Definition**: Object Locking is used to protect an object against concurrent, thread-unsafe access.

#### Difference from Code Locking 🔄
- Unlike code locking, which protects a code section, object locking protects an object (like a data structure).
  
## Interview Questions and Answers ❓🤔

### Q1: What is Code Locking and when would you use it?
**A1**: Code Locking is a mutex locking type used to protect a segment of code from being accessed in a thread-unsafe manner. You would use it when you want to ensure that a particular section of your code is accessed by only one thread at a time.

### Q2: Can you explain the concept of Object Locking?
**A2**: Object Locking involves using a mutex to protect an object or a data structure from concurrent, thread-unsafe access. This ensures that only one thread can read/write to the object at a given time.

### Q3: What are the differences between Code Locking and Object Locking?
**A3**: Code Locking is used to protect a section of code, while Object Locking is used to protect an object or data structure. In Code Locking, the mutex is usually global within the source file and can protect multiple critical sections in the file. Object Locking typically associates a mutex with a specific object to ensure its safe access.

### Q4: How is a mutex generally used in the context of Code Locking?
**A4**: In Code Locking, a global mutex within the file is used to protect all the critical sections within that file. The critical section is usually sandwiched between `pthread_mutex_lock()` and `pthread_mutex_unlock()` calls to ensure mutual exclusion.

### Q5: Can you provide an example scenario where Code Locking is essential?
**A5**: Imagine a scenario where a global buffer is accessed by multiple threads for read and write operations. To prevent thread-unsafe access, you could use Code Locking. You would sandwich the code section that accesses the global buffer between `pthread_mutex_lock()` and `pthread_mutex_unlock()` calls.

---

By understanding these types of mutex locking, you can better choose the appropriate method for thread synchronization in your programs.

📚 Happy Learning! 🌈
