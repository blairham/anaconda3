#########################################################################
FROM centos
MAINTAINER Blair Hamilton <blairham@wickedcode.io>

RUN set -eux \
  ; yum -y install zsh \
  ; yum -y install bzip2 \
  ; yum -y install wget \
  ; yum clean all && rm -rf /var/cache/yum \
# install miniconda
  ; wget -q -O miniconda.sh https://repo.anaconda.com/miniconda/Miniconda3-4.5.4-Linux-x86_64.sh \
  ; /bin/bash miniconda.sh -b -p /opt/conda \
  ; rm miniconda.sh \
# configure anaconda
  ; ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh \
  ; echo "conda activate base" | tee -a ~/.bashrc ~/.zshrc

# add conda to path
ENV PATH=$PATH:/opt/conda:/opt/conda/bin \
    LANG=C.UTF-8
