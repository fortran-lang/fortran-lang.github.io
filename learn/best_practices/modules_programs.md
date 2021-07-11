---
layout: book
title: Modules and Programs
permalink: /learn/best_practices/modules_programs
---

Modules are the preferred way create modern Fortran libraries and applications.
As a convention, one source file should always contain only one module, while
the module name should match the filepath to allow easy navigation in larger
projects. It is also recommended to prefix module names with the library name
to avoid nameclashes when used as dependency in other projects.

An example for such a module file is given here

```
!> Interface to TOML processing library.
!>
!> ...
module fpm_toml
  use fpm_error, only : error_t, fatal_error, file_not_found_error
  use fpm_strings, only : string_t
  use tomlf, only : toml_table, toml_array, toml_key, toml_stat, get_value, &
    & set_value, toml_parse, toml_error, new_table, add_table, add_array, &
    & toml_serializer, len
  implicit none
  private

  public :: read_package_file
  public :: toml_table, toml_array, toml_key, toml_stat, get_value, set_value
  public :: new_table, add_table, add_array, len
  public :: toml_error, toml_serializer, toml_parse

contains

  !> Process the configuration file to a TOML data structure
  subroutine read_package_file(table, manifest, error)
    !> TOML data structure
    type(toml_table), allocatable, intent(out) :: table
    !> Name of the package configuration file
    character(len=*), intent(in) :: manifest
    !> Error status of the operation
    type(error_t), allocatable, intent(out) :: error
    ! ...
  end subroutine read_package_file

end module fpm_toml
```

There are a few things in this example module to highlight. First, every module
starts with comments documenting the purpose and content of the module,
similarly, every procedure starts with a comment briefly describing its
purse and the intent of the dummy arguments. Documentation is one of the most
important parts of creating long-living software, regardless of language.

Second, imports (*use*) and exports (*public*) are explicitly given, this
allows on a glance at the module source to check the used and available
procedures, constants and derived types. The imports are usually limited
to the module scope rather than reimported in every procedure or interface
scope. Similarly, exports are made explicitly by adding a *private* statement
one a single line and explicitly listing all exported symbols in *public*
statements.

Finally, the `implicit none` statement works for the whole module and there
is no need to repeat it within each procedure.

Variables inside a module are static (*implicitly saved*), it is highly
recommended to limit the usage of module variables to constant expressions,
like parameters or enumerators only or export them as *protected* rather
than *public*.

Submodules can be used to break long dependency chains and shorten recompilation
cascades in Fortran programs. They also offer the possibility to provide specialized
and optimized implementations without requiring the use of preprocessor.

An example from the Fortran standard library is the quadrature module, which
only defines interfaces to module procedures, but no implementations

```fortran
!> Numerical integration
!>
!> ...
module stdlib_quadrature
  use stdlib_kinds, only: sp, dp, qp
  implicit none
  private

  public :: trapz
  ! ...

  !> Integrates sampled values using trapezoidal rule
  interface trapz
    pure module function trapz_dx_dp(y, dx) result(integral)
      real(dp), intent(in) :: y(:)
      real(dp), intent(in) :: dx
      real(dp) :: integral
    end function trapz_dx_dp
    module function trapz_x_dp(y, x) result(integral)
      real(dp), intent(in) :: y(:)
      real(dp), intent(in) :: x(:)
      real(dp) :: integral
    end function trapz_x_dp
  end interface trapz

  ! ...
end module stdlib_quadrature
```

While the implementation is provided in separate submodules like the one for the
trapezoidal integration rule given here.

```fortran
!> Actual implementation of the trapezoidal integration rule
!>
!> ...
submodule (stdlib_quadrature) stdlib_quadrature_trapz
  use stdlib_error, only: check
  implicit none

contains

  pure module function trapz_dx_dp(y, dx) result(integral)
    real(dp), intent(in) :: y(:)
    real(dp), intent(in) :: dx
    real(dp) :: integral
    integer :: n

    n = size(y)
    select case (n)
    case (0:1)
      integral = 0.0_dp
    case (2)
      integral = 0.5_dp*dx*(y(1) + y(2))
    case default
      integral = dx*(sum(y(2:n-1)) + 0.5_dp*(y(1) + y(n)))
    end select
  end function trapz_dx_dp

  ! ...
end submodule stdlib_quadrature_trapz
```

Note that the module procedures do not have to be implemented in the same submodule.
Several submodules can be used to reduce the compilation load for huge modules.

Finally, when setting up a program, it is recommended to keep the actual implementations
in the program body at minimum. Reusing implementations from modules allows to write
reusable code and focus in the program unit only on translating user input to the
respective library functions and objects.
