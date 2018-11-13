# Android and Linux Kernel

2018-11-13

* Out-of-tree android patching is down to weeks (formerly months)
* SoC lifetime
  * All Android devices start with a two year old kernel -- why?
  * Chip designers use linux-next and emulator to build support
  * Eventually the chip is released and that kernel is used to validate the hardware
  * Manufacturers usually move to the newest LTS kernel at that point
    * Seen to be too risky to move ahead to a newer kernel
  * SoC kernel gets frozen in time -- that's the "device kernel"
* Problems
  * Shipping older kernels with slower updates (or no updates at all)
  * No CI for kernels
    * Nothing available to verify that a certain patch against a kernel will work with Android
  * Can't run/test mainline kernels with Android
    * No devices have a mainline kernel running
    * Latest is likely 1.5 year old kernel running on a device somewhere
  * Managing multiple kernel versions
  * Millions of lines of out-of-tree code
    * Two contributors: Android and SoC manufacturers
  * Requires lots of checks in Android code to see if kernel support is present for certain features (lots of branching)
  * How do you do security/performance validation with hundreds of fixes?
    * LTS changes must be tested regularly for SoC manufacturers to use them
* Versions
  * Oreo: 3.18, 4.4, 4.9
  * Pie: 4.4.107+, 4.9.84+, 4.14.42+
    * About a two year delay
  * Android must continue to work on 3.18, 4.4, 4.9, 4.14, 4.19
    * This is not yet solved
    * Platform deprecation is 5-6 years long
* Adding CI
  * LKFT tests of LTS/rc/android common
    * LKFT == Linux Kernel Function Tests (part of Project Treble)
  * kernelci testing of android common kernels
  * LTP improvements: syscall coverage, fixing breakage
  * Pre-submit testing on Android kernels using Cuttlefish
    * Cuttlefish is like an emulator, but not an emulator
    * You can treat it as an android device -- shows up as if a phone is connected to your x86 laptop
    * Can boot the android common (and mainline) kernels
  * Testing from SoC vendors
* Kernel updates
  * Concerning for carriers/vendors
    * Controlling the frequency of change is important to them
  * Oreo: Minimum kernel version is defined/required
  * Pie: Minimum kernel version with LTS is defined/required
  * Include LTS releases instead of patches
* No testing targets
  * No Android devices run mainline kernels
  * Creates problems for Android + kernel developers
  * Out-of-tree code includes Android common changes and hardware support
* Dealing with out-of-tree code
  * Much has merged upstream
  * In 4.19, only ~ 30 patches are required
  * Lots of out-of-tree changes dropped due to deprecation, userspace alternatives, and upstreamed patches
  * Goal: get out of tree patches to zero
  * Work remaining: Binder priority inheritance, EAS, SDCardFS, and others
* What about out-of-tree hardware specific code?
  * *shrug* ;)
* Project Treble + Kernel
  * Vendor interface (VINTF) is a collection of versioned HAL interfaces
  * Generic System Image (GSI) is the AOSP build that can run on any Android device
    * Vendor code is kept separate
  * Goal is to have GSI + GKI (Generic Kernel Image) withh VINTF and extra kernel modules supplied by the vendor
    * Allows the kernel to move forward more easily
* Getting there
  * Kernel symbol namespaces
  * Single compiler for Android (userspace and kernel)
  * In-kernel ABI monitoring
* Process updates
  * Upstream first
  * Proactively report vulnerabilities and work w/Upstream to fix them
  * Mainline, next, and stable testing on ARM hardware (same with Cuttlefish)

## Q/A

* Where are guides on Cuttlefish?
  * Should appear on https://android.com/ soon
* Android really only has 30 patches that are not upstream?
  * These are the ones that are required to boot the device
  * Doesn't include binder priority / SDCardFS]
  * The exercise was to determine which patches are *REQUIRED* for Android (to boot)
