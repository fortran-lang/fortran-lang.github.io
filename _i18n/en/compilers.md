Fortran has over a dozen open source and commercial compilers.

## Open source compilers

### GNU Fortran Compiler

[GNU Fortran Compiler (gfortran)](https://gcc.gnu.org/fortran/) is a mature
free and open source compiler, part of the GNU Compiler Collection.

[OpenCoarrays](http://www.opencoarrays.org/) is a library and compiler wrapper
around gfortran which enables the parallel programming features of Fortran 2018
with gfortran.


### LLVM Flang

[Flang](https://github.com/llvm/llvm-project/tree/main/flang)
is a new front-end for Fortran 2018 that has been recently
added to LLVM.
It is implemented in modern C++ and uses a Fortran-oriented MLIR dialect for lowering to LLVM IR.
This project is under active development.


### Current Flang

[Flang](https://github.com/flang-compiler/flang) is an open source compiler 
based on the NVIDIA/PGI commercial compiler.


### LFortran

[LFortran](https://lfortran.org) is a modern, interactive, LLVM-based Fortran
compiler.


## Commercial compilers

### Intel

[Intel oneAPI](https://software.intel.com/content/www/us/en/develop/tools/oneapi/all-toolkits.html)
is Intel's suite of compilers, tools, and libraries for Fortran, C, C++, and
Python. Intel oneAPI HPC Toolkit provides
[two Fortran compilers](https://software.intel.com/content/www/us/en/develop/articles/intel-oneapi-fortran-compiler-release-notes.html):
* Intel Fortran Compiler Classic (`ifort`), a mature compiler
  with full Fortran 2018 support; and
* Intel Fortran Compiler Beta (`ifx`), a new, LLVM-based compiler
  that supports Fortran 95 and partially newer versions of the standard.

Intel oneAPI is available for free.

### NAG

The latest [NAG Fortran Compiler](https://www.nag.com/nag-compiler)
release (7.0) has extensive support for legacy and modern Fortran features including parallel programming with coarrays, as well as additional support for programming with OpenMP.

The Compiler also provides significant support for Fortran 2018 (atomic
operations, events and tasks, plus other smaller features), almost all of
Fortran 2008, complete coverage of Fortran 2003, and all of OpenMP 3.1. All
platforms include supporting tools for software development: source file
polishers, dependency generator for module and include files, call-graph
generator, interface builder and a precision unifier.

### NVIDIA

The [NVIDIA HPC SDK](https://developer.nvidia.com/hpc-sdk) C, C++, and Fortran compilers, former [PGI compilers](https://www.pgroup.com/products/index.htm), support GPU acceleration of HPC modeling and simulation applications with standard C++ and Fortran, OpenACC® directives, and CUDA®. GPU-accelerated math libraries maximize performance on common HPC algorithms, and optimized communications libraries enable standards-based multi-GPU and scalable systems programming.

### HPE / Cray

The [Cray Compiling Environment (CCE)](https://www.cray.com/sites/default/files/SB-Cray-Programming-Environment.pdf)
is the cornerstone innovation of Cray's adaptive computing paradigm. CCE builds
on a well-developed and sophisticated Cray technology base that identifies
regions of computation that are either sequential scalar, vector parallel or
highly multithreaded. It includes optimizing compilers that automatically
exploit the scalar, vector and multithreading hardware capabilities of the Cray
system. CCE supports Fortran, C and C++.

### IBM

[IBM® XL Fortran](https://www.ibm.com/us-en/marketplace/xl-fortran-linux-compiler-power)
for Linux is an industry standards-based programming tool used to develop large
and complex applications in the Fortran programming language. It generates code
that leverages the capabilities of the latest POWER9 architecture and maximizes
your hardware utilization. IBM XL Fortran for Linux optimizes your
infrastructure on IBM Power Systems™ in support of extensive numerical,
scientific and high-performance computing.

### AMD

The [AMD Optimizing C/C++ Compiler (AOCC)](https://developer.amd.com/amd-aocc/)
compiler system is a high performance, production quality code generation tool.
The AOCC environment provides various options to developers when building and
optimizing C, C++, and Fortran applications targeting 32-bit and 64-bit Linux®
platforms. The AOCC compiler system offers a high level of advanced
optimizations, multi-threading and processor support that includes global
optimization, vectorization, inter-procedural analyses, loop transformations,
and code generation. AMD also provides highly optimized libraries, which extract
the optimal performance from each x86 processor core when utilized. The AOCC
Compiler Suite simplifies and accelerates development and tuning for x86
applications.


### ARM

[Linux user-space Fortran compiler](https://developer.arm.com/tools-and-software/server-and-hpc/compile/arm-compiler-for-linux/arm-fortran-compiler).
Tailored for HPC and scientific codes, with support for popular Fortran and
OpenMP standards and tuned for leading server-class Arm-based platforms. Built
on the open source Flang front-end, and the LLVM‑based optimization and code
generation back-end. Available as part of the Arm Compiler for Linux package.


### Absoft

[Our compilers](https://www.absoft.com/products/) build faster code more
efficiently than ever before. Pro Fortran delivers Absoft’s exclusive AP load
balancing (offering an increase in performance of up to 20%!), AVX, OpenMP 3.1,
highly extended Fortran 95 compiler with F2003 and F2008 features,, FX3
graphical debugger, native tool suite integration, AMDAL HPC scientific and
engineering library, and much more. Plus, Pro Fortran is the only compiler with
Fast Data Visualization, an Absoft exclusive technology for graphical rendering
and data output.


### Oracle / Sun

[Oracle C, C++, Fortran Compiler](https://www.oracle.com/application-development/technologies/developerstudio-features.html)
is highly optimized for Oracle systems, on-premise and in the cloud

* Advanced code generation technology for the latest Oracle SPARC and x86 based systems
* Support for the latest industry standards, including C++14, C++11, C11 and OpenMP 4.0 and extensive GCC compatibility features
* Automatic code analysis during compilation and automatic stack overflow protection at application runtime


### Lahey / Fujitsu

Combining the 32/64-bit LGF Rainier compiler with the classic [Lahey/Fujitsu
LF95](https://lahey.com/) compiler, LF Professional v7.8 delivers! LGF Rainier
has full Fortran 95/90/77 compliance with extensive support for the Fortran 2003
and 2008 standards. Lahey/Fujitsu LF95 offers best in class diagnostics.
Includes the automatic-parallelizing GFortran compiler, Lahey/Fujitsu Fortran 95
compiler, Visual Studio 2015 Shell (compatible with VS2017), Lahey's Exclusive
Visual Studio Fortran support, Winteracter WiSK Graphics package, and more!


### Silverfrost FTN95

[Silverfrost FTN95](https://www.silverfrost.com/) is a full Fortran 95 standards
compliant compiler, capable of producing fast executables for Win32 and for
Microsoft .NET. FTN95 ships with the world's best runtime checking and a great
range of supporting software. All standard and many vendor-specific legacy
language features are supported, so that Fortran projects may be any combination
of Fortran 77, Fortran 90 and Fortran 95.


### NEC

[The Fortran compiler](https://www.nec.com/en/global/solutions/hpc/sx/tools.html)
conforms to the Fortran-2003 standard (ISO/IEC 1539-1:2004) and supports many
features from Fortran-2008 (ISO/IEC 1539-1:2010).


## Discontinued

The following is a list of Fortran compilers that seem discontinued, so we do
not list them above:

* Hewlett Packard
* Watcom
* PathScale
* G95
* Open64
* Unisys


## Note

Please let us know if there is any compiler that is not listed, or if we listed
a compiler in the Discontinued section and it is in fact actively maintained.
