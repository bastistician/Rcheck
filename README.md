This is a preliminary repository used to share **installation issues**
of R packages on Alpine Linux, which uses [musl](https://musl.libc.org/)
instead of [glibc](https://www.gnu.org/software/libc/). Portable code will
work with both. Some functional differences between the two are listed on
[musl's community wiki](https://wiki.musl-libc.org/functional-differences-from-glibc).

A nightly cron job builds
[R-patched](https://CRAN.R-project.org/src/base-prerelease/)
and installs/updates (almost) **all available CRAN packages**
as well as required or suggested packages from Bioconductor.

Installation issues are *force-pushed* to the
[**results branch**](../../tree/results/musl).
Results may be published elsewhere in the future.


## Background

I have been (re-)checking a fixed (irregularly updated) subset of
~6000 CRAN/BIOC packages specifically to test R patches since mid-2021,
experimenting with Alpine Linux as a not-yet-tested but sufficiently
relevant platform with some open issues on R's Bugzilla at the time.
In December 2022, I started reporting installation/check problems to
individual package maintainers.
This repository now gathers issues found from a routine check system
that covers (almost) all of CRAN, so maintainers can be informed about
non-portable code in their packages.
