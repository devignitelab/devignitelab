---
title: Python Threads
---

- Each instance of the Python interpreter is a process
  - You can start additional Python processes using the multiprocessing or `concurrent.futures` libraries
  - Python’s subprocess library is designed to launch processes to run external programs, regardless of the languages used to write them.

- The Python interpreter uses a single thread to run the user’s program and the memory garbage collector.
- You can start additional Python `threads` using the threading or `concurrent.futures` libraries.

- Access to object reference counts and other internal interpreter state is controlled by a lock, the Global Interpreter Lock (GIL). 
  - Only one Python thread can hold the GIL at any time. 
  - This means that only one thread can execute Python code at any time, regardless of the number of CPU cores.
  - To prevent a Python thread from holding the GIL indefinitely, Python’s bytecode interpreter pauses the current Python thread every 5ms by default releasing the GIL. The thread can then try to reacquire the GIL, but if there are other threads waiting for it, the OS scheduler may pick one of them to proceed.
  - When we write Python code, we have no control over the GIL. But a built-in function or an extension written in C—or any language that interfaces at the Python/C API level—can release the GIL while running time-consuming tasks.
  - Every Python standard library function that makes a `syscall` releases the GIL. This includes all functions that perform `disk I/O, network I/O, and time.sleep()`
  - Many CPU-intensive functions in the NumPy/SciPy libraries, as well as the compressing/decompressing functions from the zlib and bz2 modules, also release the GIL
  - Extensions that integrate at the Python/C API level can also launch other non-Python threads that are not affected by the GIL. Such GIL-free threads generally cannot change Python objects, but they can read from and write to the memory underlying objects that support the buffer protocol, such as bytearray, array.array, and NumPy arrays.
  - The effect of the GIL on network programming with Python threads is relatively small, because the I/O functions release the GIL, and reading or writing to the network always implies high latency—compared to reading and writing to memory
  - Consequently, each individual thread spends a lot of time waiting anyway, so their execution can be interleaved without major impact on the overall throughput. 
  - Contention over the GIL slows down compute-intensive Python threads. Sequential, single-threaded code is simpler and faster for such tasks.
  - To run CPU-intensive Python code on multiple cores, you must use multiple Python processes.

