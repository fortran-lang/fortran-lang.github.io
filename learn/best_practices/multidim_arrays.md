---
layout: book
title: Multidimensional Arrays
permalink: /learn/best_practices/multidim_arrays
---

Multidimensional arrays are stored in column-major order. This means the
left-most (inner-most) index addresses elements contiguously.
From a practical point this means that the array slice ``V(:, 1)`` is
contiguous, while the stride between elements in the slice ``V(1, :)``
is the dimension of the columns. This is important when passing array
slices to procedures which expect to work on contiguous data.

The locality of the memory is important to consider depending on
your application, usually when performing operations on a multidimensional
the sequential access should always advance in unity strides.

In the following example the inverse distance between two sets of points
is evaluated, note that the points are stored contiguously in the arrays
``xyz1``/``xyz2``, while the inner-most loop is advancing the left-most
index of the matrix ``a``.

```fortran
subroutine coulomb_matrix(xyz1, xyz2, a)
  real(dp), intent(in) :: xyz1(:, :)
  real(dp), intent(in) :: xyz2(:, :)
  real(dp), intent(out) :: a(:, :)
  integer :: i, j
  do i = 1, size(a, 2)
    do j = 1, size(a, 1)
      a(j, i) = 1.0_dp/norm2(xyz1(:, j) - xyz2(:, i))
    end do
  end do
end subroutine coulomb_matrix
```

Another example would be the contraction of the third dimension of a rank
three array:

```fortran
do i = 1, size(amat, 3)
  do j = 1, size(amat, 2)
    do k = 1, size(amat, 1)
      cmat(k, j) = cmat(k, j) + amat(k, j, i) * bvec(i)
    end do
  end do
end do
```

Contiguous array slices can be used in array-bound remapping to allow usage
of higher rank arrays as lower rank arrays without requiring to reshape
and potentially create a temporary copy of the array.

For example this can be used to contract the third dimension of a rank
three array using a matrix-vector operation:

```fortran
subroutine matmul312(amat, bvec, cmat)
  real(dp), contiguous, intent(in) :: amat(:, :, :)
  real(dp), intent(in) :: bvec(:)
  real(dp), contiguous, intent(out) :: cmat(:, :)
  real(dp), pointer :: aptr(:, :)
  real(dp), pointer :: cptr(:)

  aptr(1:size(amat, 1)*size(amat, 2), 1:size(amat, 3)) => amat
  cptr(1:size(cmat)) => cmat

  cptr = matmul(aptr, bvec)
end subroutine matmul312
```
