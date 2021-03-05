---
layout: post
title: "Fortran newsletter: December 2020"
category: newsletter
author: Milan Curcic, Jérémie Vandenplas, Laurence Kedward, Gary Klimowicz, Ondřej Čertík
---

Welcome to the December 2020 edition of the monthly Fortran newsletter.
The newsletter comes out at the beginning of every month and details
Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

This month we've had a few updates to the website:

* [#156](https://github.com/fortran-lang/fortran-lang.org/pull/156):
Updates to the mini-book on building Fortran programs, including the addition of
short guides on Meson and CMake.
You can read the mini-book [here](https://fortran-lang.org/learn/building_programs).
* [#169](https://github.com/fortran-lang/fortran-lang.org/pull/169):
Add PSBLAS to the package index.

Ongoing work:

* [#160](https://github.com/fortran-lang/fortran-lang.org/pull/160) (WIP):
In-depth introduction for Fortran with Make.

[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.

## Fortran Standard Library

Here's what's new in `stdlib`:

* [#239](https://github.com/fortran-lang/stdlib/pull/239): Implementation of bitsets in `stdlib_bitsets`.
* [#243](https://github.com/fortran-lang/stdlib/pull/243),
  [#245](https://github.com/fortran-lang/stdlib/pull/245),
  [#252](https://github.com/fortran-lang/stdlib/pull/253),
  [#255](https://github.com/fortran-lang/stdlib/pull/255): Various improvements to `stdlib_logger`.
* [#245](https://github.com/fortran-lang/stdlib/pull/245),
  [#250](https://github.com/fortran-lang/stdlib/pull/250): Minor fixes to the CI.

Work in progress:

* (WIP) [#240](https://github.com/fortran-lang/stdlib/pull/240): Implementation of the `stdlib_stats_distribution` module. It provides probability distribution and statistical functions.
* (WIP) [#189](https://github.com/fortran-lang/stdlib/pull/189): Initial implementation of sparse matrices.

Don't hesitate to test and review these pull requests!

Otherwise, ongoing discussions continue:
* [#220](https://github.com/fortran-lang/stdlib/issues/220): API for file system operations: directory manipulation
* [#241](https://github.com/fortran-lang/stdlib/issues/241): Include a `split` function (202X feature)
* [#254](https://github.com/fortran-lang/stdlib/issues/254): Proposition to add a logger for debug phases and levels among the different logs.

The candidate for file system operations to be included in stdlib is being developed by
[@MarDiehl](https://github.com/MarDiehl) and [@arjenmarkus](https://github.com/arjenmarkus)
in [this repository](https://github.com/MarDiehl/stdlib_os).
Please try it out and let us know how it works, if there are any issues, or if the API can be improved.

## Fortran Package Manager

Here's what's new in `fpm`:

* [#259](https://github.com/fortran-lang/fpm/pull/259): Update the instructions for building from source in README.md.
* [#246](https://github.com/fortran-lang/fpm/pull/246): Automated binary releases in CI.
* [#233](https://github.com/fortran-lang/fpm/pull/233): Allow linking with external libraries.
* [#224](https://github.com/fortran-lang/fpm/pull/224): Add a reference document for the package manifest (fpm.toml).
* [#221](https://github.com/fortran-lang/fpm/pull/221),
  [#239](https://github.com/fortran-lang/fpm/pull/239): Runner options for test and app executables.
* [#220](https://github.com/fortran-lang/fpm/pull/220): Implement compiler and flags settings in Haskell fpm.
* [#209](https://github.com/fortran-lang/fpm/pull/209):
  [#237](https://github.com/fortran-lang/fpm/pull/237): Developer API docs.
* [#216](https://github.com/fortran-lang/fpm/pull/216),
  [#225](https://github.com/fortran-lang/fpm/pull/225),
  [#226](https://github.com/fortran-lang/fpm/pull/226),
  [#229](https://github.com/fortran-lang/fpm/pull/229),
  [#236](https://github.com/fortran-lang/fpm/pull/236),
  [#240](https://github.com/fortran-lang/fpm/pull/240),
  [#247](https://github.com/fortran-lang/fpm/pull/240): Other fixes and improvements.

Work in progress:

* [First beta release](https://github.com/fortran-lang/fpm/milestone/1) (WIP): First feature-complete release of the Fortran implementation.
* (WIP) [#230](https://github.com/fortran-lang/fpm/pull/230),
        [#261](https://github.com/fortran-lang/fpm/pull/261): Specification of the fpm CLI.
* (WIP) [#232](https://github.com/fortran-lang/fpm/pull/232): Allowing the `extra` section in fpm.toml.
* (WIP) [#248](https://github.com/fortran-lang/fpm/pull/248): Refactor backend for incremental rebuilds.
* (WIP) [#251](https://github.com/fortran-lang/fpm/pull/251): Dependency management.
* (WIP) [#255](https://github.com/fortran-lang/fpm/pull/255): Setting the compiler and specifying test or app target.
* (WIP) [#257](https://github.com/fortran-lang/fpm/pull/257): Implement `fpm install`.
* (WIP) [#260](https://github.com/fortran-lang/fpm/pull/260): Fix CI to test release build.

`fpm` is still in early development and we need as much help as we can get.
Here's how you can help today:

* Use it and let us know what you think! Read the [fpm packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md) to learn how to build your package with fpm, and the [manifest reference](https://github.com/fortran-lang/fpm/blob/master/manifest-reference.md) to learn what are all the things that you can specify in the fpm.toml file.
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features.
* Adapt your Fortran package for fpm and submit it to the [Registry](https://github.com/fortran-lang/fpm-registry).
* Improve the documentation.

The short-term goal of fpm is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy
environment in which new open source Fortran projects are created and published with ease.

## Compilers

### Classic Flang

We continue to evaluate and merge pull requests into Classic Flang. Recently merged pull requests into Classic Flang include:
* [PR#883: Flang generated executable does not show result variable of function](https://github.com/flang-compiler/flang/pull/883)
* [PR#933: Updating X-flag entries for internal command line option "-x 49"](https://github.com/flang-compiler/flang/pull/933)
* [PR#939: Publish Arm's internal documentation](https://github.com/flang-compiler/flang/pull/939)
* [PR#941: [DebugInfo] Internal subprogram variable is not accessible for printing in gdb](https://github.com/flang-compiler/flang/pull/941)
* [PR#942: Implement UNROLL(n) directive](https://github.com/flang-compiler/flang/pull/942)
* [PR#943: Enable github Actions for push to master and pull requests to master](https://github.com/flang-compiler/flang/pull/943)
* [PR#945: libpgmath: Stop using pgstdinit.h](https://github.com/flang-compiler/flang/pull/945)
* [PR#946: Call check_member() for PD_is_contiguous](https://github.com/flang-compiler/flang/pull/946)
* [PR#951: Fix for ICE in atomic instruction generation](https://github.com/flang-compiler/flang/pull/951)

Pull requests merged into the supporting projects:
* [classic flang LLVM monorepo PR#5: [Driver] Reduce downstream delta](https://github.com/flang-compiler/classic-flang-llvm-project/pull/5)
* [classic flang LLVM monorepo PR#6: Removing a few CI pipelines](https://github.com/flang-compiler/classic-flang-llvm-project/pull/6)
* [classic flang LLVM monorepo PR#7: Github Actions added to pre-compile artifacts for flang](https://github.com/flang-compiler/classic-flang-llvm-project/pull/7)
* [llvm mirror PR#87: Enable github actions for llvm](https://github.com/flang-compiler/llvm/pull/87)
* [flang-driver PR#94: Enable github actions](https://github.com/flang-compiler/flang-driver/pull/94)

The Classic Flang biweekly call has been set up to discuss issues and plans
for the next pull requests to be validated and merged. Our next calls are Wednesday, December 16 and 30, 8:00 AM Pacific time. The notes from previous calls, upcoming agenda and a link to join the call can be found
[here](https://docs.google.com/document/d/1-OuiKx4d7O6eLEJDBDKSRnSiUO2rgRR-c2Ga4AkrzOI).

### LLVM Flang

Work continues on LLVM Flang, concentrating on semantics, lowering and runtime. Significant contributions are being made for OpenMP and OpenACC support.

In conjunction with the MLIR-based code from the _fir-dev_ fork (the Fortran IR used for lowering), Flang can compile and run most F77 programs, including the Fortran Compiler Validation Suite (FCVS).

Pat McCormick is (still) working on an RFC for the merge of the lowering code
in the fir-dev fork into LLVM master. (This was interrupted by Supercomputing 2020 and other ECP duties.) The goal is to expedite this in a way that is acceptable to the Flang community, so we can do further work in the single master branch.

Recent updates include:
* Johannes Doerfert has created a web page at https://flang.llvm.org; you can find call and Slack logistics there
* Nichols Romero has an llvm-dev RFC for adding Fortran tests to the llvm-tests project: http://lists.llvm.org/pipermail/llvm-dev/2020-November/146873.html
* Andzrej Warzynski has a flang-dev RFC regarding flang option names: http://lists.llvm.org/pipermail/flang-dev/2020-November/000588.html
* Andzrej Warzynski has a cfe-dev RFC regarding refactoring clang to help flang driver become independent of clang: http://lists.llvm.org/pipermail/cfe-dev/2020-November/067263.html
* Changed representation of CHARACTER data in type system to make more consistent with other types (for arrays)
* Changed COMPLEX expression representation to provide better handling in lowering
* More improvements for supporting Fortran 77 programs
* Implemented runtime support for basic ALLOCATE/DEALLOCATE and further work
* Continued implementation of table-driven runtime for derived types; posted documentation
* Continued implementation of array expression lowering
* Improved error checks on forward references
* More updates to flang driver (option handling; -E can now be used to invoke just the Flang preprocessor)
* OpenACC semantic checks for modifiers on enter/exit data, set directives
* OpenACC lowering (enter/exit data, update, init, shutdown, wait directives)
* OpenMP structure checker updates; semantic checks for copyin clause; schedule class


## Events

* Brian Friesen (Lawrence Berkeley National Laboratory) was selected to be the new Chair of PL22.3 (J3, US Standards Committee).
Brian will serve in his first term until November 2023. Congratulations, Brian!
* We had our 6th Fortran Monthly call on November 17.
You can watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/HI-Yhn7Q8Ko" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As usual, subscribe to the [mailing list](https://groups.io/g/fortran-lang) and/or
join the [Discourse](https://fortran-lang.discourse.group) to stay tuned with the future meetings.

## Contributors

We thank everybody who contributed to fortran-lang in the past month by
commenting in any of these repositories:

* [fortran-lang/stdlib](https://github.com/fortran-lang/stdlib)
* [fortran-lang/fpm](https://github.com/fortran-lang/fpm)
* [fortran-lang/fpm-registry](https://github.com/fortran-lang/fpm-registry)
* [fortran-lang/fortran-lang.org](https://github.com/fortran-lang/fortran-lang.org)
* [fortran-lang/benchmarks](https://github.com/fortran-lang/benchmarks)
* [j3-fortran/fortran_proposals](https://github.com/j3-fortran/fortran_proposals)

<div id="gh-contributors" data-startdate="November 01 2020" data-enddate="November 31 2020" height="500px"></div>
