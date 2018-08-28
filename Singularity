Bootstrap: docker
From: ubuntu:latest


%post

  apt-get update
  apt-get install -y wget git vim tmux tree htop
  apt-get install -y libtool m4 automake
  apt-get install -y unrar unzip


  # Utility and support packages
  apt-get install -y aptitude build-essential cmake gcc g++ gfortran git \
      pkg-config python-pip python-dev software-properties-common


  # More utilities
  # apt-get install -y graphviz libatlas-dev libfreetype6 libfreetype6-dev \
  #     libgraphviz-dev liblapack-dev swig libxft-dev libxml2-dev \
  #     libxslt-dev zlib1g-dev

  # wget "http://registrationcenter-download.intel.com/akdlm/irc_nas/tec/12998/parallel_studio_xe_2018_update3_cluster_edition.tgz"
  #
	# mkdir ~/psxe_staging_area
	# tar -xvzf parallel_studio_xe_2018_update3_cluster_edition.tgz -C ~/psxe_staging_area
  #
	# cd ~/psxe_staging_area/parallel_studio_xe_2018_update3_cluster_edition
  #
  # sed -i 's/decline/accept/' silent.cfg
  # sed -i 's/COMPONENTS=DEFAULTS/COMPONENTS=ALL/' silent.cfg
  # sed -i 's/ACTIVATION_TYPE=exist_lic/ACTIVATION_TYPE=serial_number/' silent.cfg
  # sed -i 's/#ACTIVATION_SERIAL_NUMBER=snpat/ACTIVATION_SERIAL_NUMBER=ST5V-FXTNFJHK/' silent.cfg

  # ./install.sh --silent=silent.cfg

  wget "https://cmake.org/files/v3.12/cmake-3.12.1.tar.gz"
  tar -xzf cmake-3.12.1.tar.gz
  cd cmake-3.12.1
  ./bootstrap
  make
  make install

  wget "http://glaros.dtc.umn.edu/gkhome/fetch/sw/metis/metis-5.1.0.tar.gz"
  tar -xvf metis-5.1.0.tar.gz
  cd metis-5.1.0
  make

%runscript

exec echo Hello "$@"
