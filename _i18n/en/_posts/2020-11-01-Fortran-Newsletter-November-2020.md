---
layout: post
title: "Fortran newsletter: November 2020"
category: newsletter
author: Milan Curcic, Sebastian Ehlert, Laurence Kedward, Jeremie Vandenplas, Ivan Pribec, Ondřej Čertík, Gary Klimowicz, Brad Richardson
---

Welcome to the November 2020 edition of the monthly Fortran newsletter.
The newsletter comes out on the first calendar day of every month and details
Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

This month we've had a few additions and improvements to the website:

* [#152](https://github.com/fortran-lang/fortran-lang.org/pull/152):
New mini-book on setting up the Fortran development environment.
You can read it [here](https://fortran-lang.org/learn/os_setup).
* [#147](https://github.com/fortran-lang/fortran-lang.org/pull/147):
Automated posting to @fortranlang Twitter using twitter-together.
* [#155](https://github.com/fortran-lang/fortran-lang.org/pull/155):
Fix for a security vulnerability reported by the GitHub Security Team.
* The following packages were added to the
[Package Index](https://fortran-lang.org/packages):
atomsk, ddPCM, DFTB+, DFT-D4, ELPA, ELSI, FortJSON, fypp, HANDE, libmbd, libnegf,
mpifx, NTPoly, NWChem, OpenMolcas, PoisFFT, QMD-PROGRESS, scalapackfx,
tapenade, wannier90, and xtb.
* [#145](https://github.com/fortran-lang/fortran-lang.org/pull/145),
[#146](https://github.com/fortran-lang/fortran-lang.org/pull/146),
[#154](https://github.com/fortran-lang/fortran-lang.org/pull/154),
[#158](https://github.com/fortran-lang/fortran-lang.org/pull/158):
Minor fixes and improvements.

Ongoing work:

* [#160](https://github.com/fortran-lang/fortran-lang.org/pull/160) (WIP):
In-depth introduction for Fortran with Make.
* [#156](https://github.com/fortran-lang/fortran-lang.org/pull/156) (WIP):
Updating the mini-book on building programs.

[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.

## Fortran Standard Library

This month progress was made on a few pull requests:

* [#239](https://github.com/fortran-lang/stdlib/pull/239): Implementation of the `stdlib_bitsets` module. It provides a bitset data type.
* [#240](https://github.com/fortran-lang/stdlib/pull/240): Implementation of the `stdlib_stats_distribution` module. It provides probability distribution and statistical functions.
* [#243](https://github.com/fortran-lang/stdlib/pull/243): A proposition to support newline characters in the message provided to the logger.

Don't hesitate to test and review these pull requests!

Otherwise, ongoing discussions continue;
 * [#220](https://github.com/fortran-lang/stdlib/pull/220): API for file system operations: directory manipulation
 * [#241](https://github.com/fortran-lang/stdlib/pull/241): Include a `split` function (202X feature)


The candidate for file system operations to be included in stdlib is being developed by
[@MarDiehl](https://github.com/MarDiehl) and [@arjenmarkus](https://github.com/arjenmarkus)
in [this repository](https://github.com/MarDiehl/stdlib_os).
Please try it out and let us know how it works, if there are any issues, or if the API can be improved.

## Fortran Package Manager

What's new:

* [#213](https://github.com/fortran-lang/fpm/issues/213): Bootstrap fpm submodule support
* [#208](https://github.com/fortran-lang/fpm/issues/208): Minor fixes to `list_files` and `mkdir` in `fpm_filesystem`
* [#206](https://github.com/fortran-lang/fpm/issues/206): Add installation script in `install.sh`
* [#193](https://github.com/fortran-lang/fpm/issues/193): Local and remote package dependencies (Fortran fpm can now build itself)
* [#190](https://github.com/fortran-lang/fpm/issues/190): Auto discovery of executables
* [#189](https://github.com/fortran-lang/fpm/issues/189),
[#204](https://github.com/fortran-lang/fpm/issues/204),
[#203](https://github.com/fortran-lang/fpm/issues/203): Implement `fpm new` in Fortran fpm

Work in progress:

* [First beta release](https://github.com/fortran-lang/fpm/milestone/1) (WIP): First feature-complete release of the Fortran implementation.
* [#221](https://github.com/fortran-lang/fpm/issues/221) (WIP): Test and executable runner options
* [#220](https://github.com/fortran-lang/fpm/issues/220) (WIP): Compiler and flags
* [#216](https://github.com/fortran-lang/fpm/issues/216) (WIP): Remove bashism from install.sh
* [#209](https://github.com/fortran-lang/fpm/issues/209) (WIP): Add automatic documentation for Fortran fpm
* [#202](https://github.com/fortran-lang/fpm/issues/202) (WIP): Create package manifest with toml-f build interface

fpm is still in early development and we need as much help as we can get.
Here's how you can help today:

* Try to use it. Does it work? No? Let us know! Read the [fpm packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md) to learn how to build your package with fpm.
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features.
* Adapt your Fortran package for fpm and submit it to the [Registry](https://github.com/fortran-lang/fpm-registry).
* Improve the documentation.

The short-term goal of fpm is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy
environment in which new open source Fortran projects are created and published with ease.

## Compilers

### Classic Flang

We continue to evaluate and merge pull requests into the original Flang
compiler again. We pulled in several changes in October.

Recently merged pull requests into Classic Flang include:
* [PR#660: Enable support for simd directives](https://github.com/flang-compiler/flang/pull/660)
* [PR#878: [DebugInfo]: Fix for missing DISPFlagOptimized in debug metadata](https://github.com/flang-compiler/flang/pull/878)
* [PR#910: Fix f90_correct tests](https://github.com/flang-compiler/flang/pull/910)
* [PR#922: Fix private flag overwrite in find_def_in_most_recent_scope()](https://github.com/flang-compiler/flang/pull/922)
* [PR#927: f90_correct: exclude tests failing with LLVM 10 on OpenPOWER](https://github.com/flang-compiler/flang/pull/927)
* [PR#930: Fix HTML docs generation](https://github.com/flang-compiler/flang/pull/930)
* [PR#931: [flang2] Fix segmentation faults (#421)](https://github.com/flang-compiler/flang/pull/931)
* [PR#932: [flang1] Do not assume unempty derived types](https://github.com/flang-compiler/flang/pull/932)
* [PR#938: [flang2] Fixing possible crash due to ivl being NULL in dinit.cpp](https://github.com/flang-compiler/flang/pull/938)

The Classic Flang biweekly call has been set up to discuss issues and plans
for the next pull requests to be validated and merged. Our next calls will be
Wednesday, November 4 and 18, 8:00 AM Pacific time (note the time change).
The notes from previous calls, upcoming agenda and a link to join the call can be found
[here](https://docs.google.com/document/d/1-OuiKx4d7O6eLEJDBDKSRnSiUO2rgRR-c2Ga4AkrzOI).

### LLVM Flang

Work continues on LLVM Flang, concentrating on semantics, lowering and runtime.

In conjunction with the MLIR-based code from the _fir-dev_ fork (the Fortran
IR used for lowering), Flang can compile and run most F77 programs,
including the Fortran Compiler Validation Suite (FCVS).

Pat McCormick is working on an RFC for the merge of the lowering code
in the fir-dev fork into LLVM master.
The goal is to expedite this in a way that is acceptable to the Flang community,
so we can do further work in the single master branch.

Arm continues to contribute changes toward a full-fledged driver for flang.

AMD continues to add support for OpenMP semantics and lowering.

Valentin Clement continues to contribute parsing and semantics changes for
OpenACC support.

Michael Kruse continues to add support for building Flang on Windows with MSVC
to the point that he can build and test Flang on Windows.

### LFortran

What's new in LFortran:

* 9 Merge Requests were merged and 5 issues fixed in October 2020
* We gave LFortran
  [talk](https://cfp.jupytercon.com/2020/schedule/presentation/169/lfortran-interactive-llvm-based-fortran-compiler-for-modern-architectures/)
  at JupyterCon 2020
* A prototype compiler implementation of conditional expressions for the
  October 2020 Fortran Standards Committee meeting
  ([!645](https://gitlab.com/lfortran/lfortran/-/merge_requests/645))
* Better code formatting support (`lfortran fmt`)
* Improvements to AST
* Capture stdout on Windows in a Jupyter notebook
  ([!642](https://gitlab.com/lfortran/lfortran/-/merge_requests/642))

You can follow LFortran on Twitter for latest updates: [@lfortranorg](https://twitter.com/lfortranorg).

## Events

* The US Fortran Standards Committee held a virtual meeting from October 12-14.
You can read the summary and the discussion [here](https://github.com/j3-fortran/fortran_proposals/issues/185) and all the documents [here](https://j3-fortran.org/doc/meeting/222).

* We had our 5th Fortran Monthly call on October 27.
You can watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/om869cZHeRU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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

<div id="gh-contributors" data-startdate="October 01 2020" data-enddate="October 31 2020" height="500px"></div>
