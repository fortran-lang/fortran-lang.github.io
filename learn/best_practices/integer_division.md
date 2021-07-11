---
layout: book
title: Integer Division
permalink: /learn/best_practices/integer_division
---

Fortran distinguishs between floating point and integer arithmetic.
It is important to note that division for integers is always using
integer arithmetic.
Consider the following example for integer division of an odd number:

```fortran
integer :: n
n = 3
print *, n / 2  ! prints 1
print *, n*(n + 1)/2  ! prints 6
print *, n/2*(n + 1)  ! prints 4
n = -3
print *, n / 2  ! prints -1
```

Be careful about whether you want to actually use integer arithmetic
in this context. If you want to use floating point arithmetic instead
make sure to cast to reals before using the division operator:

```fortran
integer :: n
n = 3
print *, real(n, dp) / 2  ! prints 1.5
n = -3
print *, real(n, dp) / 2  ! prints -1.5
```
