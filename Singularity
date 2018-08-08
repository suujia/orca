Bootstrap: docker
From: linuxbrew/linuxbrew

%labels
    MAINTAINER="sjackman@gmail.com"

%post
    chown -R root:root /usr/bin/sudo
    chown -R linuxbrew: /usr/local
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew/Homebrew

    chmod -R 777 /home/linuxbrew/.linuxbrew

    # need to create mount point for home dir, scratch
    mkdir /uufs /scratch

    apt-get update \
        && apt-get install -y --no-install-recommends \
                fonts-dejavu-core \
                python-setuptools \
        && rm -rf /var/lib/apt/lists/*
    apt-get clean

    # for brew install to work
    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment

    echo "
      export PATH=/usr/local/bin:$PATH
      export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
    " >> /etc/environment

    # brew can't be run as root, use as li nuxbrew user
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/base' linuxbrew
    su -c 'brew tap brewsci/science' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew

    su -c 'brew install \
    autoconf \
    automake \
    berkeley-db \
    expat \
    jdk \
    less \
    libxml2 \
    matplotlib \
    miller \
    numpy \
    python \
    python@2 \
    scipy \
    tcsh \
    unzip \
    zip \
    zlib' linuxbrew