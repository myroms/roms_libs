# ROMS External Liabraries

Depending on the **ROMS** configuration, several third-party
libraries are required for linking and compiling an
application. 

## ARPACK (ARnoldi PACKage)

Serial and parallel legacy libraries applied to solve
large eigenvalue problems using either the Implicitly
Restarted Arnoldi Method (**IRAM**) for sparse matrices or
the Lanczos algorithm for symmetric matrices. It includes
a subset of the **BLAS** and **LAPACK** libraries. Some of its
functions are used in **4D-Var** and the adjoint-based
stability analysis propagators. 