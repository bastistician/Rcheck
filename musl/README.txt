Outputs of failed R package installations on a Linux system
using musl instead of glibc and BusyBox instead of GNU coreutils.

R version: nightly R-patched snapshot from CRAN/src/base-prerelease
Platform: x86_64-pc-linux-musl
OS: Alpine Linux v3.21
Locale: C.UTF-8
TZ: Europe/Berlin

R was configured with options

--with-internal-tzcode
--enable-lto=R
--with-blas=openblas
--with-lapack

See sub-directory 'config' for more details, including:
- 'config.site' for compiler flags and other configuration variables
- 'world' for the list of installed Alpine packages
A simple Dockerfile is also provided.  It uses these files to build an R
environment that mimics the server's setup.  Note that the image will be
very large (> 6 GB) as it fulfils the system requirements of almost all
CRAN packages.  To reproduce an issue for a specific R package, it may be
more convenient to first try with a smaller Alpine-based Docker image,
for example from <https://github.com/r-hub/r-minimal>.

The following additional software was manually installed from source
(and is currently not reproduced in the Dockerfile):
- JAGS 4.3.2 <https://mcmc-jags.sourceforge.io/>
- BWidget 1.10.1 <https://wiki.tcl-lang.org/page/BWidget>
- COIN-OR SYMPHONY 5.7.2 <https://github.com/coin-or/SYMPHONY>
