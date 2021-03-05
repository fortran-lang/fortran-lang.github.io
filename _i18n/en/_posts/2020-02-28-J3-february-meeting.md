---
layout: post
title: J3 February 2020 Meeting
category: newsletter
author: Ondřej Čertík and Zach Jibben
---

The J3 Fortran Committee meeting took place in Las Vegas, NV, on February 24-28,
2020.

## Attendance

The following people / companies attended:

Voting members:

1. Intel: Jon Steidel
2. HPE/Cray: Bill Long
3. NVIDIA: Peter Klausler, Gary Klimowicz
4. IBM: Daniel Chen
5. ARM: Srinath Vadlamani
6. NCAR: Dan Nagle, Magne Haveraaen
7. NASA: Tom Clune
8. JPL: Van Sneider
9. LANL: Zach Jibben, Ondřej Čertík
10. ORNL: Reuben Budiardja
11. LBNL: Brian Friesen
12. Sandia: Damian Rouson
13. Lionel: Steven Lionel, Malcolm Cohen, Vipul Parekh
14. Corbett: Bob Corbett

Others:

15. AMD: Richard Bleikamp
16. WG23: Stephen Michell (convenor), Erhard Ploedereder (member)
17. Structural Integrity: Brad Richardson

## Proposals Discussed at Plenary

### Monday 2/24

### Tuesday 2/25

* [#22] : Default values of optional arguments (<https://j3-fortran.org/doc/year/20/20-107.txt>)

### Wednesday 2/26

* [#157] : Rank-agnostic array element and section denotation (<https://j3-fortran.org/doc/year/20/20-113.txt>, <https://j3-fortran.org/doc/year/20/20-115.txt>)
* [#158] : TYPEOF and CLASSOF (<https://j3-fortran.org/doc/year/20/20-114.txt>)
* [#1] : Namespace for modules (<https://j3-fortran.org/doc/year/20/20-108.txt>)
* Interpretation: FORM TEAM and failed images (<https://j3-fortran.org/doc/year/20/20-102r1.txt>)
* Interpretation: Collective subroutines and STAT= (<https://j3-fortran.org/doc/year/20/20-104r1.txt>)

### Thursday 2/27

* Interpretation: events that cause variables to become undefined (<https://j3-fortran.org/doc/year/20/20-119.txt>)
* Edits for SIMPLE procedures (<https://j3-fortran.org/doc/year/20/20-116.txt>)
* BFLOAT16 (<https://j3-fortran.org/doc/year/20/20-118.txt>)
* [#146] : Interpretation: allocatable component finalization (<https://j3-fortran.org/doc/year/20/20-117.txt>)

### Friday 2/28

* [#157] : Rank-agnostic syntax (<https://j3-fortran.org/doc/year/20/20-120.txt>). Passed unanimously with minor changes.
* [#156] : Protected components (<https://j3-fortran.org/doc/year/20/20-121.txt>). Withdrawn to address conflicting interests.
* [#160] : Edits for auto-allocate characters (<https://j3-fortran.org/doc/year/20/20-122.txt>). Passed unanimously with minor changes.
* Edits for procedure pointer association (<https://j3-fortran.org/doc/year/20/20-123.txt>). Passed unanimously.
* [#157] : Edits for rank-agnostic bounds (<https://j3-fortran.org/doc/year/20/20-124.txt>). Withdrawn because some edits were missing and need to be added. There were concerns about fitting into the framework of generics later on.
* [#157] : Edits for rank-agnostic array element and section denotation (<https://j3-fortran.org/doc/year/20/20-125.txt>). Failed (5 v 7). Missing edits, and disagreement on types vs rank-1 integers, the options need to be explored more.
* [#157] : Edits for rank-agnostic allocation and pointer assignment (<https://j3-fortran.org/doc/year/20/20-126.txt>). Passed unanimously with minor changes.
* Interpretation: Public namelist and private variable (<https://j3-fortran.org/doc/year/20/20-127.txt>). Straw vote (0 yes, 8 no, 9 undecided). Passed unanimously with "no" alternative.
* Interpretation F18/015 (<https://j3-fortran.org/doc/year/20/20-105.txt>). Passed unanimously.


## Skipped

This was on the plan but we did not get to it:

* [#5] : US 27 POINTER dummy arguments, INTENT, and target modification (<https://j3-fortran.org/doc/year/18/18-144r1.txt>)
* [#19] : Short-circuiting proposal

## More Details

More details available at
[j3-fortran/fortran_proposals #155](https://github.com/j3-fortran/fortran_proposals/issues/155) and at the official [minutes](https://j3-fortran.org/doc/year/20/minutes221.txt) from the meeting.


[#1]: https://github.com/j3-fortran/fortran_proposals/issues/1
[#5]: https://github.com/j3-fortran/fortran_proposals/issues/5
[#19]: https://github.com/j3-fortran/fortran_proposals/issues/19
[#22]: https://github.com/j3-fortran/fortran_proposals/issues/22
[#146]: https://github.com/j3-fortran/fortran_proposals/issues/146
[#156]: https://github.com/j3-fortran/fortran_proposals/issues/156
[#157]: https://github.com/j3-fortran/fortran_proposals/issues/157
[#158]: https://github.com/j3-fortran/fortran_proposals/issues/158
[#160]: https://github.com/j3-fortran/fortran_proposals/issues/160
