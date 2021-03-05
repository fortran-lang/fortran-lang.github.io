---
layout: post
title: "Fortran newsletter: May 2020"
category: newsletter
author: Milan Curcic
---

```fortran
print *, 'Hello, World!' 
```

Welcome to the first monthly Fortran newsletter.
It will come out on the first calendar day of every month, 
detailing Fortran news from the previous month.

* [This website](#this-website)
* [Standard Library](#standard-library)
* [Package Manager](#package-manager)
* [WG5 Convenor candidates](#wg5-convenor-candidates)
* [Events](#events)
* [Who's hiring?](#whos-hiring)

## This website

If you came to this newsletter from elsewhere, welcome to the new Fortran website.
We built this site mid-April and hope for it to be _the_ home of Fortran on the internet,
which traditionally there hasn't been any to date.
Look around and [let us know](https://github.com/fortran-lang/fortran-lang.github.io/issues) 
if you have any suggestions for improvement.
Specifically, [Learn](/learn) and [Packages](/packages) are the pages that 
we'll be focusing on in the coming months. 
Please help us make them better!

## Standard Library

Here's what's new in Fortran Standard Library:

* [#172](https://github.com/fortran-lang/stdlib/pull/172)
New function `cov` in the `stdlib_experimental_stats` module to compute covariance of array elements.
Read the full specification [here](https://github.com/fortran-lang/stdlib/blob/master/src/stdlib_experimental_stats.md#cov---covariance-of-array-elements).

* [#168](https://github.com/fortran-lang/stdlib/pull/168)
Specify recommended order of attributes for dummy arguments in the 
[Stdlib style guide](https://github.com/fortran-lang/stdlib/blob/master/STYLE_GUIDE.md).

* [#173](https://github.com/fortran-lang/stdlib/pull/173)
Minor bug fix.

* [#170](https://github.com/fortran-lang/stdlib/pull/170)
WIP: Addition of `diag`, `eye`, and `trace` functions to make working with 
matrices easier.
 
## Package Manager

In the past month we've seen the first working implementation of the [Fortran Package Manager (FPM)](https://github.com/fortran-lang/fpm).
Specifically:

* FPM supports three commands:
  - `fpm build`--compiles and links your application and/or library.
  - `fpm test`--runs tests if your package has any test programs.
  - `fpm run`--runs the application if your package has an executable program.
* FPM can build an executable program, a library, or a combination of both.
* Currently only gfortran is supported as the compiler backend. FPM will suport other compilers soon.

Read the [FPM packaging guide](https://github.com/fortran-lang/fpm/blob/master/PACKAGING.md)
to learn how to build your package with FPM.

FPM is still in very early development, and we need as much help as we can get.
Here's how you can help today:

* Try to use it. Does it work? No? Let us know!
* Browse the [open issues](https://github.com/fortran-lang/fpm/issues) and see if you can help implement any fixes or features. 
* Adapt your Fortran package for FPM.
* Improve the documentation.

The short term goal of FPM is to make development and installation of Fortran packages with dependencies easier.
Its long term goal is to build a rich and decentralized ecosystem of Fortran packages and create a healthy 
environment in which new open source Fortran projects are created and published with ease.

## WG5 Convenor candidates

Last month was also the deadline for the [WG5](https://wg5-fortran.org/)
convenor candidates to apply for the next 3-year term (2021-2024).
There are two candidates:

* [Steve Lionel](https://stevelionel.com), who is also the current WG5 convenor,
announced running for another term.
Read Steve's [post](https://stevelionel.com/drfortran/2020/04/25/doctor-fortran-in-forward)
about how he has guided the standardization process over the past three years and his direction for the future.

* [Ondřej Čertík](https://ondrejcertik.com) has also announced announced to run
for the WG5 convenor.
Read Ondřej's [announcement](https://ondrejcertik.com/blog/2020/04/running-for-wg5-convenor-announcement/)
and [platform](https://github.com/certik/wg5_platform_2020)
that detail current issues with Fortran language development and how to
overcome them going forward.

## Events

* [OpenTeams](https://openteams.com) and [QuanSight](https://quansight.com) hosted Ondřej Čertík and Milan Curcic
in the Episode 40 of the Open Source Directions Webinar.
They talked about the current state and future of Fortran, as well as about building the Fortran community and developer tools.
Read more about it and watch the video [here](/newsletter/2020/04/18/Fortran-Webinar/).
* [FortranCon 2020](https://tcevents.chem.uzh.ch/event/12) will take place on July 2-4 in Zurich, Switzerland.
Virtual participation is enabled for both attendees and speakers.
Registration is free and due by June 1, 2020.
* J3/WG5 joint meeting will take place on October 12-16 in Las Vegas, Nevada.
You can submit a proposal for the Standards committee [here](https://github.com/j3-fortran/fortran_proposals).
For reference, you can read the [notes from the February meeting](/newsletter/2020/02/28/J3-february-meeting).

## Who's hiring?

* [Intel Corporation (Santa Clara, CA): Software Engineer, Fortran](https://g.co/kgs/aogdeh)
* [Intel Corporation (Hillsboro, OR): Software Engineer, Fortran](https://g.co/kgs/5X3d2Y)
* [Pozent (York, PA): Fortran Technical Lead](https://g.co/kgs/yuaohU)
* [American Cybersystems, Inc. (Binghamton, NY): Software Engineer (Fortran, C/C++, Ada, C#, Java, Radar)](https://g.co/kgs/VAWjWk)
* [BravoTech (Dallas, TX): C++ / Fortran Developer](https://g.co/kgs/eLsn63)
* [Siemens (Milford, OH): CAE Software Engineer (Fortran or C++) Design and Topology Optimization](https://g.co/kgs/eYftiA)
