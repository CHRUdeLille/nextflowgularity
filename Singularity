# =====================================
# HEADER
# =====================================
Bootstrap: docker
From: nextflow/nextflow:0.29.1

%labels
  MAINTAINER christophe.demay@chru-lille.fr
  CONTAINER_VERSION 0.0.1
  SINGULARITY_VERSION 2.5.1
  NEXTFLOW_VERSION 0.29.1

%setup

%files

%environment
  NXF_OPTS='-XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap' 
  NXF_HOME=/.nextflow
  
%help

%post
  # =====================================
  # INSTALL DEPENDENCIES
  # =====================================
  apk update && apk upgrade 
  apk add --no-cache coreutils 
  apk add --no-cache curl bash 
  apk add --no-cache wget 
  apk add --no-cache build-base 
  apk add --no-cache python
  apk add --no-cache --upgrade tar
  apk add --no-cache linux-headers
  apk add --no-cache libarchive-dev
  apk add --no-cache squashfs-tools
  apk add --no-cache sudo
  
  
  # =====================================
  # INSTALL SINGULARITY
  # =====================================

  mkdir -p /opt/singularity && cd /opt/singularity

  SINGULARITY_VERSION=2.5.1
  wget https://github.com/singularityware/singularity/releases/download/$SINGULARITY_VERSION/singularity-$SINGULARITY_VERSION.tar.gz
  tar xvf singularity-$SINGULARITY_VERSION.tar.gz
  cd singularity-$SINGULARITY_VERSION
  ./configure --prefix=/usr/local
  make
  sudo make install
   