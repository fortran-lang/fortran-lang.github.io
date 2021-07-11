---
layout: book
title: Floating Point Numbers
permalink: /learn/best_practices/floating_point
---

The default representation of floating point numbers is using single precision
(usually 32 bits / 4 bytes). For most application a higher precision is required.
For this purpose a custom kind parameter can be defined.
The recommended way of defining kind parameters is to use

```fortran
integer, parameter :: dp = selected_real_kind(15)
```

For many purposes it also suffices to directly infer the kind parameter from
a literal like here

```fortran
integer, parameter :: dp = kind(0.0d0)
```

or to rename the imported kind parameter from the ``iso_fortran_env`` module

```fortran
use, intrinsic :: iso_fortran_env, only : dp => real64
```

For some insightful thoughts on kind parameters see
<a href="https://web.archive.org/web/20200930090137/https://stevelionel.com/drfortran/2017/03/27/doctor-fortran-in-it-takes-all-kinds/">Doctor Fortran in it takes all KINDs</a>.

It is recommended to have a central module to define kind parameters and include
them with use as necessary. An example for such a module is given with

```
!> Numerical storage size parameters for real and integer values
module kind_parameter
   implicit none
   public

   !> Single precision real numbers, 6 digits, range 10⁻³⁷ to 10³⁷-1; 32 bits
   integer, parameter :: sp = selected_real_kind(6, 37)
   !> Double precision real numbers, 15 digits, range 10⁻³⁰⁷ to 10³⁰⁷-1; 64 bits
   integer, parameter :: dp = selected_real_kind(15, 307)
   !> Quadruple precision real numbers, 33 digits, range 10⁻⁴⁹³¹ to 10⁴⁹³¹-1; 128 bits
   integer, parameter :: qp = selected_real_kind(33, 4931)

   !> Char length for integers, range -2⁷ to 2⁷-1; 8 bits
   integer, parameter :: i1 = selected_int_kind(2)
   !> Short length for integers, range -2¹⁵ to 2¹⁵-1; 16 bits
   integer, parameter :: i2 = selected_int_kind(4)
   !> Length of default integers, range -2³¹ to 2³¹-1; 32 bits
   integer, parameter :: i4 = selected_int_kind(9)
   !> Long length for integers, range -2⁶³ to 2⁶³-1; 64 bits
   integer, parameter :: i8 = selected_int_kind(18)

end module kind_parameter
```

Floating point constants should always be declared including a kind parameter suffix:

```fortran
real(dp) :: a, b, c
a = 1.0_dp
b = 3.5_dp
c = 1.34e8_dp
```

It is safe to assign integers to floating point numbers without losing accuracy:

```fortran
real(dp) :: a
a = 3
```

In order to impose floating point division (as opposed to integer
division `1/2` equal to `0`), one can convert the integer to a floating
point number by:

```fortran
real(dp) :: a
a = real(1, dp) / 2  ! 'a' is equal to 0.5_dp
```

To print floating point numbers without losing precision use the unlimited
format specificer ``(g0)`` or the exponential representation ``(es24.16e3)``,
which will give you 17 significant digits of printout.
