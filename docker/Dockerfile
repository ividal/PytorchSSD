FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

COPY requirements.txt /tmp/

RUN apt-get update --fix-missing &&\
    apt-get install -y \
        software-properties-common  \
        curl\
        htop \
        git &&\
    add-apt-repository ppa:deadsnakes/ppa &&\
    apt-get update --fix-missing &&\
    apt-get install -y \
        python3.6 \
        python3-dev \
        python3.6-dev &&\   
    rm -rf /var/lib/apt/lists/* && \
    curl https://bootstrap.pypa.io/get-pip.py | python3.6 &&\
    pip install -r /tmp/requirements.txt

RUN cd /tmp/ && \
    git clone -b temp/local-config https://github.com/ividal/PytorchSSD.git 
    
ENV CUDA_PATH=/usr/local/cuda

RUN cd /tmp/PytorchSSD/utils &&\
    python3.6 build.py build_ext --inplace
RUN pip install git+https://github.com/szagoruyko/pyinn.git@master

