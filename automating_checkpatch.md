# Automating checkpatch/sparce/smatch/checkdoc

2018-11-13, Knut Omang

* Why: Run static checking tools as part of automated testing
  * Reduce the review back-and-forth noise
  * Avoid regressions

* Problems
  * Lots of false negatives and differing policies
  * Considered integrating with `make C={1,2}` but it isn't general enough
  * Lots of different tools exists with different output formats
    * Could these be unified?

* Config / Suppressions
  * Each module directory can have a `runchecks.cfg` file that excludes certain checks

## Q/A

* Why not add it to the kernel config itself to add checking?
  * Might be too heavy
  * Could use config fragments to bring in tests
