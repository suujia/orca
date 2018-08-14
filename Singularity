BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://us.archive.ubuntu.com/ubuntu/

%runscript
	# print out software versions installed by linuxbrew
	find /Software/brew/Cellar -maxdepth 2 -print | sed 's|/Software/brew/Cellar||g' | sed 's|^/||' | grep "/" | sed 's|/|\t|' | sort | awk '{print $1, $2, "Homebrew"}' | column -t | sort -u --ignore-case

%post
	sed -i 's/$/ universe/' /etc/apt/sources.list
	locale-gen "en_US.UTF-8"
	dpkg-reconfigure locales
	export LANGUAGE="en_US.UTF-8"
	echo 'LANGUAGE="en_US.UTF-8"' >> /etc/default/locale
	echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale
    echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers
    useradd -m -s /bin/bash linuxbrew

    apt-get update \
        && apt-get install -y --no-install-recommends \
                bzip2 \
                ca-certificates \
                curl \
                file \
                fonts-dejavu-core \
                g++ \
                git \
                locales \
                make \
                openssh-client \
                patch \
                sudo \
                uuid-runtime \
        && rm -rf /var/lib/apt/lists/*

    mkdir /home/linuxbrew/.linuxbrew
    mkdir /home/linuxbrew/.linuxbrew/bin
	ln -s ../Homebrew/bin/brew /home/linuxbrew/.linuxbrew/bin/
	chown -R linuxbrew: /home/linuxbrew/.linuxbrew
	cd /home/linuxbrew/.linuxbrew/Homebrew
	git remote set-url origin https://github.com/Linuxbrew/brew.git

    cd /home/linuxbrew 

    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment
    SHELL=/bin/bash
    echo 'SHELL='$SHELL >> /etc/environment
    USER=linuxbrew
    echo 'USER='$USER >> /etc/environment

    export HOMEBREW_NO_ANALYTICS=1 HOMEBREW_NO_AUTO_UPDATE=1 
    su -c 'brew tap homebrew/core' linuxbrew
    rm -rf ~/.cache

    # test brew install brewsci tools 
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew
    su -c 'brew install \
    matplotlib \
    nextflow' linuxbrew

%post
    chown -R linuxbrew: /home/linuxbrew/
    chmod 777 /home/linuxbrew/.linuxbrew
    chmod 777 /home/linuxbrew/.linuxbrew/Homebrew

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
    cpanm \
    expat \
    jdk \
    less \
    libxml2 \
    matplotlib \
    miller \
    mysql \
    numpy \
    pandoc \
    python \
    python@2 \
    scipy \
    tcsh \
    vim \
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

    su -c 'brew install \
    gfalint \
    gfakluge \
    gingr \
    glimmerhmm \
    gmap-gsnap \
    grabix \
    graphviz \
    gsl \
    gzstream \
    harfbuzz \
    hisat \
    hisat2 \
    hlaminer \
    hmmer \
    hmmer2 \
    htsbox \
    htslib \
    humann2 \
    idba \
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
    kent-tools \
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
    lrsim \
    lsd \
    lumpy-sv \
    mafft \
    magic-blast \
    makedepend \
    maker \
    linuxbrew/extra/man-db \
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
    minia \
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
    multi-worm-tracker \
    mummer \
    muscle \
    nano \
    ncl \
    newick-utils \
    newicktools \
    nextflow \
    brewsci/science/novoalign \
    ntcard \
    nxtrim \
    oases \
    oma \
    orfm \
    orthofinder \
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
    phyx \
    picard-tools \
    piler \
    pilercr \
    pilon \
    pixman \
    pkg-config \
    plink \
    poa \
    portcullis \
    prank \
    prodigal \
    prokka \
    proteinortho \
    psmc \
    quast \
    quest \
    quickmerge \
    quicktree \
    quorum \
    r8s \
    racon \
    rampart \
    rapidnj \
    raxml \
    raxml-ng \
    ray \
    rcorrector \
    readline \
    readseq \
    readsim \
    realphy \
    recon \
    repeatmasker \
    repeatmodeler \
    repeatscout \
    rmblast \
    rna-star \
    rnammer \
    ropebwt2 \
    rtg-tools \
    salmon \
    sambamba \
    samblaster \
    samclip \
    samtools \
    samtools@0.1 \
    scarpa \
    sdsl-lite \
    seq-gen \
    seqan \
    seqkit \
    seqtk \
    sequel \
    sga \
    shovill \
    shrimp \
    sickle \
    simulate-pcr \
    skesa \
    skewer \
    smalt \
    snap \
    snoscan \
    snp-dists \
    snp-sites \
    snpeff \
    soapdenovo \
    solexaqa \
    sortmerna \
    spaced \
    spades \
    spici \
    sqlite \
    squeakr \
    squeezambler \
    sratoolkit \
    ssake \
    stringtie \
    swarm \
    szip \
    tagdust \
    tasr \
    tbb \
    tbl2asn \
    tophat \
    trans-abyss \
    transdecoder \
    transrate-tools \
    treepl \
    trf \
    trimadap \
    trimmomatic \
    trnascan \
    unicycler \
    uniqtag \
    uproc \
    vague \
    varscan \
    varsim \
    vcake \
    vcflib \
    vcftools \
    velvet \
    velvetoptimiser \
    viennarna \
    vsearch \
    vt \
    weblogo \
    wiggletools \
    yaha' linuxbrew

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
    abricate \
    abyss \
    abyss-explorer \
    ace-corrector \
    adam \
    adapterremoval \
    afra \
    amos \
    andi \
    aragorn \
    arcs \
    art \
    artemis \
    ascp \
    astral \
    augustus \
    bali-phy \
    bam-readcount \
    bamhash \
    bamm \
    bamtools \
    bamutil \
    bandage \
    barrnap \
    bbtools \
    bcalm \
    bcftools \
    beagle \
    beast \
    beast2 \
    bedops \
    bedtools \
    beetl \
    berokka \
    bfc \
    bioawk \
    biobloomtools \
    biomake \
    bioperl \
    bison \
    blast \
    blast-legacy \
    blat \
    bless \
    bonsai \
    bowtie \
    bowtie2 \
    breseq \
    busco \
    bwa \
    cannoli \
    canu \
    cap3 \
    cd-hit \
    cegma \
    celera-assembler \
    centrifuge \
    cerulean \
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
    figtree \
    finch-rs \
    flash \
    flex \
    flye \
    fqzcomp \
    freebayes \
    freec \
    fsa \
    fwdpp \
    gatb \
    gatk \
    geneid \
    genewise \
    genome-painter \
    genometools' linuxbrew
    
    su -c 'brew install perl' linuxbrew
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment
