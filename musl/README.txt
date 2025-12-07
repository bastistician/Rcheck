Testing R package installations on a Linux system
with musl instead of glibc and BusyBox instead of GNU coreutils.

R version: nightly R-patched snapshot from CRAN/src/base-prerelease
Platform: x86_64-pc-linux-musl
OS: Alpine Linux v3.22
Locale: C.UTF-8
TZ: Europe/Berlin

See sub-directory 'config' for more details, including:

- 'config.site' for compiler flags and configuration variables
- 'world' for the list of installed Alpine packages

A Docker image built from that configuration with the latest R release
is available via

    docker pull ghcr.io/bastistician/rcheckserver:latest

but note that this image is very large (> 4 GB) as it fulfils the system
requirements of almost all CRAN packages.  To reproduce an issue for a
specific R package, it is more efficient and often sufficient to use the
standard Alpine Linux image.  Interactively:

    docker pull alpine
    docker run --rm -it alpine

Install R from Alpine and only the required system dependencies for the
R package at hand, for example:

    apk add R R-dev R-doc
    apk add g++ libxml2-dev  # for Rcpp, xml2 et al.
    R -s -e 'install.packages("PKGNAME", repos = "https://cloud.R-project.org")'

Some R packages require additional software that is not available from
the regular Alpine Linux package repositories.  On the check system,
the following software is manually installed from source:

- JAGS 4.3.2 <https://mcmc-jags.sourceforge.io/>
- BWidget 1.10.1 <https://wiki.tcl-lang.org/page/BWidget>
- COIN-OR SYMPHONY 5.7.2 <https://github.com/coin-or/SYMPHONY>
