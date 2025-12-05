Outputs of failed R package installations on a Linux system
using musl instead of glibc and BusyBox instead of GNU coreutils.

R version: nightly R-patched snapshot from CRAN/src/base-prerelease
Platform: x86_64-pc-linux-musl
OS: Alpine Linux v3.22
Locale: C.UTF-8
TZ: Europe/Berlin

See sub-directory 'config' for more details, including:
- 'config.site' for compiler flags and configuration variables
- 'world' for the list of installed Alpine packages
A simple Dockerfile is also provided.  It uses these files to build an R
environment that mimics the server's setup.  Note that the image will be
very large (> 4 GB) as it fulfils the system requirements of almost all
CRAN packages.  To reproduce an issue for a specific R package, it may
be more convenient and sufficient to use the standard 'alpine' Docker
image (`docker pull alpine`) with a released version of R from Alpine's
repositories (`apk add R R-dev R-doc`).

The following additional software was manually installed from source
(and is currently not reproduced in the Dockerfile):
- JAGS 4.3.2 <https://mcmc-jags.sourceforge.io/>
- BWidget 1.10.1 <https://wiki.tcl-lang.org/page/BWidget>
- COIN-OR SYMPHONY 5.7.2 <https://github.com/coin-or/SYMPHONY>
