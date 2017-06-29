# Header
BootStrap: docker
From: ubuntu:16.04

# Sections
%setup

%environment
PATH=/opt/conda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

%post
apt-get -y update && apt-get install -y build-essential

apt-get install -y apt-utils

apt-get install -y gfortran

apt-get install -y libopenblas-base

apt-get install -y liblapacke-dev libnetcdf-dev libarpack2-dev libboost-all-dev

apt-get install -y wget

apt-get install -y libgtk2.0-dev

echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh -O ~/anaconda.sh && \
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh

#install pip

export PATH=/opt/conda/bin:$PATH

conda install -c anaconda pip

pip install --upgrade pip

pip install Theano

conda install -y --quiet -c conda-forge tensorflow-gpu=1.1.0

pip install keras

pip install hyperas

conda install jupyter -y --quiet && mkdir /opt/notebooks

apt-get install -y nano

mkdir -p /nobackup

#Now install OpenCV
#SSH certificat error on 290617- need to check...
#conda install -y --quiet -c https://conda.binstar.org/menpo opencv3

JN_PORT=$(shuf -i 8000-9000 -n 1)

echo "Jupyter Notebook Server will run on port: ", $JN_PORT

%runscript
