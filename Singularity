Bootstrap: docker
From: linuxbrew/linuxbrew

%labels
    MAINTAINER="sjackman@gmail.com"

%post
    chown -R linuxbrew: /usr/local
    chown -R linuxbrew: /home/linuxbrew/
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew/Homebrew

    # need to create mount point for home dir
    # scratch is larger than /tmp and is always local
    mkdir /uufs
    mkdir /scratch

    apt-get update \
        && apt-get install -y --no-install-recommends \
                fonts-dejavu-core \
                python-setuptools \
        && rm -rf /var/lib/apt/lists/*

    export PERL5LIB PATH SINGULARITY_DISABLE_CACHE=yes

    # for brew install to work
    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment

    # install everything at the user's home directory 
    cd /home/linuxbrew/

    # brew can't be run as root, use as linuxbrew user
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/base' linuxbrew
    su -c 'brew tap brewsci/science' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew

    su -c 'brew install autoconf' linuxbrew
    su -c 'brew install automake' linuxbrew
    su -c 'brew install berkeley-db' linuxbrew
    su -c 'brew install jdk' linuxbrew
    su -c 'brew install less' linuxbrew
    su -c 'brew install numpy' linuxbrew
    su -c 'brew install tcsh' linuxbrew
    su -c 'brew install unzip' linuxbrew
    su -c 'brew install zip' linuxbrew
    su -c 'brew install zlib' linuxbrew
    su -c 'brew install expat' linuxbrew
    su -c 'brew install pandoc' linuxbrew
    su -c 'brew install libxml2' linuxbrew
    su -c 'brew install miller' linuxbrew

    su -c 'brew install perl' linuxbrew
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

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

    pip2 install --upgrade  \
    --upgrade setuptools \
    -U pip \
    biopython

    pip3 install --upgrade \
    --upgrade setuptools \
    --no-cache-dir biopython \
    cwlref-runner \
    pandas \
    pysam \
    pyvcf \
    virtualenv


    su -c 'brew install r' linuxbrew
    Rscript -e 'install.packages(c("ggplot2", "knitr", "rmarkdown", "tidyverse"), repos = "http://cran.rstudio.com"); source("https://bioconductor.org/biocLite.R"); biocLite()'

    su -c 'brew install matplotlib' linuxbrew
    su -c 'brew install mysql' linuxbrew
    su -c 'brew install scipy' linuxbrew
    su -c 'brew install vim' linuxbrew
    su -c 'brew install cpanm' linuxbrew

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
    bali-phy
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

%file 
    # runs automatically when the simg is run 
    # python /hello_world.py

%test
    exec R --version
