#albacore in singularity

BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://us.archive.ubuntu.com/ubuntu/

%runscript
    read_fast5_basecaller.py "$@"

%post
    apt-get --assume-yes install wget
    apt-get --assume-yes install sudo

    sudo apt-get update
    sudo apt-get --assume-yes install python3

    sudo apt-get --assume-yes install python3-setuptools
    sudo easy_install3 pip

    mkdir -p /albacore/
    cd /albacore/
    wget https://mirror.oxfordnanoportal.com/software/analysis/ont_albacore-0.8.4-cp35-cp35m-manylinux1_x86_64.whl
    pip3 install ont_albacore-0.8.4-cp35-cp35m-manylinux1_x86_64.whl\
    
    sudo mkdir /groups
    sudo mkdir /clustertmp

%test
    read_fast5_basecaller.py -h
    
