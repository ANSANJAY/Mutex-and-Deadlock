## Mutual Exclusion in Threads: README.md Notes 📝

### Overview 🌐

The video focuses on implementing mutual exclusion between two threads that act on a shared data structure, in this case, an array. The use of mutex (Mutual Exclusion) ensures that only one thread can act on the array at a given time, ensuring data integrity.

### Objectives 🎯

- Deploy mutual exclusion between two threads
- Use mutex variables to protect a shared data structure (an array in this example)

### Initialization 🏁

1. **Global Mutex**: Declare a global mutex variable to protect the shared data structure (the array).
2. **Initialization**: Initialize the mutex in the main function when the application starts.

  ```cpp
  // Initialize mutex
  pthread_mutex_init(&mutex, NULL);
  ```

### Mutex in Action 🛠

#### Thread Callback: Swap 🔄

1. **Purpose**: Swaps the first and last elements in the array.
2. **Logic**: The swapping logic is "sandwiched" between `pthread_mutex_lock` and `pthread_mutex_unlock`.

  ```cpp
  pthread_mutex_lock(&mutex);
  // Swap logic
  pthread_mutex_unlock(&mutex);
  ```

#### Thread Callback: Sum ➕

1. **Purpose**: Computes the sum of all elements in the array.
2. **Logic**: The sum computation logic is also "sandwiched" between `pthread_mutex_lock` and `pthread_mutex_unlock`.

  ```cpp
  pthread_mutex_lock(&mutex);
  // Sum logic
  pthread_mutex_unlock(&mutex);
  ```

### Locking Mechanism 🔒

- When a thread locks the mutex, no other thread can perform operations on the array until the mutex is unlocked.
- If another thread attempts to lock an already locked mutex, it will block until the mutex is released.

### Outcome ✅

- Mutexes ensure that the program produces the correct output, with thread-safe access to shared resources.
- Guaranteed mutual exclusion, resulting in consistent and expected results.

### Advanced Topics 🚀

- The video hints at discussing more advanced usages of mutexes in future sections.

---

### Interview Questions About this Topic 🤔💡

1. **What is the primary objective of using a mutex in multi-threaded applications?**

   *Answer*: The primary objective is to ensure mutual exclusion so that only one thread can act on a shared resource at a given time. This prevents data corruption and ensures data integrity.

2. **How do you initialize a mutex?**

   *Answer*: A mutex is typically initialized in the main function when the application starts. In C++, this is commonly done using `pthread_mutex_init`.

3. **Explain the term "sandwiching" in the context of using mutex.**

   *Answer*: Sandwiching refers to placing the critical code section between `pthread_mutex_lock` and `pthread_mutex_unlock`. This ensures that the critical section is accessed by only one thread at a time.

4. **What happens when a thread attempts to lock an already locked mutex?**

   *Answer*: If a thread tries to lock an already locked mutex, it will be blocked until the mutex is unlocked by the thread that currently owns it.

5. **What kind of problems can mutexes solve in a multi-threaded program?**

   *Answer*: Mutexes can solve problems related to data integrity and consistency by ensuring that only one thread at a time can modify a shared resource. This is particularly useful for preventing race conditions.

6. **Are there any advanced use-cases for mutexes that the video hints at?**

   *Answer*: The video suggests that advanced uses of mutexes will be covered in future sections, although it doesn't specify what those advanced use-cases are.

7. **Why is the output always 15 in the example provided in the video?**

   *Answer*: The output is always 15 because mutual exclusion is ensured. The reader thread computes the sum only after the writer thread has completed its operations on the array, leading to consistent and expected results.

8. **What is the role of the `Swap` and `Sum` thread callback functions?**

   *Answer*: The `Swap` function swaps the first and last elements of the array, while the `Sum` function computes the sum of the elements in the array. Both functions use mutexes to ensure thread safety and data integrity.

9. **What happens if the mutex is not used in this scenario?**

   *Answer*: Without a mutex, both threads could potentially access and modify the shared resource (the array) at the same time. This could lead to data corruption, unexpected results, and race conditions.

10. **How can mutexes impact the performance of a multi-threaded program?**

    *Answer*: While mutexes provide safety, they can also introduce performance overhead due to the locking mechanism, especially in scenarios where lock contention is high.

---
