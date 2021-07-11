---
layout: book
title: File Input/Output
permalink: /learn/best_practices/file_io
---

In Fortran files are managed by unit identifiers. Interaction with the filesystem
mainly happens through the ``open`` and ``inquire`` built-in procedures.
Generally, the workflow is to open a file to a unit identifier, read and/or write
to it and close it again.

```fortran
integer :: io
open(newunit=io, file="log.txt")
! ...
close(io)
```

By default the file will be created if it is not existing already and opened for
both reading and writing. Writing to an existing file will start in the first
record (line) and therefore overwrite the file by default.

To create a read-only access to a file the ``status`` and ``action`` have to be
specified with

```fortran
integer :: io
open(newunit=io, file="log.txt", status="old", action="read")
read(io, *) a, b
close(io)
```

In case the file is not present a runtime error will occur. To check for the existence
of a file prior to opening it the ``inquire`` function can be used

```fortran
logical :: exists
inquire(file="log.txt", exist=exists)
if (exists) then
  ! ...
end if
```

Alternatively, the ``open`` procedure can return an optional *iostat* and *iomsg*:

```fortran
integer :: io, stat
character(len=512) :: msg
open(newunit=io, file="log.txt", status="old", action="read", &
  iostat=stat, iomsg=msg)
if (stat /= 0) then
  print *, trim(msg)
end if
```

Note that *iomsg* requires a fixed-length character variable with sufficent storage
size to hold the error message.

Similarly, writing to a file happens by using the *status* and *action* keyword.
To create a new file use

```fortran
integer :: io
open(newunit=io, file="log.txt", status="new", action="write")
write(io, *) a, b
close(io)
```

Alternatively, ``status="replace"`` can be used to overwrite an existing file,
it is highly recommended to first check for the existence of a file before deciding
on the *status* to use.
To append to an output file the *position* keyword can be specified explicitly with

```fortran
integer :: io
open(newunit=io, file="log.txt", position="append", &
  & status="old", action="write")
write(io, *) size(v)
write(io, *) v(:)
close(io)
```

To reset the position in a file the built-in procedures ``rewind`` and ``backspace``
can be used. ``rewind`` will reset to the first record (line), while ``backspace`` will
return to the previous record (line).

Finally, to delete a file the file has to be opened and can be deleted after closing
with

```fortran
logical :: exists
integer :: io, stat
inquire(file="log.txt", exist=exists)
if (exists) then
  open(file="log.txt", newunit=io, iostat=stat)
  if (stat == 0) close(io, status="delete", iostat=stat)
end if
```

A useful IO feature are scratch files, which can be opened with ``status="scratch"``.
They are automatically deleted after closing the unit identifier.
