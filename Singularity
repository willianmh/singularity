Bootstrap: docker
From: nvidia/cuda:9.2-cudnn7-devel-ubuntu16.04

%environment

	#Environment variables

	#Use bash as default shell
	SHELL=/bin/bash

	#Add CUDA paths
	CPATH="/usr/local/cuda/include:$CPATH"
	PATH="/usr/local/cuda/bin:$PATH"
	LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
	CUDA_HOME="/usr/local/cuda"

	#Add Anaconda path
	PATH="/usr/local/anaconda3-4.2.0/bin:$PATH"

	export PATH LD_LIBRARY_PATH CPATH CUDA_HOME

%setup
	#Runs on host
	#The path to the image is $SINGULARITY_ROOTFS



%post
	#Post setup script

	#Load environment variables
	. /environment

	#Default mount paths
	mkdir /scratch /data /shared /fastdata


  #Updating and getting required packages
  apt-get update
  apt-get install -y wget git vim tmux tree htop
	apt-get install -y libtool m4 automake
	apt-get install -y unrar unzip


	# Utility and support packages
  apt-get install -y aptitude build-essential cmake gcc g++ gfortran git \
      pkg-config python-pip python-dev software-properties-common


	# More utilities
  apt-get install -y graphviz libatlas-dev libfreetype6 libfreetype6-dev \
      libgraphviz-dev liblapack-dev swig libxft-dev libxml2-dev \
      libxslt-dev zlib1g-dev

  # Python modules from system package manager
  apt-get install -y python-numpy python-scipy python-nose python-h5py \
      python-skimage python-matplotlib python-pandas python-sklearn \
      python-sympy python-virtualenv




  #Creates a build directory
  mkdir build
  cd build

  #Download and install Anaconda
  CONDA_INSTALL_PATH="/usr/local/anaconda3-4.2.0"
  wget https://repo.continuum.io/archive/Anaconda3-4.2.0-Linux-x86_64.sh
  chmod +x Anaconda3-4.2.0-Linux-x86_64.sh
  ./Anaconda3-4.2.0-Linux-x86_64.sh -b -p $CONDA_INSTALL_PATH


  #Install Tensorflow
  pip install tensorflow-gpu

	#Install Keras
	pip install keras

%runscript
	#Executes with the singularity run command
	#delete this section to use existing docker ENTRYPOINT command


%test
	#Test that script is a success
