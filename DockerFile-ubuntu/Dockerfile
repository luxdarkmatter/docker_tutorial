FROM ubuntu:18.04


RUN apt-get update && apt-get install -y autoconf automake binutils build-essential \
    cmake dpkg-dev gcc gfortran git g++ make ssh python3-pip python3-dev\
    libboost-all-dev \
    libxft-dev libxext-dev libssl-dev libpcre3-dev \
    xlibmesa-glu-dev libglew1.5-dev libftgl-dev \
    libmysqlclient-dev libfftw3-dev libcfitsio-dev \
    graphviz-dev libavahi-compat-libdnssd-dev \
    libldap2-dev python-dev libxml2-dev libkrb5-dev \
    libgsl0-dev


RUN apt-get clean all

RUN pip3 install numpy scipy matplotlib




CMD ["/sbin/init"]
