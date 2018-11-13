# KernelCI Update

* Designed to work with distributed hardware across the planet
* About 10 labs exist right now with centralized reporting at kernelci.org
* Primary focus is build/boot
  * Breaks quite often on the hardware under test

* 280+ unique boards with 37 unique SoCs, 4 million boots
* Focus now is on depth of testing
  * kselftest
  * LTP
  * IGT
  * DRM
  * V4L2

* Standardized on a Debian-based rootfs for all architectures
* Moved to Jenkins pipelines
  * Took a lot of work, but things are more stable now

* Added docs: http://wiki.kernelci.org/
* Automatic bisection on boot failures
  * Currently beta testing emails to a limited audience

* Running test suites is easy -- reporting on them in a valuable/actionable way is difficult
* KernelCI is becoming a project under the LF
* Recruiting founding members now
* Features to work on:
  * Better reporting/visualization
  * Advanced metrics/analytics
  * More architectures, toolchains, and test suites

## Q/A

* What are pass/fail rates right now?
  * Stable/mainline: ~ 90% pass rate
  * linux-next is much more fragile
  * boot tests are often stable on x86, ARM is problematic but improving
  * kernels will often merge/build just fine, but won't boot

* How do you report a breakage?
  * ARM maintainers will watch for breakage

* What are the common problems that you are running into
  * Lots of dependency issues where some support merges for something but not all of it
  * Kernel size is increasing and memory allocation in boot is challenging
    * Sometimes so large that it overwrites kernel device trees
  * The `defconfigs` for ARM were out of date; often wouldn't build/boot

* What about testing patches that are proposed to the list?
  * On the list of to-dos, might takea while to get there

* What about systemd flakiness around kernel hiccups?
  * systemd seems fragile when the kernel replies in a way that it doesn't expect
  * Debian rootfs is quite minimal
  * Current tests verify that certain systemd services are running after boot

* How reliable is the auto bisection?
  * Lots of bisection fails because it takes forever and doesn't finish
  * Sometimes there's a failure on ARM but the bisection finds an x86_64 patch
  * Usually it's more often a hardware problem in the lab
    * Networking hiccup or hardware goes offline

* How reliable is the lab infrastructure?
  * Everything is dependent on a lab setup
  * Really depends on whether someone is available to maintain the lab
  * KernelCI can report a lab failure vs. kernel failure
  * Some hardware is early release and has flaky components

* How can a company add a new lab to KernelCI?
  * Go see the documentation, send an email to the ML, join the IRC channel
  * `#kernelci` on IRC

* Limits on bisection?
  * Using the same gcc/glibc/toolchain each time
  * Newer toolchains will likely cause more problems than older ones
  * Certain kernel versions require updates for binutils -- can't bisect backwards past those points
  * Usually the bisection range is narrow (worked yesterday, not today)

* Do you have virt testing?
  * Real hardware testing is more expensive
  * Some labs do this but it doesn't do enough to test the hardware
  * Tests some things, but not a lot of other things

* Do people ever go back and fix defconfigs to include new drivers?
  * Mostly driven by people who find problems
  * "Driver showed up, but I don't need it"
