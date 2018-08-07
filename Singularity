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
    jdk \
    less \
    libxml2 \
    miller \
    numpy \
    python \
    python@2 \
    r \
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
   # su -c 'brew install mysql' singularity
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
    exabayes \
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
    genometools \
    gepard \
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
    iva \
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
    lumpy-sv' singularity
    
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
    mpboost \
    mrbayes \
    multi-worm-tracker \
    mummer \
    muscle \
    nano \
    nanopolish \
    ncl \
    newick-utils \
    newicktools \
    nextflow \ 
    nonpareil \
    novoalign \
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
    phylip \
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
    porechop \
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
    tigmint \
    tophat \
    trans-abyss \
    transdecoder \
    transrate-tools \
    treepl \
    trf \
    trimadap \
    trimal \
    trimmomatic \
    trinity \
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
    yaha' singularity

    su -c 'brew install perl' singularity
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

%file 
    # runs automatically when the simg is run 
    # python /hello_world.py