FROM alpine:3.22

LABEL org.opencontainers.image.title="Large Alpine Linux system for checking R packages under musl"
LABEL org.opencontainers.image.authors="Sebastian Meyer <seb.meyer@fau.de>"

ENV TZ=Europe/Berlin

## restore full set of Alpine packages as used on the server
COPY world /etc/apk/world
RUN apk fix --no-cache

## download and build R
## the actual check system uses R-patched (potentially R-beta or R-rc)
#ADD https://CRAN.R-project.org/src/base-prerelease/R-patched.tar.xz /R.tar.xz
## but here we use R-release so the image does not need to be updated too often
ADD https://CRAN.R-project.org/src/base/R-latest.tar.xz /R.tar.xz
WORKDIR /R
RUN tar x -J -f /R.tar.xz --strip-components=1 && rm /R.tar.xz
COPY config.site .
RUN ./configure && make

## set a default CRAN mirror for convenience
RUN sed -i -e 's|@CRAN@|https://cloud.R-project.org|' etc/repositories

## add this R to the PATH, masking the system R
RUN ln -s /R/bin/R /usr/local/bin/R

WORKDIR /
CMD ["R"]
