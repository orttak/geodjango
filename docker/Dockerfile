FROM python:3

#USER root

## Set environment variables
ENV LANG=C.UTF-8 LC_ALL=C.UTF-8


RUN apt-get update --fix-missing


RUN apt-get install -y wget \
	bzip2 \
	ca-certificates \
	build-essential \
	curl \
	git-core \
	pkg-config \
	python3-dev \
	python3-pip \
	python3-setuptools \
	python3-virtualenv \
	unzip \
	software-properties-common \
	llvm

RUN add-apt-repository -y ppa:ubuntugis/ubuntugis-unstable && apt-get update
RUN apt-get update --fix-missing

# Set python aliases for python3
RUN echo 'alias python=python3' >> ~/.bashrc
RUN echo 'alias pip=pip3' >> ~/.bashrc

RUN apt-get install -y gdal-bin \
		       libgdal-dev

# Update C env vars so compiler can find gdal
ENV CPLUS_INCLUDE_PATH=/usr/include/gdal
ENV C_INCLUDE_PATH=/usr/include/gdal


## Install packages to Python3
RUN pip3 install --upgrade pip
 


# Generate default config and disable authentication
WORKDIR /home
COPY requirements.txt .
RUN pip3 install -r requirements.txt










