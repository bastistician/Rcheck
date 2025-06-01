FROM alpine:3.22

MAINTAINER "Sebastian Meyer" seb.meyer@fau.de

ENV TZ=Europe/Berlin

## restore full set of Alpine packages as used on the server
COPY world /etc/apk/world
RUN apk fix --no-cache

## download and build R-patched
WORKDIR /opt/R
RUN wget -q -O - https://CRAN.R-project.org/src/base-prerelease/R-patched.tar.xz | \
        tar x -J -f - --strip-components=1
COPY config.site .
RUN ./configure && make
RUN ln -s /opt/R/bin/R /usr/local/bin/R

WORKDIR /
CMD ["R"]
