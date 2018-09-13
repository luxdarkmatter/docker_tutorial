FROM centos:7.4.1708

RUN yum -y update && yum -y upgrade
RUN yum -y install git make cmake gcc-c++ gcc binutils \
libX11-devel libXpm-devel libXft-devel libXext-devel


RUN yum -y install gcc-gfortran openssl-devel pcre-devel \
mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel \
fftw-devel cfitsio-devel graphviz-devel \
avahi-compat-libdns_sd-devel libldap-dev python-devel \
libxml2-devel gsl-static wget

# The cmake that comes with centos 7.4 is too old for lzuser offline, so install a useable one
RUN mkdir downloads \
    && cd downloads \
    && CMAKE_DISTRO=/usr/local/distros/cmake \
    && mkdir -p ${CMAKE_DISTRO} \
    && wget https://cmake.org/files/v3.12/cmake-3.12.2-Linux-x86_64.sh \
    && /bin/sh cmake-3.12.2-Linux-x86_64.sh --prefix=${CMAKE_DISTRO} --include-subdir

ENV PATH="/usr/local/distros/cmake/cmake-3.12.2-Linux-x86_64/bin:${PATH}"


#------------------------------------
# Install root
#------------------------------------
#Get the sources
RUN cd downloads \
    && wget https://root.cern.ch/download/root_v6.14.04.source.tar.gz \
    && tar -xf root_v6.14.04.source.tar.gz


RUN cd downloads && mkdir root-6.14.04-build && cd root-6.14.04-build && cmake ../root-6.14.04
RUN cd downloads && cd root-6.14.04-build && make -j2 && make install

RUN cd downloads && rm -r root-6.14.04 && rm -r root-6.14.04-build

RUN yum clean all && rm -rf /var/cache/yum


CMD ["/sbin/init"]
