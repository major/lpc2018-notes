# Testing IDA in userspace

2018-11-13, Matthew Wilcox

* IDA == ID Allocator
* Goal: Test kernel ID allocation in userspace
* Yes, testing kernel code from userspace
* Much of the kernel API is in userspace already
* Uses `librcu` to provide RCU support
* Advantages:
  * Quick to iterate new version (get test results in ~ 30 seconds)
  * Built with UBSAN/ASAN
  * Can run under GDB

* Issues
  * `tools/lib` implementations make assumptions and have undeclared dependencies
    * If you want to use something that isn't implemented in `perf` already, it's difficult

  * This testing may only be worthwhile for library code

* Next idea: test page cache in userspace
  * Lots of code to drag down into userspace
  * May have to give up if the payoff isn't worth it

* It's not possible to force a memory allocation failure in the kernel
