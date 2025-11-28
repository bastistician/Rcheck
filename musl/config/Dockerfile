FROM alpine:3.22

MAINTAINER "Sebastian Meyer" seb.meyer@fau.de

ENV TZ=Europe/Berlin

## restore full set of Alpine packages as used on the server
COPY world /etc/apk/world
RUN apk fix --no-cache

## download and build nightly R-patched (potentially R-beta or R-rc)
ADD https://CRAN.R-project.org/src/base-prerelease/R-patched.tar.xz /R.tar.xz
WORKDIR /R
RUN tar x -J -f /R.tar.xz --strip-components=1 && rm /R.tar.xz
COPY config.site .
RUN ./configure && make
RUN ln -s /R/bin/R /usr/local/bin/R

WORKDIR /
CMD ["R"]
