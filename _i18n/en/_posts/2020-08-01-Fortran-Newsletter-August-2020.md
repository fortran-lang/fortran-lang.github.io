---
layout: post
title: "Fortran newsletter: August 2020"
category: newsletter
author: Ondřej Čertík, Milan Curcic, Laurence Kedward, Jérémie Vandenplas, Arjen Markus and Gary Klimowicz
---

Welcome to the August 2020 edition of the monthly Fortran newsletter.
The newsletter comes out on the first calendar day of every month
and details Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

We continued the work on the Fortran-lang website, including:

* [#116](https://github.com/fortran-lang/fortran-lang.org/pull/116): updates to the Quickstart tutorial on loop control and syntax

* [#120](https://github.com/fortran-lang/fortran-lang.org/pull/120): updated the
  [Book section](https://fortran-lang.org/learn/) with a comprehensive list of
  books about Fortran

* [#121](https://github.com/fortran-lang/fortran-lang.org/pull/121), [#122](https://github.com/fortran-lang/fortran-lang.org/pull/122), [#127](https://github.com/fortran-lang/fortran-lang.org/pull/127), [#128](https://github.com/fortran-lang/fortran-lang.org/pull/128): additional packages added to the Fortran-lang.org [packages](https://fortran-lang.org/packages) page
  
Ongoing work:

* [#117](https://github.com/fortran-lang/fortran-lang.org/issues/117): Adding a
  Benchmarks section, a new dedicated repository was created at
  https://github.com/fortran-lang/benchmarks and many details have been
  discussed in [issues](https://github.com/fortran-lang/benchmarks/issues) there



[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.


## Fortran Standard Library

What's new in the Fortran Standard Library:
* [#223](https://github.com/fortran-lang/stdlib/pull/223): the structure of the Fortran Standard Library has been modified for clarity and ease of use. With these changes, both experimental and stable procedures will reside together in the same modules. The status of the procedures (experimental vs stable) are documented in the code, in the specs, and in the [API docs](https://stdlib.fortran-lang.org/)

Main ongoing discussions:
* [#225](https://github.com/fortran-lang/stdlib/issues/225): Name convention for derived types in `stdlib`
* [#224](https://github.com/fortran-lang/stdlib/issues/224): Handling and propagating errors inside `stdlib`
* [#221](https://github.com/fortran-lang/stdlib/issues/221): API for a bitset data type
* [#201](https://github.com/fortran-lang/stdlib/issues/201): API for file system operations

## Fortran Package Manager

What's new in fpm:
* We created the [fpm-registry](https://github.com/fortran-lang/fpm-registry) repository,
which serves as a registry of fpm-enabled Fortran packages.
Please see the README there to learn how to contribute a package.
For now, the registry is simply a list of fpm-enabled Fortran packages that you can use as a dependency in your `fpm.toml` file.
Soon, this registry will be used to generate detailed metadata that will be used by fpm to allow you to search for packages from the command-line, e.g. `fpm search <package>` or similar.
* [#146](https://github.com/fortran-lang/fpm/issues/146): We discussed the design of the new Fortran implementation of fpm in a video call. We agreed on the need for an intermediate package model which will allow for clean separation of fpm frontends (user interface, parsing, and semantics) and fpm backends (fpm itself, CMake, Make, etc.).
* [#131](https://github.com/fortran-lang/fpm/pull/131),
[#132](https://github.com/fortran-lang/fpm/pull/132),
[#139](https://github.com/fortran-lang/fpm/pull/139),
[#140](https://github.com/fortran-lang/fpm/pull/140),
[#142](https://github.com/fortran-lang/fpm/pull/142),
[#145](https://github.com/fortran-lang/fpm/pull/145),
[#147](https://github.com/fortran-lang/fpm/pull/147),
[#148](https://github.com/fortran-lang/fpm/pull/148),
[#151](https://github.com/fortran-lang/fpm/pull/151):
We merged several pull requests toward the Fortran fpm implementation. The Haskell implementation has moved to the `fpm/bootstrap` directory, and the Fortran implementation is developed in `fpm/fpm`. The Fortran fpm is, of course, an fpm package itself so it can be built by the Haskell fpm. Soon, it will be able to be build by itself. 

fpm is still in very early development, and we need as much help as we can get.
Here's how you can help today:

* Try to use it. Does it work? No? Let us know! Read the [fpm packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md) to learn how to build your package with fpm.
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features.
* Adapt your Fortran package for fpm.
* Improve the documentation.

The short term goal of fpm is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy
environment in which new open source Fortran projects are created and published with ease.

##  Fortran benchmarks

We created the [benchmarks repository](https://github.com/fortran-lang/benchmarks) with the goal to design and implement a comprehensive set of benchmarks.
The benchmarks will aim to compare the performance of various Fortran compilers, as well as the performance of canonical algorithms implemented in Fortran and different languages.
If you'd like to contribute in any way, be it the design, implementation, or testing of benchmarks, please join the ongoing discussion [here](https://github.com/fortran-lang/benchmarks/issues).

## Classic Flang

We've begun to evaluate pull requests and merge them into the original Flang
compiler again. There is now a biweekly call to discuss issues and plans for
Classic Flang. The next call will be Wednesday, August 12, 8:30 AM Pacific time.
The notes from previous calls, upcoming agenda and a link to join the call can
be found [here](https://docs.google.com/document/d/1-OuiKx4d7O6eLEJDBDKSRnSiUO2rgRR-c2Ga4AkrzOI).

In the last call, AMD reviewed their outstanding pull requests for Fortran debug
metadata enhancements.

## LLVM Flang

Work continues on LLVM Flang, concentrating on semantics, lowering and runtime
sufficient to compile and run Fortran 77 programs. We are fixing bugs we find in
running FCVS and other test suites that use F77.

We cominue upstreaming the lowering code from the fir-dev fork (MLIR-based
Fortran IR) into the llvm-project repository. Arm is working on changes to
support a driver program to replace the throwaway driver we currently have.

AMD has been contributing parser and semantic processing for OpenMP constructs
like task wait, barrier and parallel constructs.

Changes have been made to default parse/unparse/compile processing to default to
gfortran (not NVIDIA Fortran).

Valentin Clement has been committing initial changes for OpenACC support.


## LFortran

What's new in LFortran:

* The initial prototype C++ backend can translate Fortran's `do concurrent` to C++'s `Kokkos::parallel_for`: [https://twitter.com/lfortranorg/status/1280764915242811393](https://twitter.com/lfortranorg/status/1280764915242811393)
* LFortran has a Twitter account for latest updates: [@lfortranorg](https://twitter.com/lfortranorg)
* Work is progressing on the production version of LFortran that is written in C++
* 22 Merge Requests were merged and 4 issues fixed in July 2020. Some notable ones:
  * [#163](https://gitlab.com/lfortran/lfortran/-/issues/163): Implement basic Fortran to C++ translation backend
  * [!410](https://gitlab.com/lfortran/lfortran/-/merge_requests/410): Make simple calculations work via LLVM in interactive mode
  * [!402](https://gitlab.com/lfortran/lfortran/-/merge_requests/402): Build ASR (Abstract Semantic Representation) properly for subroutines and functions

The short term goal is to get the C++ based production version of LFortran
matching most of the features from the Python prototype version and make a
public release. The long term goal is to build a modern Fortran compiler that
works with any production code and allows it to run efficiently on modern
hardware (CPUs and GPUs), both interactively and compiling to binaries, and
provide the basis for other tools such as the Fortran to C++ translation, editor
support, automatic documentation generation (and doctesting like in Python),
automatic formatting and others.

## Events

* [FortranCon 2020](https://tcevents.chem.uzh.ch/event/12) was held July 2 - 4.
with many interesting talks.
See the talk schedule
[here](https://tcevents.chem.uzh.ch/event/12/timetable/#20200702.detailed).
All presentations have been recorded and will be soon made available online by the FortranCon organizers.

* We had our third Fortran Monthly call on July 16.
You can read watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/_ojLReFvjbs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As usual, subscribe to the [mailing list](https://groups.io/g/fortran-lang) and/or
join the [Discourse](https://fortran-lang.discourse.group) to stay tuned with the future meetings.


## Contributors

We thank everybody who contributed to fortran-lang in the past month by
commenting in any of the four repositories:

* [fortran-lang/stdlib](https://github.com/fortran-lang/stdlib),
* [fortran-lang/fpm](https://github.com/fortran-lang/fpm),
* [fortran-lang/fortran-lang.org](https://github.com/fortran-lang/fortran-lang.org),
* [j3-fortran/fortran_proposals](https://github.com/j3-fortran/fortran_proposals):



<div id="gh-contributors" data-startdate="July 01 2020" data-enddate="July 31 2020" height="500px"></div>
