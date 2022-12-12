# A simple C thread pool implementation

**UPDATE: I have replaced the original pthread with [tinycthread](https://github.com/tinycthread/tinycthread), so it's working on both Windows and POSIX systems.**

Currently, the implementation:
 * ~~Works with pthreads only, but API is intentionally opaque to allow other implementations (Windows for instance).~~
 * [New] Based on [tinycthread](https://github.com/tinycthread/tinycthread), provided Windows/Linux/macOS supports.
 * Starts all threads on creation of the thread pool.
 * Reserves one task for signaling the queue is full.
 * Stops and joins all worker threads on destroy.

## How to Use

You can use the source code in your project directly. 

But it becomes more easily to use conan. 

1. Install conan first according to this [reference](https://docs.conan.io/en/latest/installation.html).
2. add it to your conan.txt:

   ```
   [requires]
   ...
   tinycthreadpool/1.0

   ```

3. At last, install or build the lib with conan automatically.

   ```
   conan install <path to conan.txt> --build=missing
   ```

Enjoy!


Possible enhancements
=====================

The API contains addtional unused 'flags' parameters that would allow
some additional options:

 * Lazy creation of threads (easy)
 * Reduce number of threads automatically (hard)
 * Unlimited queue size (medium)
 * Kill worker threads on destroy (hard, dangerous)
 * ~~Support Windows API (medium)~~
 * Reduce locking contention (medium/hard)
