---
layout: post
title: "Fortran newsletter: July 2020"
category: newsletter
author: Milan Curcic, Laurence Kedward, and Jérémie Vandenplas
---

Welcome to the July 2020 edition of the monthly Fortran newsletter.
The newsletter comes out on the first calendar day of every month
and details Fortran news from the previous month.

<ul id="page-nav"></ul>

## fortran-lang.org

Work has continued on the Fortran-lang website, including a new community page and additional tutorial content:

* [#98](https://github.com/fortran-lang/fortran-lang.org/pull/98): updated the [Quickstart mini-book](https://fortran-lang.org/learn/quickstart/derived_types) tutorial with a comprehensive overview of derived types;

* [#99](https://github.com/fortran-lang/fortran-lang.org/pull/99): added a second mini-book tutorial to the [Learn](https://fortran-lang.org/learn) page on building compiled programs and libraries;

* [#100](https://github.com/fortran-lang/fortran-lang.org/pull/100): added a new top-level web-page for Fortran-lang community projects.
The page gives useful information and links for new contributors, as well as acknowledging each of our many existing contributors.
Check it out at <https://fortran-lang.org/community>.

Ongoing work:

* [#101](https://github.com/fortran-lang/fortran-lang.org/issues/101): Code style for Fortran examples in the tutorials.
See the corresponding community poll and discussion on [Discourse](https://fortran-lang.discourse.group/t/should-tutorials-on-fortran-lang-org-follow-a-consistent-style-for-code-listings/134);

* [#112](https://github.com/fortran-lang/fortran-lang.org/issues/112): Plan for core language tutorials.

[Let us know](https://github.com/fortran-lang/fortran-lang.org/issues) if you have any suggestions for the website and its content.
We welcome any new contributors to the website and the tutorials page in particular - see the [contributor guide](https://github.com/fortran-lang/fortran-lang.org/blob/master/CONTRIBUTING.md) for how to get started.

__Did you know__ you don't need to know HTML or any fancy languages to contribute to the website;
all of the online tutorials and most of the website content are written in [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet), a simple markup language for formatting text - don't worry if you haven't used it before, it's very easy to pick up!


## Fortran Standard Library

What's new in the Fortran Standard Library:

* [#209](https://github.com/fortran-lang/stdlib/pull/209)
Implements Simpson's rule for 1-d arrays (`simps` and `simps_weights`) in the
quadrature module (`stdlib_experimental_quadrature`).
* [#205](https://github.com/fortran-lang/stdlib/pull/205)
Tests for and improved standard conformance.

Some miscellaneous fixes and improvements:

* [#208](https://github.com/fortran-lang/stdlib/pull/208)
Fixes to support Intel Fortran compilers
* [#210](https://github.com/fortran-lang/stdlib/pull/210)
Fixes to support NAG compiler
* [#207](https://github.com/fortran-lang/stdlib/pull/207)
[#211](https://github.com/fortran-lang/stdlib/pull/211)
Other minor fixes and improvements

## Fortran Package Manager

What's new in fpm:

* [#99](https://github.com/fortran-lang/fpm/pull/99)
fpm now lets you specify a custom build script or a Makefile to use.
This will help building packages that use a custom structure and/or external
dependencies in other languages.
* [#89](https://github.com/fortran-lang/fpm/pull/89)
Allow specifying specific tests or executables to run via command-line arguments.
* [#85](https://github.com/fortran-lang/fpm/pull/85)
Enables having specific dependencies for tests and executables.
* [#97](https://github.com/fortran-lang/fpm/pull/97)
[#100](https://github.com/fortran-lang/fpm/pull/100)
[#101](https://github.com/fortran-lang/fpm/pull/101)
Minor improvements to the README.

fpm is still in very early development, and we need as much help as we can get.
Here's how you can help today:

* Try to use it. Does it work? No? Let us know! Read the [fpm packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md) to learn how to build your package with fpm.
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features.
* Adapt your Fortran package for fpm.
* Improve the documentation.

The short term goal of fpm is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy
environment in which new open source Fortran projects are created and published with ease.

## Events

* We had our second Fortran Monthly call on June 19.
You can read watch the recording below:

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/i-gRNGRzugc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

As usual, subscribe to the [mailing list](https://groups.io/g/fortran-lang) and/or
join the [Discourse](https://fortran-lang.discourse.group) to stay tuned with the future meetings.

* [FortranCon 2020](https://tcevents.chem.uzh.ch/event/12) began today (July 2),
with many interesting talks.
See the talk schedule [here](https://tcevents.chem.uzh.ch/event/12/timetable/#20200702.detailed).

## Contributors

We thank everybody who contributed to fortran-lang in the past month by
commenting in any of the four repositories:

* [fortran-lang/stdlib](https://github.com/fortran-lang/stdlib),
* [fortran-lang/fpm](https://github.com/fortran-lang/fpm),
* [fortran-lang/fortran-lang.org](https://github.com/fortran-lang/fortran-lang.org),
* [j3-fortran/fortran_proposals](https://github.com/j3-fortran/fortran_proposals):



<div id="gh-contributors" data-startdate="June 01 2020" data-enddate="June 30 2020" height="500px"></div>
