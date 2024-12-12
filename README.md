This repository is currently used to share installation or check issues
of R packages on Alpine Linux, which uses [musl](https://musl.libc.org/)
instead of [glibc](https://www.gnu.org/software/libc/). Portable code will
work with both. Some functional differences between the two are listed on
[musl's community wiki](https://wiki.musl-libc.org/functional-differences-from-glibc).

These routine checks use a nightly build of
[R-patched](https://CRAN.R-project.org/src/base-prerelease/)
to install/update all available CRAN packages
as well as required or suggested packages from Bioconductor.

Issues are *force-pushed* to the [**results branch**](tree/results/musl).


## TODO

- Exercise the packages, i.e., run something like `R CMD check --extra-arch`.

- Document the setup, ideally by providing a Docker image that mirrors
  the server on which these checks run.
  In the meantime, the Alpine-based Docker images maintained at
  [`rhub/r-minimal`](https://github.com/r-hub/r-minimal)
  should usually reproduce the compilation issues reported here.


## Background

I have been (re-)checking a fixed (irregularly updated) subset of ~6000
CRAN/BIOC packages specifically to test R patches since mid-2021,
experimenting with Alpine Linux as a not-yet-tested but sufficiently
relevant platform with some open issues on R's Bugzilla at the time.
In December 2022, I started reporting installation/check problems to
individual package maintainers.
I have now added a separate, routine check service that covers (almost)
all of CRAN so maintainers can be informed about non-portable code in
their packages.
