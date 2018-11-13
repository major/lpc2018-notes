# Automated Testing Summit at the Embedded Linux Conf in 2018

2018-11-13

* Problems found:
  * Lots of testing activity, not enough collaboration
  * No common place to share resources/development/ideas
  * Growing number of test suites, but they're used differently
  * No common test definition format (everyone living in their own world)
  * No common parseable result output format
  * Running tests is easy, doing something useful with results is hard

* Why is there so little sharing?
  * Companies think that their test frameworks are secret sauce
  * Most people are doing the same things already
  * Tests are dependent on lab/test/hardware frameworks
  * Some companies are afraid to share their tests
    * Might show how little testing they're actually doing
  * Need to define common terminology
    * Embedded vs server terms are different
    * Example: DUT for embedded systems (device under test) is not well known

* Where is the best place to start collaborating?
  * How do we define a test definition so that it can be run everywhere
    * Where to get the source? How to build them?
    * What is a pass or failure result?
    * No common way to define that right now
  * Output/interchange formats
    * All the tests send out results in different ways
    * Text, XML, JSON, human readable -- not easily parseable
    * Makes it difficult to put results in the same place to share them

* Action items:
  * Refine terminology/glossary
  * Collaborate on test definitions
  * pdudaemon (collect tools for automating various PDUs)
  * Full list: https://elinux.org/Automated_Testing_Summit
  * Next meeting at ELC-E in Lyon, France (Oct 2019)

## Q/A

* What's the problem with the frameworks / test suites?
  * Lots of tests from LTP are known to fail on embedded architectures
  * People make "skip lists" but nobody knows why certain tests were skipped
  * We need to know why they were skipped
  * Is there a hardware specific reason why the test won't run on that hardware?

* Should we standardized on one suite? Should we focus on interoperability?
  * Survey is in progress to determine the the plan
  * Answer not known right now

* How many desktop/server folks at ATS?
  * It was heavily skewed towards embedded
  * zeroday/syzcaller maintainers were present
  * LTP maintainer was present

* What about comparative testing?
  * Did performance go up or down? What about other metrics?
  * Part of the criteria for pass/fail
  * Becomes part of the test case definition

* What about variance from lab to lab?
  * Different storage/machines in each lab
  * Could skew performance results
  *

## Links

* eLinux Wiki: https://elinux.org/Automated_Testing_Summit
  * Detailed survey responses are on this page
