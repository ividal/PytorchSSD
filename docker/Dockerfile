FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

COPY requirements.txt /tmp/

RUN apt-get update --fix-missing &&\
    apt-get install -y \
        software-properties-common  \
        curl\
        htop \
        git \
        libsm6 \
        libxext6 \
        libfontconfig1 \
        libxrender1 &&\
    add-apt-repository ppa:deadsnakes/ppa &&\
    apt-get update --fix-missing &&\
    apt-get install -y \
        python3.6 \
        python3-dev \
        python3.6-dev \
        python3.6-tk &&\ 
    rm -rf /var/lib/apt/lists/* && \
    curl https://bootstrap.pypa.io/get-pip.py | python3.6 &&\
    pip install -r /tmp/requirements.txt 

RUN pip install http://download.pytorch.org/whl/cu90/torch-0.3.0.post4-cp36-cp36m-linux_x86_64.whl \
                torchvision \
                git+https://github.com/szagoruyko/pyinn.git@master

