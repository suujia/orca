Bootstrap: docker
From: linuxbrew/linuxbrew

%labels
    MAINTAINER="sjackman@gmail.com"

%runscript
  exec python "$@" 

%runscript
  exec R "$@" 

%post
    chown -R root:root /usr/bin/sudo
    chown -R linuxbrew: /usr/local
    chown -R linuxbrew: /home/linuxbrew/
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew/Homebrew

    chmod 775 /usr/local
    chmod 775 /home/linuxbrew/
    chmod 775 /home/linuxbrew/.linuxbrew
    chmod 775 /home/linuxbrew/.linuxbrew/Homebrew

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

    # for brew install to work
    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment

    echo "
      export PATH=/usr/local/bin:$PATH
      export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
    " >> /etc/environment

    # install everything at the user's home directory 
    # cd /home/linuxbrew/

    # brew can't be run as root, use as linuxbrew user
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/base' linuxbrew
    su -c 'brew tap brewsci/science' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew

    # man-db is in linuxbrew/extra
    su -c 'brew tap linuxbrew/extra' linuxbrew

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

  # su -c 'brew install mysql' linuxbrew
    su -c 'brew install vim' linuxbrew
    su -c 'brew install cpanm' linuxbrew
  # su -c 'brew install pandoc' linuxbrew

    # for gem install to work 
    su -c 'brew install ruby' linuxbrew
    export PATH=/usr/local/lib/ruby/gems/2.0.0/bin:$PATH
    export PATH=/usr/local/opt/ruby20/bin:$PATH
    su -c 'gem install \
    gnuplot \
    narray \
    RubyInline \
    terminal-table \
    && gem cleanup all' linuxbrew

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
    augustus' linuxbrew

    su -c 'brew install \
    cannoli \
    canu \
    cap3 \
    cd-hit \
    cegma \
    celera-assembler \
    centrifuge \
    cerulean' linuxbrew

    su -c 'brew install \
    circlator \
    circos \
    clark \
    clonalframeml \
    clonehd \
    clustal-omega \
    clustal-w \
    cmake \
    consel \
    curl \
    cutadapt \
    daligner \
    dazz_db \
    delly \
    dextractor \
    diamond \
    dida \
    discovar \
    disty \
    dsh-bio \
    dsk \
    dwgsim \
    e-mem \
    easel \
    edirect \
    elph \
    ema \
    emacs \
    emboss \
    exonerate  \
    fasta \
    fastani \
    fastml \
    fastp \
    fastq-tools \
    fastqc \
    fasttree \
    fastuniq \
    fastx_toolkit \
    fermi \
    fermi-lite \
    fermi2 \
    fermikit \
    finch-rs \
    flash \
    flex \
    flye \
    fqzcomp \
    freec \
    fsa \
    fwdpp \
    gatb \
    gatk \
    geneid \
    genewise \
    genome-painter \
    gepard \
    gfalint \
    gfakluge \
    gingr \
    glimmerhmm \
    gmap-gsnap \
    grabix \
    graphviz \
    gzstream' linuxbrew

    su -c 'brew install \
    harfbuzz \
    hisat \
    hisat2 \
    hlaminer \
    hmmer \
    hmmer2 \
    htsbox \
    htslib \
    humann2 \
    igv \
    igvtools \
    impute2 \
    infernal \
    iqtree \
    ispcr \
    jellyfish \
    jpeg \
    jspecies \
    k8 \
    kaiju \
    kallisto \
    kat \
    kma \
    kmacs \
    kmc \
    kmergenie \
    kmerstream \
    kollector \
    kr \
    kraken \
    last \
    lastz \
    libbigwig \
    libpll \
    libsequence \
    libtool \
    light-assembler \
    lighter \
    links-scaffolder \
    lofreq \
    lsd \
    lumpy-sv' linuxbrew

    su -c 'brew install \
    macse \
    mafft \
    magic-blast \
    makedepend \
    maker \
    man-db \
    mapsembler2 \
    maq \
    mash \
    mcl \
    megahit \
    meme \
    metaphlan \
    methpipe \
    mhap \
    minced \
    minia' linuxbrew

    su -c 'brew install \
    miniasm \
    minimap \
    minimap2 \
    mir-prefer \
    mitofy \
    mlst \
    mosdepth \
    mothur \
    mp-est \
    mrbayes \
    multi-worm-tracker' linuxbrew

    su -c 'brew install \
    mummer \
    muscle \
    nano \
    nanopolish \
    ncl \
    newick-utils \
    newicktools \
    nextflow
    ntcard \
    nxtrim \
    oases \
    oma \
    orfm \
    orthofinder' linuxbrew

    su -c 'brew install \
    paml \
    pandaseq \
    panito \
    parallel \
    parsnp \
    pathd8 \
    pathvisio \
    pcre \
    pear \
    phipack \
    phlawd \
    phyml \
    phyutility \
    picard-tools \
    piler \
    pilercr \
    pilon \
    pixman \
    pkg-config \
    plink \
    poa \
    prank \
    prodigal' linuxbrew

    su -c 'brew install \
    prokka \
    psmc \
    quast \
    quest \
    quickmerge \
    quicktree \
    r8s \
    racon \
    rampart \
    rapidnj \
    raxml \
    ray \
    readline \
    readseq \
    readsim \
    realphy \
    recon \
    repeatmodeler \
    repeatscout \
    rmblast \
    rna-star \
    rnammer \
    rtg-tools \
    salmon \
    sambamba' linuxbrew

    su -c 'brew install \
    samblaster \
    samclip \
    samtools \
    samtools@0.1 \
    scarpa \
    sdsl-lite \
    seq-gen \
    seqan \
    seqkit \
    sga \
    shovill \
    shrimp \
    sickle \
    simulate-pcr \
    skesa' linuxbrew

    su -c 'brew install \
    tagdust \
    tasr \
    tbb \
    tophat \
    trans-abyss \
    transdecoder \
    transrate-tools \
    trf \
    trimadap \
    trimmomatic \
    trnascan \
    uniqtag \
    uproc \
    vague \
    varscan \
    varsim \
    vcake' linuxbrew

    su -c 'brew install \
    vcftools \
    velvet \
    velvetoptimiser \
    viennarna \
    vsearch \
    vt \
    weblogo \
    wiggletools \
    yaha' linuxbrew

    su -c 'brew install perl' linuxbrew
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

%file 
    # runs automatically when the simg is run 
    # eg. python /hello_world.py