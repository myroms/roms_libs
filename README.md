<img width="688" alt="image" src="https://github.com/user-attachments/assets/2cc88204-6a8d-48e6-82b1-e21991a4d42c" />

# ROMS External Libraries

Depending on the **ROMS** configuration, several third-party
libraries are required for linking and compiling an
application.

For more information about the required third-party libraries and
downloading instructions, please visit:

https://www.myroms.org/wiki/External_Libraries

Only the slightly customized libraries are available in this repository. To
download, execute the following command:

``` git
git clone https://github.com/myroms/roms_libs.git
```
## ARPACK (ARnoldi PACKage)

Serial and parallel legacy libraries are used to solve
large eigenvalue problems using either the Implicitly
Restarted Arnoldi Method (**IRAM**) for sparse matrices or
the Lanczos algorithm for symmetric matrices. It includes
a subset of the **BLAS** and **LAPACK** libraries. Some of its
functions are used in **4D-Var** and the adjoint-based
stability analysis propagators.
