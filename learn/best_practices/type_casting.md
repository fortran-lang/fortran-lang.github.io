---
layout: book
title: Type Casting in Callbacks
permalink: /learn/best_practices/type_casting
---

There are essentially five different ways to do type casting, each with its own
advantages and disadvantages.

The methods I, II and V can be used both in C and Fortran. The methods
III and IV are only available in Fortran. The method VI is obsolete and
should not be used.

Work Arrays
-----------

Pass a "work array" which is packed with everything needed by
the caller and unpacked by the called routine. This is the old way --
e.g., how LAPACK does it.

Integrator:

``` fortran
module integrals
  use types, only: dp
  implicit none
  private
  public simpson

contains

real(dp) function simpson(f, a, b, data) result(s)
  real(dp), intent(in) :: a, b
  interface
    real(dp) function func(x, data)
    use types, only: dp
    implicit none
    real(dp), intent(in) :: x
    real(dp), intent(inout) :: data(:)
    end function
  end interface
  procedure(func) :: f
  real(dp), intent(inout) :: data(:)
  s = (b-a) / 6 * (f(a, data) + 4*f((a+b)/2, data) + f(b, data))
end function

end module
```

Usage:

``` fortran
module test
  use types, only: dp
  use integrals, only: simpson
  implicit none
  private
  public foo

contains

real(dp) function f(x, data) result(y)
  real(dp), intent(in) :: x
  real(dp), intent(inout) :: data(:)
  real(dp) :: a, k
  a = data(1)
  k = data(2)
  y = a*sin(k*x)
end function

subroutine foo(a, k)
  real(dp) :: a, k
  real(dp) :: data(2)
  data(1) = a
  data(2) = k
  print *, simpson(f, 0._dp, pi, data)
  print *, simpson(f, 0._dp, 2*pi, data)
end subroutine

end module
```

General Structure
-----------------

Define a general structure which encompass the variations you
actually need (or are even remotely likely to need going forward). This
single structure type can then change if needed as future
needs/ideas permit but won't likely need to change from passing, say,
real numbers to, say, and instantiation of a text editor.

Integrator:

``` fortran
module integrals
  use types, only: dp
  implicit none
  private
  public simpson, context

  type context
    ! This would be adjusted according to the problem to be solved.
    ! For example:
    real(dp) :: a, b, c, d
    integer :: i, j, k, l
    real(dp), pointer :: x(:), y(:)
    integer, pointer :: z(:)
  end type

contains

real(dp) function simpson(f, a, b, data) result(s)
  real(dp), intent(in) :: a, b
  interface
    real(dp) function func(x, data)
    use types, only: dp
    implicit none
    real(dp), intent(in) :: x
    type(context), intent(inout) :: data
    end function
  end interface
  procedure(func) :: f
  type(context), intent(inout) :: data
  s = (b-a) / 6 * (f(a, data) + 4*f((a+b)/2, data) + f(b, data))
end function

end module
```

Usage:

``` fortran
module test
  use types, only: dp
  use integrals, only: simpson, context
  implicit none
  private
  public foo

contains

real(dp) function f(x, data) result(y)
  real(dp), intent(in) :: x
  type(context), intent(inout) :: data
  real(dp) :: a, k
  a = data%a
  k = data%b
  y = a*sin(k*x)
end function

subroutine foo(a, k)
  real(dp) :: a, k
  type(context) :: data
  data%a = a
  data%b = k
  print *, simpson(f, 0._dp, pi, data)
  print *, simpson(f, 0._dp, 2*pi, data)
end subroutine

end module
```

There is only so much flexibility really needed. For example, you could
define two structure types for this purpose, one for Schroedinger and
one for Dirac. Each would then be sufficiently general and contain all
the needed pieces with all the right labels.

Point is: it needn't be "one abstract type to encompass all" or bust.
There are natural and viable options between "all" and "none".

Private Module Variables
------------------------

Hide the variable arguments completely by passing in module variables.

Integrator:

``` fortran
module integrals
  use types, only: dp
  implicit none
  private
  public simpson

contains

real(dp) function simpson(f, a, b) result(s)
  real(dp), intent(in) :: a, b
  interface
    real(dp) function func(x)
    use types, only: dp
    implicit none
    real(dp), intent(in) :: x
    end function
  end interface
  procedure(func) :: f
  s = (b-a) / 6 * (f(a) + 4*f((a+b)/2) + f(b))
end function

end module
```

Usage:

``` fortran
module test
  use types, only: dp
  use integrals, only: simpson
  implicit none
  private
  public foo

  real(dp) :: global_a, global_k

contains

real(dp) function f(x) result(y)
  real(dp), intent(in) :: x
  y = global_a*sin(global_k*x)
end function

subroutine foo(a, k)
  real(dp) :: a, k
  global_a = a
  global_k = k
  print *, simpson(f, 0._dp, pi)
  print *, simpson(f, 0._dp, 2*pi)
end subroutine

end module
```

However it is best to avoid such global variables -- even though really
just semi-global -- if possible. But sometimes it may be the simplest
cleanest way. However, with a bit of thought, usually there is a better,
safer, more explicit way along the lines of II or IV.

Nested functions
----------------

Integrator:

``` fortran
module integrals
  use types, only: dp
  implicit none
  private
  public simpson

contains

real(dp) function simpson(f, a, b) result(s)
  real(dp), intent(in) :: a, b
  interface
    real(dp) function func(x)
    use types, only: dp
    implicit none
    real(dp), intent(in) :: x
    end function
  end interface
  procedure(func) :: f
  s = (b-a) / 6 * (f(a) + 4*f((a+b)/2) + f(b))
end function

end module
```

Usage:

``` fortran
subroutine foo(a, k)
use integrals, only: simpson
real(dp) :: a, k
print *, simpson(f, 0._dp, pi)
print *, simpson(f, 0._dp, 2*pi)

contains

real(dp) function f(x) result(y)
real(dp), intent(in) :: x
y = a*sin(k*x)
end function f

end subroutine foo
```

Using type(c\_ptr) Pointer
--------------------------

In C, one would use the `void *` pointer. In Fortran, one can use
`type(c_ptr)` for exactly the same purpose.

Integrator:

``` fortran
module integrals
  use types, only: dp
  use iso_c_binding, only: c_ptr
  implicit none
  private
  public simpson

contains

real(dp) function simpson(f, a, b, data) result(s)
  real(dp), intent(in) :: a, b
  interface
    real(dp) function func(x, data)
    use types, only: dp
    implicit none
    real(dp), intent(in) :: x
    type(c_ptr), intent(in) :: data
    end function
  end interface
  procedure(func) :: f
  type(c_ptr), intent(in) :: data
  s = (b-a) / 6 * (f(a, data) + 4*f((a+b)/2, data) + f(b, data))
end function

end module
```

Usage:

``` fortran
module test
  use types, only: dp
  use integrals, only: simpson
  use iso_c_binding, only: c_ptr, c_loc, c_f_pointer
  implicit none
  private
  public foo

  type f_data
    ! Only contains data that we need for our particular callback.
    real(dp) :: a, k
  end type

contains

real(dp) function f(x, data) result(y)
  real(dp), intent(in) :: x
  type(c_ptr), intent(in) :: data
  type(f_data), pointer :: d
  call c_f_pointer(data, d)
  y = d%a * sin(d%k * x)
end function

subroutine foo(a, k)
  real(dp) :: a, k
  type(f_data), target :: data
  data%a = a
  data%k = k
  print *, simpson(f, 0._dp, pi, c_loc(data))
  print *, simpson(f, 0._dp, 2*pi, c_loc(data))
end subroutine

end module
```

As always, with the advantages of such re-casting, as Fortran lets you
do if you really want to, come also the disadvantages that fewer
compile- and run-time checks are possible to catch errors; and with
that, inevitably more leaky, bug-prone code. So one always has to
balance the costs and benefits.

Usually, in the context of scientific programming, where the main thrust
is to represent and solve precise mathematical formulations (as opposed
to create a GUI with some untold number of buttons, drop-downs, and
other interface elements), simplest, least bug-prone, and fastest is to
use one of the previous approaches.

transfer() Intrinsic Function
-----------------------------

Before Fortran 2003, the only way to do type casting was using the
`transfer` intrinsic function. It is functionally equivalent to the
method V, but more verbose and more error prone. It is now obsolete and
one should use the method V instead.

Examples:

<http://jblevins.org/log/transfer>

<http://jblevins.org/research/generic-list.pdf>

<http://www.macresearch.org/advanced_fortran_90_callbacks_with_the_transfer_function>

Object Oriented Approach
------------------------

The module:

``` fortran
module integrals

  use types, only: dp
  implicit none
  private

  public :: integrand, simpson

  ! User extends this type
  type, abstract :: integrand
  contains
    procedure(func), deferred :: eval
  end type

  abstract interface
    function func(this, x) result(fx)
      import :: integrand, dp
      class(integrand) :: this
      real(dp), intent(in) :: x
      real(dp) :: fx
    end function
  end interface

contains

real(dp) function simpson(f, a, b) result(s)
  class(integrand) :: f
  real(dp), intent(in) :: a, b
  s = ((b-a)/6) * (f%eval(a) + 4*f%eval((a+b)/2) + f%eval(b))
end function

end module
```

The abstract type prescribes exactly what the integration routine needs,
namely a method to evaluate the function, but imposes nothing else on
the user. The user extends this type, providing a concrete
implementation of the eval type bound procedure and adding necessary
context data as components of the extended type.

Usage:

``` fortran
module example_usage

  use types, only: dp
  use integrals, only: integrand, simpson
  implicit none
  private

  public :: foo

  type, extends(integrand) :: my_integrand
    real(dp) :: a, k
  contains
    procedure :: eval => f
  end type

contains

function f(this, x) result(fx)
  class(my_integrand) :: this
  real(dp), intent(in) :: x
  real(dp) :: fx
  fx = this%a*sin(this%k*x)
end function

subroutine foo(a, k)
  real(dp) :: a, k
  type(my_integrand) :: my_f
  my_f%a = a
  my_f%k = k
  print *, simpson(my_f, 0.0_dp, 1.0_dp)
  print *, simpson(my_f, 0.0_dp, 2.0_dp)
end subroutine

end module
```

Complete Example of void \* vs type(c\_ptr) and transfer()
----------------------------------------------------------

Here are three equivalent codes: one in C using `void *` and two codes
in Fortran using `type(c_ptr)` and `transfer()`:

| Language &nbsp; | Method               | Link                              |
|-----------------|----------------------|-----------------------------------|
| C               | `void *`             | <https://gist.github.com/1665641> |
| Fortran         | `type(c_ptr)` &nbsp; | <https://gist.github.com/1665626> |
| Fortran         | `transfer()`         | <https://gist.github.com/1665630> |

The C code uses the standard C approach for writing extensible libraries
that accept callbacks and contexts. The two Fortran codes show how to do
the same. The `type(c_ptr)` method is equivalent to the C version and
that is the approach that should be used.

The `transfer()` method is here for completeness only (before Fortran
2003, it was the only way) and it is a little cumbersome, because the
user needs to create auxiliary conversion functions for each of his
types. As such, the `type(c_ptr)` method should be used instead.
