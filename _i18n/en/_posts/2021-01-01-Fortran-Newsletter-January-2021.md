---
layout: post
title: "Fortran newsletter: January 2021"
category: newsletter
author: Jérémie Vandenplas, Sebastian Ehlert, Laurence Kedward, Milan Curcic, Gary Klimowicz, Ondřej Čertík
---

Happy New Year!
Welcome to the January 2021 edition of the monthly Fortran newsletter.
The newsletter comes out at the beginning of every month and details
Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

This month we've had a few updates to the website:

* [#178](https://github.com/fortran-lang/fortran-lang.org/pull/178),
  [#188](https://github.com/fortran-lang/fortran-lang.org/pull/188):
Fix build preview
* [#179](https://github.com/fortran-lang/fortran-lang.org/pull/179):
Fix word spelling error in quickstart page
* [#173](https://github.com/fortran-lang/fortran-lang.org/pull/173),
  [#180](https://github.com/fortran-lang/fortran-lang.org/pull/180),
  [#186](https://github.com/fortran-lang/fortran-lang.org/pull/186):
Add missing packages from the list of popular Fortran projects to the package index
* [#182](https://github.com/fortran-lang/fortran-lang.org/pull/182):
Update compilers page following Intel oneAPI release
* [#160](https://github.com/fortran-lang/fortran-lang.org/pull/160),
  [#171](https://github.com/fortran-lang/fortran-lang.org/pull/171):
In-depth introduction for Fortran with Make.

Ongoing work:

* [#187](https://github.com/fortran-lang/fortran-lang.org/pull/187) (WIP):
Correct compiler page and tutorial regarding Intel oneAPI and PGI to NVIDIA
* [#174](https://github.com/fortran-lang/fortran-lang.org/issues/174) (WIP):
We are searching for a representative Fortran code snippet for the website and are looking forward to suggestions.
* [#190](https://github.com/fortran-lang/fortran-lang.org/pull/190) (WIP):
Add links to fpm contributing guidelines

[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.

## Fortran Standard Library

Here's what's new in `stdlib`:

* [#256](https://github.com/fortran-lang/stdlib/pull/256): Add the method `log_debug` to `stdlib_logger`
* [#257](https://github.com/fortran-lang/stdlib/pull/257): Improve CMake check for F18 error stop
* [#260](https://github.com/fortran-lang/stdlib/pull/260): Add Intel oneAPI Fortran compiler to CI
* [#261](https://github.com/fortran-lang/stdlib/pull/261): Add a level option to ignore logging messages
* [#263](https://github.com/fortran-lang/stdlib/pull/263), 
  [#267](https://github.com/fortran-lang/stdlib/pull/267): Minor fixes to CI
* [#270](https://github.com/fortran-lang/stdlib/pull/270): Add GFortran 10 to CI
* [#275](https://github.com/fortran-lang/stdlib/pull/275): Add MSYS2 systems to Windows CI
* [#282](https://github.com/fortran-lang/stdlib/pull/282): Add a note about memory issues when compiling stdlib with the support of arrays to up 15 ranks
* [#283](https://github.com/fortran-lang/stdlib/pull/283): Improve the compilation load by splitting submodules


Work in progress:

* [#269](https://github.com/fortran-lang/stdlib/pull/269) (WIP): Implementation of a module for handling lists of strings
* [#271](https://github.com/fortran-lang/stdlib/pull/271) (WIP),
 [#272](https://github.com/fortran-lang/stdlib/pull/272) (WIP),
 [#273](https://github.com/fortran-lang/stdlib/pull/273) (WIP),
 [#276](https://github.com/fortran-lang/stdlib/pull/276) (WIP),
 [#278](https://github.com/fortran-lang/stdlib/pull/278) (WIP): Implementation of the `stdlib_stats_distribution` modules. It provides probability distribution and statistical functions.
* [#284](https://github.com/fortran-lang/stdlib/pull/284) (WIP): Required changes to be able to use `stdlib` as a subproject in CMake
* [#189](https://github.com/fortran-lang/stdlib/pull/189) (WIP): Initial implementation of sparse matrices.

Don't hesitate to test and review these pull requests!

Otherwise, ongoing discussions continue about usability of `stdlib`
([#7](https://github.com/fortran-lang/stdlib/issues/7),
[#215](https://github.com/fortran-lang/stdlib/issues/215),
[#279](https://github.com/fortran-lang/stdlib/issues/279),
[#280](https://github.com/fortran-lang/stdlib/issues/280),
[#285](https://github.com/fortran-lang/stdlib/issues/285)),
and new implementations for `stdlib`
([#135](https://github.com/fortran-lang/stdlib/issues/135),
[#212](https://github.com/fortran-lang/stdlib/issues/212),
[#234](https://github.com/fortran-lang/stdlib/issues/234),
[#241](https://github.com/fortran-lang/stdlib/issues/241),
[#258](https://github.com/fortran-lang/stdlib/issues/258),
[#259](https://github.com/fortran-lang/stdlib/issues/259),
[#262](https://github.com/fortran-lang/stdlib/issues/262),
[#268](https://github.com/fortran-lang/stdlib/issues/268),
[#277](https://github.com/fortran-lang/stdlib/issues/277)).


The candidate for file system operations to be included in stdlib is being developed by
[@MarDiehl](https://github.com/MarDiehl) and [@arjenmarkus](https://github.com/arjenmarkus)
in [this repository](https://github.com/MarDiehl/stdlib_os).
Please try it out and let us know how it works, if there are any issues, or if the API can be improved.

## Fortran Package Manager

Here's what's new in `fpm`:

* [Alpha release version 0.1.3](https://github.com/fortran-lang/fpm/releases/tag/v0.1.3)
* [setup-fpm action](https://github.com/marketplace/actions/setup-fpm):
  GitHub Action to setup the Fortran Package Manager on Ubuntu, MacOS and Windows runners
* [Discussion board](https://github.com/fortran-lang/fpm/discussions):
  For questions & answers, sharing of ideas, showing off projects and, of course, discussions around fpm
* [#248](https://github.com/fortran-lang/fpm/pull/248):
  Refactor backend for incremental rebuilds
* [#266](https://github.com/fortran-lang/fpm/pull/251):
  Dependency management and `fpm update` subcommand
* [#255](https://github.com/fortran-lang/fpm/pull/255)
  Setting the compiler and specifying test or app target
* [#262](https://github.com/fortran-lang/fpm/pull/262):
  Add -fcoarray=single to default gfortran flags
* [#257](https://github.com/fortran-lang/fpm/pull/257):
  Implement `fpm install`
* [#260](https://github.com/fortran-lang/fpm/pull/260):
  Fix CI to test release build
* [#267](https://github.com/fortran-lang/fpm/pull/267):
  Fix enumeration of non-library link objects
* [#268](https://github.com/fortran-lang/fpm/pull/268):
  Fix dependency tracking issue in bootstrap version
* [#271](https://github.com/fortran-lang/fpm/pull/271):
  Fix Windows run and test commands
* [#273](https://github.com/fortran-lang/fpm/pull/273):
  Update developer documentation (manifest + command line)
* [#274](https://github.com/fortran-lang/fpm/pull/274):
  Update README with link to setup-fpm github action.
* [#280](https://github.com/fortran-lang/fpm/pull/280):
  Create specification for example section
* [#281](https://github.com/fortran-lang/fpm/pull/281):
  Cleanup: Remove archived Rust prototype
* [#284](https://github.com/fortran-lang/fpm/pull/284):
  Document model and backend for developers
* [#285](https://github.com/fortran-lang/fpm/pull/285):
  CI: update naming of release binaries
* [#286](https://github.com/fortran-lang/fpm/pull/286):
  Implement check for duplicated program names
* [#289](https://github.com/fortran-lang/fpm/pull/289):
  Add support for same compilers as Fortran version to Haskell version
* [#291](https://github.com/fortran-lang/fpm/pull/291):
  Initial implementation of `fpm build --show-model`
* [#292](https://github.com/fortran-lang/fpm/pull/292):
  Specify the correct help for `fpm run -h`
* [#293](https://github.com/fortran-lang/fpm/pull/293):
  Fix: missing error check after `new_package` call
* [#294](https://github.com/fortran-lang/fpm/pull/294):
  Add: support for detecting .f and .F files
* [#300](https://github.com/fortran-lang/fpm/pull/300):
  Remove -coarray=single option from ifort compiler default options
* [#303](https://github.com/fortran-lang/fpm/pull/303):
  Fixes to source parsing
* [#304](https://github.com/fortran-lang/fpm/pull/304):
  Remove note on not supported dependencies in program targets
* [#307](https://github.com/fortran-lang/fpm/pull/307):
  Fix: program object file collision
* [#315](https://github.com/fortran-lang/fpm/pull/315):
  Remove: -ffast-math in gfortran default release flags
* [#322](https://github.com/fortran-lang/fpm/pull/322):
  Group sources by package in the model

Work in progress:

* [First beta release](https://github.com/fortran-lang/fpm/milestone/1) (WIP):
  First feature-complete release of the Fortran implementation.
* [#230](https://github.com/fortran-lang/fpm/pull/230),
  [#261](https://github.com/fortran-lang/fpm/pull/261) (WIP):
  Specification of the fpm CLI.
* [#316](https://github.com/fortran-lang/fpm/pull/316) (WIP):
  Update subcommand "new" to reflect the addition of support for examples

`fpm` is still in early development and we need as much help as we can get.
Here's how you can help today:

* Use it and let us know what you think! Read the [fpm packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md) to learn how to build your package with fpm, and the [manifest reference](https://github.com/fortran-lang/fpm/blob/master/manifest-reference.md) to learn what are all the things that you can specify in the fpm.toml file.
* Browse existing *fpm* packages on the [fortran-lang website](https://fortran-lang.org/packages/fpm)
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features.
* Adapt your Fortran package for fpm and submit it to the [Registry](https://github.com/fortran-lang/fpm-registry).
* Improve the documentation.

The short-term goal of fpm is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy
environment in which new open source Fortran projects are created and published with ease.

## Compilers

### Classic Flang

There are several pull requests out for evaluation.

Only one pull request was merged in December:

* [PR#951 Fix for ICE in atomic instruction generation](https://github.com/flang-compiler/flang/pull/951)

### LLVM Flang

Alexis-Perry Holby (aperry@lanl.gov) has taken over the Flang biweekly calls.
An invitation was sent to the _flang-dev_ LLVM email list on December 22nd.
Call notes will be sent to the _flang-dev_ email list and also recorded [here]( https://docs.google.com/document/d/10T-S2J3GrahpG4Ooif93NSTz2zBW0MQc_RlwHi0-afY).

Recent development updates:

* Semantic analysis fix for index-names of `FORALL` statements
* Continued work on parser support for `ALLOCATE`
* Build tidying
* OpenMP semantic checks: atomic, flush
* Continued work on new driver
* Fix for list-directed REAL output editing
* Bug fixes: USE of USE of generic, crash in folding (#48437), crash in OpenMP semantic check (#48308), `IMPLICIT_NONE(EXTERNAL)`
* Implement `STORAGE_SIZE()`, `SIZEOF()`, and `C_SIZEOF()`
* OpenACC: update serial construct clauses for 3.1, enforce restriction on routine directive and clauses
* OpenMP: adding important clauses to OmpClause, task reduction clause

## Events

* We had our 7th Fortran Monthly call on December 15.
You can watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/S_xQCSRlefE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As usual, subscribe to the [mailing list](https://groups.io/g/fortran-lang) and/or
join the [Discourse](https://fortran-lang.discourse.group) to stay tuned with the future meetings.

* [Episode 6](https://adspthepodcast.com/2021/01/01/Episode-6.html) of the
Algorithms+Data Structures=Programs (ADSP) Podcast discussed Fortran and
the recent fortran-lang developments.
* [First year of Fortran-lang](https://medium.com/modern-fortran/first-year-of-fortran-lang-d8796bfa0067) by Milan Curcic.

## Contributors

We thank everybody who contributed to fortran-lang in the past month by
commenting in any of these repositories:

* [fortran-lang/stdlib](https://github.com/fortran-lang/stdlib)
* [fortran-lang/fpm](https://github.com/fortran-lang/fpm)
* [fortran-lang/fpm-registry](https://github.com/fortran-lang/fpm-registry)
* [fortran-lang/setup-fpm](https://github.com/fortran-lang/setup-fpm)
* [fortran-lang/fortran-lang.org](https://github.com/fortran-lang/fortran-lang.org)
* [fortran-lang/benchmarks](https://github.com/fortran-lang/benchmarks)
* [j3-fortran/fortran_proposals](https://github.com/j3-fortran/fortran_proposals)

<div id="gh-contributors" data-startdate="December 01 2020" data-enddate="December 31 2020" height="500px"></div>
