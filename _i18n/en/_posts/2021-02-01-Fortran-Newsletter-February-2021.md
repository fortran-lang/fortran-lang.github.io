---
layout: post
title: "Fortran newsletter: February 2021"
category: newsletter
author: Sebastian Ehlert, Milan Curcic, Laurence Kedward, Jérémie Vandenplas, Alexis Perry-Holby
---

Welcome to the February 2021 edition of the monthly Fortran newsletter.
The newsletter comes out at the beginning of every month and details
Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

This month we've had a few updates to the website:

* [#190](https://github.com/fortran-lang/fortran-lang.org/pull/190):
  Add links to fpm contributing guidelines

Ongoing work:

* [#191](https://github.com/fortran-lang/fortran-lang.org/pull/191) (WIP):
  Fix author/maintainer output in fpm registry
* [#187](https://github.com/fortran-lang/fortran-lang.org/pull/187) (WIP):
  Correct compiler page and tutorial regarding Intel oneAPI and PGI to NVIDIA
* [#174](https://github.com/fortran-lang/fortran-lang.org/issues/174) (WIP):
  We are searching for a representative Fortran code snippet for the website and are looking forward to suggestions.

[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.

## Fortran Standard Library

Here's what's new in `stdlib`:

* [#303](https://github.com/fortran-lang/stdlib/pull/303),
  [#301](https://github.com/fortran-lang/stdlib/pull/301),
  [#294](https://github.com/fortran-lang/stdlib/pull/294):
  Fixes and improvements for the manual Makefile build
* [#293](https://github.com/fortran-lang/stdlib/pull/293):
  Write a more verbose introduction to building stdlib
* [#291](https://github.com/fortran-lang/stdlib/pull/291):
  Export package files (CMake and pkg-config)
* [#290](https://github.com/fortran-lang/stdlib/pull/290):
  Rename CMake project from stdlib to fortran\_stdlib
* [#288](https://github.com/fortran-lang/stdlib/pull/288):
  Follow GNU install conventions
* [#284](https://github.com/fortran-lang/stdlib/pull/284):
  Required changes to be able to use `stdlib` as a subproject in CMake
* [CMake example](https://github.com/fortran-lang/stdlib-cmake-example):
  Integration of the Fortran standard library in CMake projects

Work in progress:

* [#304](https://github.com/fortran-lang/stdlib/pull/304) (WIP):
  Add supported compilers MinGW 8, 9, 10
* [#269](https://github.com/fortran-lang/stdlib/pull/269) (WIP):
  Implementation of a module for handling lists of strings
* [#271](https://github.com/fortran-lang/stdlib/pull/271) (WIP),
  [#272](https://github.com/fortran-lang/stdlib/pull/272) (WIP),
  [#273](https://github.com/fortran-lang/stdlib/pull/273) (WIP),
  [#276](https://github.com/fortran-lang/stdlib/pull/276) (WIP),
  [#278](https://github.com/fortran-lang/stdlib/pull/278) (WIP):
  Implementation of the `stdlib_stats_distribution` modules.
  It provides probability distribution and statistical functions.
* [#189](https://github.com/fortran-lang/stdlib/pull/189) (WIP):
  Initial implementation of sparse matrices.

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

* [#342](https://github.com/fortran-lang/fpm/pull/342):
  Fix broken link in contributing guidelines
* [#337](https://github.com/fortran-lang/fpm/pull/337):
  Allow hyphens in fpm project names in "fpm new"
* [#335](https://github.com/fortran-lang/fpm/pull/335):
  Fix: performance regression
* [#334](https://github.com/fortran-lang/fpm/pull/334):
  Remove a name clash in the fpm testsuite

Work in progress:

* [First beta release](https://github.com/fortran-lang/fpm/milestone/1) (WIP):
  First feature-complete release of the Fortran implementation.
* [#230](https://github.com/fortran-lang/fpm/pull/230),
  [#261](https://github.com/fortran-lang/fpm/pull/261) (WIP):
  Specification of the fpm CLI.
* [#316](https://github.com/fortran-lang/fpm/pull/316) (WIP):
  Update subcommand "new" to reflect the addition of support for examples
* [#345](https://github.com/fortran-lang/fpm/pull/345) (WIP):
  Update: fpm\_backend with dynamic openmp scheduling

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

There are a number of pull requests out for evaluation.

A total of 12 pull requests were merged in January.

* [PR#932 Do not assume unempty derived types](https://github.com/flang-compiler/flang/pull/932)
* [PR#957 Support Prefetch Directive](https://github.com/flang-compiler/flang/pull/957)
* [PR#947 Fix gcc-10 compilaton issues](https://github.com/flang-compiler/flang/pull/947)
* [PR#948 Expand CI to run with GCC-9/10 and LLVM-9/10/11](https://github.com/flang-compiler/flang/pull/948)
* [PR#949 USE rename should check if renamed sptr is available in the scope](https://github.com/flang-compiler/flang/pull/949)
* [PR#971 Remove dwarfdump_prolog.f90 test since it is dependent on codegen](https://github.com/flang-compiler/flang/pull/971)
* [PR#940 Flang should generate debug location for limited instructions in prolog](https://github.com/flang-compiler/flang/pull/940)
* [PR#977 Update apt data before installing sphinx](https://github.com/flang-compiler/flang/pull/977)
* [PR#751 Fix for len intrinsic returning int*8 in some cases](https://github.com/flang-compiler/flang/pull/751)
* [PR#956 Minor FileCheck pattern fixes](https://github.com/flang-compiler/flang/pull/956)
* [PR#978 Fix the readme to point to the correct flang-dev list](https://github.com/flang-compiler/flang/pull/978)
* [PR#979 Rename direct header to avoid windows conflict](https://github.com/flang-compiler/flang/pull/979)


### LLVM Flang

Recent development updates:

* OpenMP semantic checks: private, firstprivate, lastprivate, Workshare Construct, `DO` loop restrictions
* Detect call to abstract interface
* OpenMP - add task_reduction clause, make reduction clause part of OmpClause
* New Driver - adding support for various options, testing improvements, standard macro pre-definitions, fixed-form detection, CMake improvements
* OpenACC - semantic checks to enforce declare directive restrictions
* Internal subprogram improvements
* OpenMP/OpenACC - Extend CheckNoBranching to handle branching provided by LabelEnforce
* Disallow `INTENT` attribute on procedure dummy arguments
* Module file improvements and bug fixes
* Add tests for procedure arguments with implicit interfaces

Call notes will be sent to the _flang-dev_ email list and also recorded [here](https://docs.google.com/document/d/10T-S2J3GrahpG4Ooif93NSTz2zBW0MQc_RlwHi0-afY).


## Events

* We had our 8th Fortran Monthly call on January 19.
You can watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/QfiBUAgI3kw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* This year fortran-lang will be applying as a mentor organisation for [Google Summer of Code](https://summerofcode.withgoogle.com/).
We have started working on the application and the project ideas; you can join the ongoing discussion [here](https://fortran-lang.discourse.group/t/google-summer-of-code-2021/658).
If you'd like to help us flesh out the ideas, or have a project idea of your own, please join our upcoming video calls on February 9 and 16 (call info will be posted in the Discourse thread), or write directly in the Discourse thread.
If you're a student, or know students who are [eligible to participate](https://developers.google.com/open-source/gsoc/faq#what_are_the_eligibility_requirements_for_participation), and you'd like to help build the Fortran ecosystem please reach out and let us know.

As usual, subscribe to the [mailing list](https://groups.io/g/fortran-lang) and/or
join the [Discourse](https://fortran-lang.discourse.group) to stay tuned with the future meetings.

## Contributors

We thank everybody who contributed to fortran-lang in the past month by
commenting in any of these repositories:

* [fortran-lang/stdlib](https://github.com/fortran-lang/stdlib)
* [fortran-lang/stdlib-cmake-example](https://github.com/fortran-lang/stdlib-cmake-example)
* [fortran-lang/fpm](https://github.com/fortran-lang/fpm)
* [fortran-lang/fpm-registry](https://github.com/fortran-lang/fpm-registry)
* [fortran-lang/setup-fpm](https://github.com/fortran-lang/setup-fpm)
* [fortran-lang/fortran-lang.org](https://github.com/fortran-lang/fortran-lang.org)
* [fortran-lang/benchmarks](https://github.com/fortran-lang/benchmarks)
* [j3-fortran/fortran\_proposals](https://github.com/j3-fortran/fortran_proposals)

<div id="gh-contributors" data-startdate="January 01 2021" data-enddate="January 31 2021" height="500px"></div>
