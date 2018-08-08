BootStrap: debootstrap
OSVersion: trusty
MirrorURL: http://us.archive.ubuntu.com/ubuntu/

%labels
    MAINTAINER="sjackman@gmail.com"

%apprun R
  exec R "$@"

%apprun Rscript
  exec Rscript "$@"

%runscript
  exec R "$@"

%post
    mkdir -p /Software 
    cd /Software
    chmod 777 /Software

    # need to create mount point for home dir
    mkdir /uufs

    apt-get update \
        && apt-get install -y --no-install-recommends \
                fonts-dejavu-core \
                python-setuptools \
        && rm -rf /var/lib/apt/lists/*
    apt-get clean

    # set up linuxbrew 
    locale-gen "en_US.UTF-8"
    dpkg-reconfigure locales
    export LANGUAGE="en_US.UTF-8"
    echo 'LANGUAGE="en_US.UTF-8"' >> /etc/default/locale
    echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale
    cd /Software
    chmod 777 /scratch
    chmod +t /scratch
    apt-get install -y apt-transport-https build-essential libsm6 libxrender1 libfontconfig1 ruby
    useradd -m singularity
    su -c 'cd /Software && git clone https://github.com/Linuxbrew/brew.git /Software/brew' singularity
    su -c 'brew install gawk' singularity

    # for brew install to work
    PATH=/Software/brew/bin:/Software/brew/sbin:$PATH
    export PATH

    # brew can't be run as root, use as linuxbrew user
    su -c 'brew update' singularity
    su -c 'brew tap brewsci/base' singularity
    su -c 'brew tap brewsci/science' singularity
    su -c 'brew tap brewsci/bio' singularity

    su -c 'brew install bcalm' singularity

    su -c 'brew install \
    autoconf \
    automake \
    berkeley-db \
    expat \
    less \
    libxml2 \
    miller \
    numpy \
    python \
    python@2 \
    tcsh \
    unzip \
    zip \
    zlib' singularity

    # python3 installed with numpy, python2 installed with jdk

    # for gem install to work 
    export PATH=/usr/local/lib/ruby/gems/2.0.0/bin:$PATH
    export PATH=/usr/local/opt/ruby20/bin:$PATH
    su -c 'brew install ruby' singularity
    su -c 'gem install \
    gnuplot \
    narray \
    RubyInline \
    terminal-table \
    && gem cleanup all' singularity

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

    su -c 'brew install matplotlib' singularity
    su -c 'brew install scipy' singularity
    su -c 'brew install vim' singularity
    su -c 'brew install cpanm' singularity
    su -c 'brew install pandoc' singularity

    su -c 'brew install \
    a5 \
    abacas \
    abyss \
    abyss-explorer \
    ace-corrector \
    adapterremoval \
    afra \
    andi \
    anvio \
    aragorn \
    arcs \
    art \
    artemis \
    ascp \
    astral \
    augustus' singularity

    su -c 'brew install \
    bali-phy \
    bamutil \
    barrnap \
    bamhash \
    bamm \
    bamtools \
    busco \
    bwa' singularity
    
    su -c 'brew install \
    cannoli \
    canu \
    cap3 \
    cd-hit \
    cegma \
    celera-assembler \
    centrifuge \
    cerulean' singularity

    su -c 'brew install perl' singularity
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

%file 
    # runs automatically when the simg is run 
    # python /hello_world.py