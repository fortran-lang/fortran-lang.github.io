---
layout: book
title: Arrays
permalink: /learn/best_practices/arrays
---

Arrays are a central object in Fortran. The creation of dynamic sized arrays
is discussed in the [allocatable arrays arrays](./allocatable_arrays.html).

To pass arrays to procedures four ways are available

1. *assumed-shape* arrays
4. *assumed-rank* arrays
2. *explicit-shape* arrays
3. *assumed-size* arrays

The preferred way to pass arrays to procedures is as *assumed-shape* arrays

```fortran
subroutine f(r)
  real(dp), intent(out) :: r(:)
  integer :: n, i
  n = size(r)
  do i = 1, n
    r(i) = 1.0_dp / i**2
  end do
end subroutine f
```

Higher dimensional arrays can be passed in a similar way.

```fortran
subroutine g(A)
  real(dp), intent(in) :: A(:, :)
  ...
end subroutine g
```

The array is simply passed by

```fortran
real(dp) :: r(5)
call f(r)
```

In this case no array copy is done, which has the advantage that the shape and size
information is automatically passed along and checked at compile and optionally at
runtime.
Similarly, array strides can be passed without requiring a copy of the array but as
*assumed-shape* discriptor:

```fortran
real(dp) :: r(10)
call f(r(1:10:2))
call f(r(2:10:2))
```

This should always be your default way of passing arrays in and out of subroutines.
Avoid passing arrays as whole slices, as it obfuscates the actual intent of the code:

```fortran
real(dp) :: r(10)
call f(r(:))
```

In case more general arrays should be passed to a procedure the *assumed-rank*
functionality introduced in the Fortran 2018 standard can be used

```fortran
subroutine h(r)
  real(dp), intent(in) :: r(..)
  select rank(r)
  rank(1)
  ! ...
  rank(2)
  ! ...
  end select
end subroutine h
```

The actual rank can be queried at runtime using the ``select rank`` construct.
This easily allows to create more generic functions that have to deal with
differnet array ranks.

*Explicit-shape* arrays can be useful for returning data from functions.
Most of their functionality can be provided by *assumed-shape* and *assumed-rank*
arrays but they find frequent use for interfacing with C or in legacy Fortran
procedures, therefore they will be discussed briefly here.

To use *explicit-shape* arrays, the dimension has to be passed explicitly as dummy
argument like in the example below

``` fortran
subroutine f(n, r)
  integer, intent(in) :: n
  real(dp), intent(out) :: r(n)
  integer :: i
  do i = 1, n
    r(i) = 1.0_dp / i**2
  end do
end subroutine
```

For high-dimensional arrays additional indices have to be passed.

``` fortran
subroutine g(m, n, A)
  integer, intent(in) :: m, n
  real(dp), intent(in) :: A(m, n)
  ...
end subroutine
```

The routines can be invoked by

``` fortran
real(dp) :: r(5), s(3, 4)
call f(size(r), r)
call g(size(s, 1), size(s, 2), s)
```

Note that the shape is not checked, therefore the following would be valid code
with will potentially yield incorrect results:

```fortran
real(dp) :: s(3, 4)
call g(size(s), 1, s)  ! s(12, 1) in g
call g(size(s, 2), size(s, 1), s)  ! s(4, 3) in g
```

In this case the memory layout is preserved but the shape is changed.
Also, *explicit-shape* arrays require contiguous memory and will create temporary
arrays in case non-contiguous array strides are passed.

To return an array from a function with *explicit-shape* use

``` fortran
function f(n) result(r)
  integer, intent(in) :: n
  real(dp) :: r(n)
  integer :: i
  do i = 1, n
    r(i) = 1.0_dp / i**2
  end do
end function
```

Finally, there are *assumed-size* arrays, which provide the least compile and runtime
checking and can be found be found frequently in legacy code, they should be avoided
in favour of *assumed-shape* or *assumed-rank* arrays.
An *assumed-size* array dummy argument is identified by an asterisk as the last dimension,
this disables the usage of this array with many intrinsic functions, like ``size`` or
``shape``.

To check for the correct size and shape of an *assumed-shape* array the ``size`` and
``shape`` intrinsic functions can be used to query for those properties

```fortran
if (size(r) /= 4) error stop "Incorrect size of 'r'"
if (any(shape(r) /= [2, 2])) error stop "Incorrect shape of 'r'"
```

Note that ``size`` returns the total size of all dimensions, to obtain the shape of
a specific dimension add it as second argument to the function.

Arrays can be initialized by using an array constructor

```fortran
integer :: r(5)
r = [1, 2, 3, 4, 5]
```

The array constructor can be annoted with the type of the constructed array

```fortran
real(dp) :: r(5)
r = [real(dp) :: 1, 2, 3, 4, 5]
```

Implicit do loops can be used inside an array constructor as well

```fortran
integer :: i
real(dp) :: r(5)
r = [(real(i**2, dp), i = 1, size(r))]
```

In order for the array to start with different index than 1, do:

```fortran
subroutine print_eigenvalues(kappa_min, lam)
  integer, intent(in) :: kappa_min
  real(dp), intent(in) :: lam(kappa_min:)

  integer :: kappa
  do kappa = kappa_min, ubound(lam, 1)
    print *, kappa, lam(kappa)
  end do
end subroutine print_eigenvalues
```
