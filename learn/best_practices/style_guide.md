---
layout: book
title: Fortran Style Guide
permalink: /learn/best_practices/style_guide
---

Naming Convention
-----------------

Ultimately this is a matter of preference. Here is a style guide that we
like and that seems to be prevalent in most scientific codes (as well as
the Fortran standard library) and you are welcome to follow it.

1.  Use lowercase for all Fortran constructs (`do`, `subroutine`,
    `module`, ...).
2.  Follow short mathematical notation for mathematical
    variables/functions (`Ylm`, `Gamma`, `gamma`, `Enl`, `Rnl`, ...).
3.  For other names use all lowercase: try to keep names to one or two
    syllables; if more are required, use underscores to clarify
    (`sortpair`, `whitechar`, `meshexp`, `numstrings`, `linspace`,
    `meshgrid`, `argsort`, `spline`, `spline_interp`,
    `spline_interpolate`, `stoperr`, `stop_error`, `meshexp_der`).

For example "spline interpolation" can be shortened to
`spline_interpolation`, `spline_interpolate`, `spline_interp`, `spline`,
but not to `splineint` ("int" could mean integration, integer, etc. ---
too much ambiguity, even in the clear context of a computational code).
This is in contrast to `get_argument()` where `getarg()` is perfectly
clean and clear.

The above are general guidelines. In general, choosing the right name
certainly depends on the word being truncated as to whether the first
syllable is sufficient. Usually it is but clearly not always. Thus some
thought should go into step "try to keep names to 2 syllables or less"
since it can really affect the indicativeness and simplicity. Simple
consistent naming rules are a real help in this regard -- for both
collaboration and for one's own sanity when going back to some old code
you haven't seen in while.

Indentation
-----------

Use a consistent indentation to make your code readable.
The amount of indentation is a matter of preference, the most common choices
are two, three or four spaces.

Comparison to Other Languages
-----------------------------

On the other hand, in most of the rest of the programming world, where
the main focus is, in one form or another, on defining and using large
sets of complex objects, with tons of properties and behaviors, known
only in the code in which they are defined (as opposed to defined by the
same notation throughout the literature), it makes more sense to use
longer, more descriptive names. The naming conventions one sees used in
more general-purpose languages such as C++ and Python, therefore, are
perfectly consistent with their more general-purpose missions. But
Fortran has a different mission (numerical scientific computing).
