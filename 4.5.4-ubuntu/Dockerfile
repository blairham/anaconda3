#########################################################################
FROM ubuntu
MAINTAINER Blair Hamilton <blairham@wickedcode.io>

RUN set -eux \
  ; apt-get update \
  ; apt-get -y install zsh \
  ; apt-get -y install wget \
  ; apt-get clean \
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
