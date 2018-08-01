Bootstrap: docker
From: linuxbrew/linuxbrew

%labels
    MAINTAINER="sjackman@gmail.com"

%runscript
  exec python "$@" 

%post
    chown root:root /usr/bin/sudo
    chmod 4755 /usr/bin/sudo

    chown -R linuxbrew: /usr/local
    chown -R linuxbrew: /home/linuxbrew/
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew/Homebrew

    # need to create mount point for home dir, scratch
    mkdir /uufs /scratch

    # install all brew packages in user home dir
    cd /home/linuxbrew 

    apt-get update \
        && apt-get install -y --no-install-recommends \
                fonts-dejavu-core \
                python-setuptools \
        && rm -rf /var/lib/apt/lists/*
    apt-get clean

    export PATH SINGULARITY_DISABLE_CACHE=yes

    # for brew install to work
    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment

    # install everything at the user's home directory 
    # cd /home/linuxbrew/

    # brew can't be run as root, use as linuxbrew user
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/base' linuxbrew
    su -c 'brew tap brewsci/science' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew

    su -c 'brew install expat' linuxbrew
    su -c 'brew install libxml2' linuxbrew
    su -c 'brew install miller' linuxbrew

    su -c 'brew install automake' linuxbrew
    su -c 'brew install berkeley-db' linuxbrew
    su -c 'brew install jdk' linuxbrew
    su -c 'brew install less' linuxbrew
    su -c 'brew install numpy' linuxbrew
    su -c 'brew install tcsh' linuxbrew
    su -c 'brew install unzip' linuxbrew
    su -c 'brew install zip' linuxbrew
    su -c 'brew install zlib' linuxbrew

    # python3 installed with numpy, python2 installed with jdk
    #    python \
    #    python@2 \

    su -c 'brew install ruby' linuxbrew
    # for gem install to work 
    export PATH=/usr/local/lib/ruby/gems/2.0.0/bin:$PATH
    export PATH=/usr/local/opt/ruby20/bin:$PATH
    su -c 'brew install ruby' linuxbrew

    su -c 'gem install \
    gnuplot \
    narray \
    RubyInline \
    terminal-table \
    && gem cleanup all' linuxbrew

    pip2 install \
    --upgrade setuptools \
    -U pip \
    biopython

    pip3 install \
    --upgrade setuptools \
    -U pip \
    --no-cache-dir biopython \
    cwlref-runner \
    pandas \
    pyvcf \
    virtualenv

    su -c 'brew install matplotlib' linuxbrew
   # su -c 'brew install mysql' linuxbrew
   # su -c 'brew install scipy' linuxbrew
   # su -c 'brew install vim' linuxbrew
   # su -c 'brew install cpanm' linuxbrew
   # su -c 'brew install pandoc' linuxbrew

    su -c 'brew install perl' linuxbrew
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

    su -c 'brew install autoconf' linuxbrew

%file 
    # runs automatically when the simg is run 
    # python /hello_world.py

%test
    # exec R --version

    # Test numpy 
    /usr/bin/python -c "import numpy as np;np.__config__.show()"