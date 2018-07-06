Bootstrap: docker
From: linuxbrew/linuxbrew

%labels
    MAINTAINER="sjackman@gmail.com"

%environment
    # sourced at runtime (for buildtime, include in %post)
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    export PERL5LIB

    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    export PATH

%setup
    # Runs from outside the container during Bootstrap

%post
    # Runs within the container during Bootstrap 
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    export PERL5LIB

    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    export PATH

    echo 'PERL5LIB='$PERL5LIB > /environment
    echo 'PATH='$PATH >> /environment

    # make environmental file executable
    # chmod +x /etc/environment
    chown -R linuxbrew /opt/linuxbrew

    # make environmental file executable
    # chmod +x /etc/environment

    chmod 4755 /usr/local/bin/sudo
    chmod -R 777 /home/linuxbrew/.linuxbrew
    chmod -R 777 /home/linuxbrew/.linuxbrew/Homebrew

    apt-get update \
	&& apt-get install -y --no-install-recommends \
		fonts-dejavu-core \
	&& rm -rf /var/lib/apt/lists/*

    # get to linuxbrew user to do brew update
    chown -R linuxbrew /usr/local/

    # brew can't be run as root, use as linuxbrew user
    su -c 'brew update' linuxbrew

    # back to root to do the moving below
    mv /opt/linuxbrew/bin/brew /usr/local/bin/
    mv /opt/linuxbrew/Library /usr/local/
    chown -R linuxbrew /usr/local/

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
    perl \
    python \
    python@2 \
    r \
    ruby \
    scipy \
    tcsh \
    unzip \
    vim \
    zip \
    zlib' linuxbrew

    pip2 install \
    biopython \
    python-igraph

    pip3 install --no-cache-dir --upgrade \
    biopython \
    cwlref-runner \
    htseq \
    pandas \
    pysam \
    python-igraph \
    pyvcf \
    virtualenv

    Rscript -e 'install.packages(repos = c(CRAN = "https://cran.rstudio.com"), c( \
    "devtools", \
    "ggplot2", \
    "knitr", \
    "rmarkdown", \
    "tidyverse")); \
    source("https://bioconductor.org/biocLite.R"); biocLite()

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
    anvio \
    aragorn \
    arcs \
    art \
    artemis \
    ascp \
    astral \
    atram \
    augustus \
    bali-phy \
    bam-readcount \
    bam2wig \
    bamhash \
    bamm \
    bamtools \
    bamutil \
    bandange \
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
    lua \
    lumpy-sv \
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
    yaha' linuxbrew