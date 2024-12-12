Platform: x86_64-pc-linux-musl
OS: Alpine Linux v3.20

R was configured with the following options:

--with-internal-tzcode
--enable-lto=R
--with-blas=openblas

-D_FORTIFY_SOURCE=2 is used by default on Alpine

-D__MUSL__ was added to CXXFLAGS as this is currently needed for Rcpp
(it is also set by R from the Alpine Linux package repository).

See 'world' in this directory for the list of installed Alpine packages.

Additionally, the following software was manually installed:
- JAGS 4.3.2 <https://mcmc-jags.sourceforge.io/>
- BWidget 1.10.1 <https://wiki.tcl-lang.org/page/BWidget>
