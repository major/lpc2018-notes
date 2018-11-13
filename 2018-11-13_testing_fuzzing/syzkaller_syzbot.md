# syzkaller/syzbot

* Stable kernels are seeing more backports per month for each release
* 95% of stable backports are fixes
* Every stable release contains > 20,000 bugs (maybe more)
  * It's not getting better over time
  * This comes from the development process -- it will keep getting worse

* syzkaller is a kernel fuzzer
  * grammar-based, coverage-guided
  * repo: https://github.com/google/syzkaller
  * frequently generates a reproducer that can trigger the bug

* syzbot is automation *on top* of syzkaller
  * continuous kernel / syzkaller build with automatic reporting
  * dashboard: http://syskaller.appspot.com

* syzbot has reported 1,400 bugs (~ 960 have been fixed)
  * Manual syzkaller tests found 560 bugs before that
  * This is done with several kernels; some kernels fix faster/more often than others
  * Some kernels have no interest around getting bugs fixed at all

* Manual bug reporting did not scale
  * Discover
  * Assess (actionable?)
  * Report
  * Ping maintainers
  * Support (answer questions)
  * Test fix
  * Fixed bug
  * **This process only works for reporting 1-2 bugs**

* syzbot automates the discovery, reporting
  * It helps with the fix (runs tests again there)

* Not all bugs have reproducers
  * Sometimes there are race conditions or state needs to be accumulated first
  * Interactions between concurrent tests could cause problems

* Future automation
  * bisection
  * testing the committed fix (verify it fixed the bug)
  * retest old bugs on the latest tree
  * fix bisection (find where/when the fix was made)
  * pings
  * auto-closing stale bugs

## Q/A

* What about stats over time?
  * Doesn't exist in syzbot now, but the data is there for someone to do stats

* Feedback: Difficult to sort through all of the emails coming from syzbot
  * Would be good to change the website to sort/filter by maintainer
  * Track syzkaller errors and cross-reference them with bugs
  * Goal is to make something patchwork-like to hold results
