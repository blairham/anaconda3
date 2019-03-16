#########################################################################
FROM alpine
MAINTAINER Blair Hamilton <blairham@wickedcode.io>

RUN set -eux \
  ; apk update \
  ; apk add --no-cache bash \
  ; apk add --no-cache zsh \
  ; apk add --no-cache ca-certificates wget \
# install glibc
  ; wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
  ; wget -q https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk \
  ; wget -q https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-bin-2.28-r0.apk \
  ; wget -q https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-i18n-2.28-r0.apk \
  ; apk add --no-cache glibc-2.28-r0.apk \
  ; apk add --no-cache glibc-bin-2.28-r0.apk \
  ; apk add --no-cache glibc-i18n-2.28-r0.apk \
  ; /usr/glibc-compat/bin/localedef --force --inputfile POSIX --charmap UTF-8 C.UTF-8 || true \
  ; echo "export LANG=C.UTF-8" > /etc/profile.d/locale.sh \
  ; rm glibc*.apk \
# install miniconda
  ; wget -q -O miniconda.sh https://repo.anaconda.com/miniconda/Miniconda3-4.5.4-Linux-x86_64.sh \
  ; /bin/bash miniconda.sh -b -p /opt/conda \
  ; rm miniconda.sh \
# configure anaconda
  ; ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh \
  ; echo ". /opt/conda/etc/profile.d/conda.sh" | tee -a ~/.bashrc

# add conda to path
ENV PATH=$PATH:/opt/conda:/opt/conda/bin \
    LANG=C.UTF-8
