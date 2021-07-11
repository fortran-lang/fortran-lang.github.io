---
layout: book
title: Allocatable Arrays
permalink: /learn/best_practices/allocatable_arrays
---

The ``allocatable`` attribute provides safe way for memory handling.
In comparison to variables with ``pointer`` attribute the memory is managed
automatically and will be deallocated automatically once the variable goes
out-of-scope. Using ``allocatable`` variables removes the possibility to
create memory leaks in an application.

They can be used in subroutines to create scratch or work arrays, where
automatic arrays would become too large to fit on the stack.

```fortran
real(dp), allocatable :: temp(:)
allocate(temp(10))
```

The allocation status can be checked using the ``allocated`` intrinsic
to avoid uninitialized access

```fortran
subroutine show_arr(arr)
  integer, allocatable, intent(in) :: arr(:)

  if (allocated(arr)) then
    print *, arr
  end if
end subroutine show_arr
```

To allocate variables inside a procedure the dummy argument has to carry
the ``allocatable`` attribute. Using it in combination with ``intent(out)``
will deallocate previous allocations before entering the procedure:

```fortran
subroutine foo(lam)
  real(dp), allocatable, intent(out) :: lam(:)
  allocate(lam(5))
end subroutine foo
```

The allocated array can be used afterwards like a normal array

```fortran
real(dp), allocatable :: lam(:)
call foo(lam)
```

An already allocated array cannot be allocated again without prior deallocation.
Similarly, deallocation can only be invoked for allocated arrays. To reallocate
an array use

```fortran
if (allocated(lam)) deallocate(lam)
allocate(lam(10))
```

Passing allocated arrays to procedures does not require the ``allocatable`` attribute
for the dummy arguments anymore.

```fortran
subroutine show_arr(arr)
  integer, intent(in) :: arr(:)

  print *, arr
end subroutine show_arr

subroutine proc
  integer :: i
  integer, allocatable :: arr

  allocate(arr(5))

  do i = 1, size(arr)
    arr(i) = 2*i + 1
  end do
  call show_arr(arr)
end subroutine proc
```

Passing an unallocated array in this context will lead to an invalid memory access.
Allocatable arrays can be passed to ``optional`` dummy arguments, if they are unallocated
the argument will not be present. The ``allocatable`` attribute is not limited to
arrays and can also be associated with scalars, which can be useful in combination
with ``optional`` dummy arguments.

Allocations can be moved between different arrays with ``allocatable`` attribute
using the ``move_alloc`` intrinsic subroutine.

```fortran
subroutine resize(var, n)
  real(wp), allocatable, intent(inout) :: var(:)
  integer, intent(in), optional :: n
  integer :: this_size, new_size
  integer, parameter :: inital_size = 16

  if (allocated(var)) then
    this_size = size(var, 1)
    call move_alloc(var, tmp)
  else
    this_size = initial_size
  end if

  if (present(n)) then
    new_size = n
  else
    new_size = this_size + this_size/2 + 1
  end if

  allocate(var(new_size))

  if (allocated(tmp)) then
    this_size = min(size(tmp, 1), size(var, 1))
    var(:this_size) = tmp(:this_size)
  end if
end subroutine resize
```

Finally, allocations do not initialize the array, the content of the uninitialized
array is most likely just the bytes of whatever was previously at the respective address.
The allocation supports initialization using the source attribute:

```fortran
real(dp), allocatable :: arr(:)
allocate(arr(10), source=0.0_dp)
```

The ``source`` keyword supports scalar and array valued variables and constants.
