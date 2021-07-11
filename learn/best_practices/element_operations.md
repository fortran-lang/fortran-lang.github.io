---
layout: book
title: Element-wise Operations on Arrays
permalink: /learn/best_practices/element_operations
---

There are three approaches to perform element-wise operations on arrays when using subroutines and functions:

-   `elemental` procedures
-   *explicit-shape* arrays
-   implementing the operation for vectors and write simple wrapper
    subroutines (that use `reshape` internally) for each array shape

In the first approach, one uses the `elemental` keyword to create a
function like this:

``` fortran
real(dp) elemental function nroot(n, x) result(y)
  integer, intent(in) :: n
  real(dp), intent(in) :: x
  y = x**(1._dp / n)
end function
```

All arguments (in and out) must be scalars. You can then use this
function with arrays of any (compatible) shape, for example:

``` fortran
print *, nroot(2, 9._dp)
print *, nroot(2, [1._dp, 4._dp, 9._dp, 10._dp])
print *, nroot(2, reshape([1._dp, 4._dp, 9._dp, 10._dp], [2, 2]))
print *, nroot([2, 3, 4, 5], [1._dp, 4._dp, 9._dp, 10._dp])
print *, nroot([2, 3, 4, 5], 4._dp)
```

The output will be:

``` fortran
3.0000000000000000
1.0000000000000000        2.0000000000000000        3.0000000000000000        3.1622776601683795
1.0000000000000000        2.0000000000000000        3.0000000000000000        3.1622776601683795
1.0000000000000000        1.5874010519681994        1.7320508075688772        1.5848931924611136
2.0000000000000000        1.5874010519681994        1.4142135623730951        1.3195079107728942
```

In the above, typically `n` is a parameter and `x` is the array of an
arbitrary shape, but as you can see, Fortran does not care as long as
the final operation makes sense (if one argument is an array, then the
other arguments must be either arrays of the same shape or scalars). If
it does not, you will get a compiler error.

The `elemental` keyword implies the `pure` keyword, so the procedure
must be pure. It results that `elemental procedures` can only use `pure` procedures and have no side effects.

If the elemental procedure algorithm can be made faster using array
operations inside, or if for some reasons the arguments must be arrays of
incompatible shapes, then one should use the other two approaches. One
can make `nroot` operate on a vector and write a simple wrapper for
other array shapes, e.g.:

``` fortran
function nroot(n, x) result(y)
  integer, intent(in) :: n
  real(dp), intent(in) :: x(:)
  real(dp) :: y(size(x))
  y = x**(1._dp / n)
end function

function nroot_0d(n, x) result(y)
  integer, intent(in) :: n
  real(dp), intent(in) :: x
  real(dp) :: y
  real(dp) :: tmp(1)
  tmp = nroot(n, [x])
  y = tmp(1)
end function

function nroot_2d(n, x) result(y)
  integer, intent(in) :: n
  real(dp), intent(in) :: x(:, :)
  real(dp) :: y(size(x, 1), size(x, 2))
  y = reshape(nroot(n, reshape(x, [size(x)])), [size(x, 1), size(x, 2)])
end function
```

And use as follows:

``` fortran
print *, nroot_0d(2, 9._dp)
print *, nroot(2, [1._dp, 4._dp, 9._dp, 10._dp])
print *, nroot_2d(2, reshape([1._dp, 4._dp, 9._dp, 10._dp], [2, 2]))
```

This will print:

``` fortran
3.0000000000000000
1.0000000000000000        2.0000000000000000        3.0000000000000000        3.1622776601683795
1.0000000000000000        2.0000000000000000        3.0000000000000000        3.1622776601683795
```

Or one can use *explicit-shape* arrays as
follows:

``` fortran
function nroot(n, k, x) result(y)
  integer, intent(in) :: n, k
  real(dp), intent(in) :: x(k)
  real(dp) :: y(k)
  y = x**(1._dp / n)
end function
```

Use as follows:

``` fortran
print *, nroot(2, 1, [9._dp])
print *, nroot(2, 4, [1._dp, 4._dp, 9._dp, 10._dp])
print *, nroot(2, 4, reshape([1._dp, 4._dp, 9._dp, 10._dp], [2, 2]))
```

The output is the same as before:

``` fortran
3.0000000000000000
1.0000000000000000        2.0000000000000000        3.0000000000000000        3.1622776601683795
1.0000000000000000        2.0000000000000000        3.0000000000000000        3.1622776601683795
```
