# Introduction

## ARPACK (ARnoldi PACKage)

**ARPACK** is a collection of Fortran77 subroutines designed to solve large 
scale eigenvalue problems. 

The package is designed to compute a few eigenvalues and corresponding 
eigenvectors of a general n by n matrix **A**. It is most appropriate for 
large sparse or structured matrices **A** where structured means that a 
matrix-vector product **w <- Av** requires order n rather than the usual 
order **n^2** floating point operations. This software is based upon an 
algorithmic variant of the Arnoldi process called the Implicitly Restarted 
Arnoldi Method (**IRAM**). When the matrix A is symmetric, it reduces
to a variant of the Lanczos process called the Implicitly Restarted Lanczos 
Method (**IRLM**). These variants may be viewed as a synthesis of the 
Arnoldi/Lanczos process with the Implicitly Shifted QR technique 
suitable for large-scale problems. For many standard problems, a matrix
factorization is not required. Only the action of the matrix on a vector is 
needed. 

**ARPACK** software can solve large-scale symmetric, nonsymmetric,
and generalized eigenproblems in significant application areas. The software 
is designed to compute a few (**k**) eigenvalues with user-specified features such 
as those of the largest real part or largest magnitude.  Storage requirements are 
on the order of n*k locations. No auxiliary storage is required. A set of
Schur basis vectors for the desired **k**-dimensional eigen-space is computed, which 
is numerically orthogonal to working precision. Numerically accurate eigenvectors 
are available on request. 

## Important Features: 

   -    Reverse Communication Interface. 

   -    Single and Double-precision Precision Real Arithmetic Versions for 
        Symmetric, Non-symmetric, Standard or Generalized Problems. 

   -    Single and Double Precision Complex Arithmetic Versions for 
        Standard or Generalized Problems. 

   -    Routines for Banded Matrices - Standard or Generalized Problems. 

   -    Routines for The Singular Value Decomposition. 

   -    Example driver routines that may be used as templates to implement 
        numerous Shift-Invert strategies for all problem types, data types 
        and precision. 

## PARPACK (Parallel ARPACK)

**PARPACK** is an extension of the **ARPACK** software package used for solving
large-scale eigenvalue problems on distributed memory parallel architectures.
The message-passing layers currently supported are **BLACS** and **MPI**.

### Routines Available: 

   - All core **ARPACK** routines for single, double, complex, and complex16.
   - A small number of example drivers.

## Instructions

- Upon executing **ls** command, you should see

      BLAS
      DOCUMENTS
      EXAMPLES
      LAPACK
      README
      SRC
      UTIL
      Makefile
      ARmake.inc
      ARMAKES
      PARPACK

   The following entries are directories:
```
      ARMAKES, BLAS, DOCUMENTS, EXAMPLES, LAPACK, SRC, UTIL, PARPACK
```
   The directory **SRC** contains the top-level routines, including the highest-level reverse
   communication interface routines
```
      ssaupd, dsaupd - symmetric single and double precision
      snaupd, dnaupd - non-symmetric single and double precision
      cnaupd, znaupd - complex non-symmetric single and double precision
```
   The headers of these routines contain full documentation of calling
   sequence and usage.  Additional information is in the **DOCUMENTS** directory.

   The directory **PARPACK** contains the Parallel **ARPACK** routines.
     
- Example driver programs that illustrate all the computational modes,
   data types and precisions may be found in the **EXAMPLES** directory.
   Upon executing the **`ls EXAMPLES`** command, you should see
```
      BAND
      COMPLEX
      NONSYM
      README
      SIMPLE
      SVD
      SYM
```
   Example programs for banded, complex, nonsymmetric, symmetric,
   and singular value decomposition may be found in the directories
   **BAND**, **COMPLEX**, **NONSYM**, **SYM**, **SVD** respectively.
   To get started, get into the **SIMPLE**
   directory to see example programs that illustrate the use of **ARPACK** in
   the simplest modes of operation for the most commonly posed 
   standard eigenvalue problems.  


   Example programs for Parallel **ARPACK** may be found in the directory
   **PARPACK/EXAMPLES**.

   The following instructions explain how to make the **ARPACK** library.

- Before you can compile anything, you must first edit and correct the file
   ARmake.inc. Sample **ARmake.inc**'s can be found in the **ARMAKES** directory.
   If you plan on using Parallel **ARPACK**, you will need to use those sample
   files that contain either **BLACS** or **MPI** in their name. For example,
   **`ARmake.MPI-$(PLAT)`** or **`ARmake.BLACS-$(PLAT)`**.
   Edit "ARmake.inc" and change the definition "home" to the root of the
   source tree (Top level of **ARPACK** directory)

   The makefile is set up to build a self-contained library that includes
   the needed **BLAS** 1/2/3 and **LAPACK** routines.  If you already have the
   **BLAS** and **LAPACK** libraries installed on your system, you might want to
   change the definition of DIRS as indicated in the ARmake.inc file. 

   **`NOTE:`** Unless the **LAPACK** library on your system is version 2.0,
   we strongly recommend that you install the **LAPACK** routines provided with
   **ARPACK**. Note that the current **LAPACK** release is version 3.0; if you are 
   not sure which version of **LAPACK** is installed, please compile and link 
   to the subset of **LAPACK** included with **ARPACK**. 

- You will also need to change the file "second.f" in the UTIL directory
   to whatever is appropriate for timing on your system.  The "second" routine
   provided works on most workstations.  If running on a Cray,
   copy the file **second.f.CRAYT3D** to **second.f** to use the **rtf** system 
   function. 

- Do **`make lib`** in the current directory to build the standard library 
  **`libarpack_$(PLAT).a`** (serial code)
 
   To build the parallel library, **`parpack_$(COMMLIB)-$(PLAT).a`**,
   type **`make plib`**. When using the parallel routines, you must link to 
   both the serial and parallel libraries.


- Within the **DOCUMENTS** directory there are three files 
```
   ex-sym.doc 
   ex-nonsym.doc and
   ex-complex.doc
```
   For templates on how to invoke the computational modes of **ARPACK**.
```
   Danny Sorensen   at  sorensen@caam.rice.edu
   Richard Lehoucq  at  rblehou@sandia.gov
   Chao Yang        at  cyang@lbl.gov
   Kristi Maschhoff at  kristyn@tera.com
```
 Good luck and enjoy.
