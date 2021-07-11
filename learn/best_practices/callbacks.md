---
layout: book
title: Callbacks
permalink: /learn/best_practices/callbacks
---

A callback is a function that is passed as an argument to another function.

The preferred way of creating such a callback is to provide an *abstract interface*
declaring the signature of the callback. This allows to use compile time checks
for the passed callback.

```fortran
module integrals
  use types, only: dp
  implicit none
  private
  public :: simpson, integratable_function

  abstract interface
    function integratable_function(x) result(func)
      import :: dp
      real(dp), intent(in) :: x
      real(dp) :: func
    end function
  end interface

contains

  function simpson(f, a, b) result(s)
    real(dp), intent(in) :: a, b
    procedure(integratable_function) :: f
    real(dp) :: s

    s = (b-a) / 6 * (f(a) + 4*f((a+b)/2) + f(b))
  end function simpson

end module integrals
```

The function can than be used with a callback by importing the module
as shown in the following example

```fortran
module demo_functions
  use types, only: dp
  implicit none
  private
  public :: test_integral

contains

  subroutine test_integral(a, k)
    real(dp), intent(in) :: a, k

    print *, simpson(f, 0._dp, pi)
    print *, simpson(f, 0._dp, 2*pi)
  contains

    function f(x) result(y)
      real(dp), intent(in) :: x
      real(dp) :: y
      y = a*sin(k*x)
    end function f
  end subroutine test_integral

end module demo_functions
```

Exporting the abstract interface allows to create procedure pointers with the
correct signature and also to extend the callback further like shown here

```fortran
module demo_integrals
  use types, only: dp
  use integrals, only: simpson, integratable_function
  implicit none
  private
  public :: simpson2, integratable_function

contains

  function simpson2(f, a, b) result(s)
    real(dp), intent(in) :: a, b
    procedure(integratable_function) :: f
    real(dp) :: s
    real(dp) :: mid
    mid = (a + b)/2
    s = simpson(f, a, mid) + simpson(f, mid, b)
  end function simpson2

end module demo_integrals
```
