---
layout: post
title: "Fortran newsletter: September 2020"
category: newsletter
author: Milan Curcic, Ondřej Čertík, Gary Klimowicz, Brad Richardson, Jérémie Vandenplas, Thomas König, and Laurence Kedward
---

Welcome to the September 2020 edition of the monthly Fortran newsletter.
The newsletter comes out on the first calendar day of every month
and details Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

We continued the work on the Fortran-lang website, specifically:

* [#133](https://github.com/fortran-lang/fortran-lang.org/pull/133):
Listing fpm packages on the Packages page of the website
  
Ongoing work:

* [#117](https://github.com/fortran-lang/fortran-lang.org/issues/117): Adding a
  Benchmarks section, a new dedicated repository was created at
  https://github.com/fortran-lang/benchmarks and many details have been
  discussed in [issues](https://github.com/fortran-lang/benchmarks/issues) there

[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.

## Fortran Standard Library

There hasn't been new stdlib development in August, however ongoing work and discussions continue:

* [#227](https://github.com/fortran-lang/stdlib/issues/227): API proposal for logging facilities in stdlib
* [#225](https://github.com/fortran-lang/stdlib/issues/225): Name convention for derived types in stdlib
* [#224](https://github.com/fortran-lang/stdlib/issues/224): Handling and propagating errors inside stdlib
* [#221](https://github.com/fortran-lang/stdlib/issues/221): API for a bitset data type
* [#201](https://github.com/fortran-lang/stdlib/issues/201): API for file system operations

The candidate for file system operations to be included in stdlib is being developed by
[@MarDiehl](https://github.com/MarDiehl) and [@arjenmarkus](https://github.com/arjenmarkus)
in [this repository](https://github.com/MarDiehl/stdlib_os).
Please try it out and let us know how it works, if there are any issues, or if the API can be improved.

## Fortran Package Manager

Ongoing work in fpm:

* [#146](https://github.com/fortran-lang/fpm/issues/146) (WIP): 
Implementing internal dependencies and build backend in the Fortran fpm

fpm is still in early development and we need as much help as we can get.
Here's how you can help today:

* Try to use it. Does it work? No? Let us know! Read the [fpm packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md) to learn how to build your package with fpm.
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features.
* Adapt your Fortran package for fpm and submit it to the [Registry](https://github.com/fortran-lang/fpm-registry).
* Improve the documentation.

The short term goal of fpm is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy
environment in which new open source Fortran projects are created and published with ease.

##  Fortran benchmarks

We created the [benchmarks repository](https://github.com/fortran-lang/benchmarks) with the goal to design and implement a comprehensive set of benchmarks.
The benchmarks will aim to compare the performance of various Fortran compilers, as well as the performance of canonical algorithms implemented in Fortran and different languages.
If you'd like to contribute in any way, be it the design, implementation, or testing of benchmarks, please join the ongoing discussion [here](https://github.com/fortran-lang/benchmarks/issues).

## Compilers

### GFortran

GFortran 10.2 has been released, a bugfix release for 10.1.
Bugs fixed include PR94361, a memory leak with finalizers.

The development version of `gfortran` now supports the
full OpenMP 4.5 specification.  This will be released
with GCC 11, but of course people can already download
and test it.

### Classic Flang

We're evaluating pull requests and merging them into the original Flang
compiler again. We pulled in 4 changes in the past couple of weeks, and expect
to merge in a few more each week. One upcoming change is the support for LLVM 10,
which requires the use of a new fork, the _classic-flang-llvm-project_
fork of the LLVM monorepo. See
[PR#1](https://github.com/flang-compiler/classic-flang-llvm-project/pull/1)
for details.

The Classic Flang biweekly call has been set up to discuss issues and plans
for the next pull requests to be validated and merged. Our next calls will be
Wednesday, September 9 and 23, 8:30 AM Pacific time. The notes from previous
calls, upcoming agenda and a link to join the call can be found
[here](https://docs.google.com/document/d/1-OuiKx4d7O6eLEJDBDKSRnSiUO2rgRR-c2Ga4AkrzOI).

### LLVM Flang

Work continues on LLVM Flang, concentrating on semantics, lowering and runtime
sufficient to compile and run Fortran 77 programs. We are fixing bugs we find
in running FCVS and other F77 test suites (and the F77 parts of non-F77
suites).

In conjunction with the MLIR-based code from the _fir-dev_ fork (the Fortran
IR used for lowering), Flang can compile and run most F77 programs. We
continue to work on refactoring necessary to upstream this fork into LLVM
flang proper.

Arm is working on changes to support a driver program to replace the temporary
driver we currently use.

Valentin Clement continues to contribute parsing and semantics changes for
OpenACC support.

### LFortran

What's new in LFortran:

* 143 Merge Requests were merged and 22 issues fixed in August 2020
* The C++ backend can now translate to C++ and compile many simple Fortran programs
* The parser can now parse a large subset of Fortran (if you find something that
  cannot be parsed, please [report](https://gitlab.com/lfortran/lfortran/-/issues) a bug). Not all the information is yet
  represented in the AST (so later stages of the compiler also work on a smaller
  subset), but one should not get parse errors anymore for most valid codes.
* Initial `lfortran fmt` subcommand for formatting Fortran files, you can
  provide feedback
  [here](https://fortran-lang.discourse.group/t/feedback-for-lfortran-fmt-to-format-fortran-source-code/281).
* A new command `lfortran kernel` can run LFortran as a Jupyter kernel.
* LFortran itself gives a nice Python like stacktrace (on Linux and macOS) in
  Debug mode when an unhandled excetion happens or a segfault.

Our goal for September is to get LFortran working for a much larger subset of
Fortran and allow it to compile and run via the C++ translation backend (the
LLVM backend will follow soon after).

You can follow LFortran on Twitter for latest updates: [@lfortranorg](https://twitter.com/lfortranorg).

## Events

* We had our fourth Fortran Monthly call on August 20.
You can watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/fiAyhHkAKFc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As usual, subscribe to the [mailing list](https://groups.io/g/fortran-lang) and/or
join the [Discourse](https://fortran-lang.discourse.group) to stay tuned with the future meetings.

## Contributors

We thank everybody who contributed to fortran-lang in the past month by
commenting in any of these repositories:

* [fortran-lang/stdlib](https://github.com/fortran-lang/stdlib),
* [fortran-lang/fpm](https://github.com/fortran-lang/fpm),
* [fortran-lang/fpm-registry](https://github.com/fortran-lang/fpm-registry),
* [fortran-lang/fortran-lang.org](https://github.com/fortran-lang/fortran-lang.org),
* [fortran-lang/benchmarks](https://github.com/fortran-lang/benchmarks),
* [j3-fortran/fortran_proposals](https://github.com/j3-fortran/fortran_proposals):

<div id="gh-contributors" data-startdate="August 01 2020" data-enddate="August 31 2020" height="500px"></div>
