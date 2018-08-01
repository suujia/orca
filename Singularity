Bootstrap: docker
From: linuxbrew/linuxbrew

%labels
    MAINTAINER="sjackman@gmail.com"

%runscript
  exec python "$@" 

%apprun Rscript
  exec Rscript "$@"

%runscript
  exec R "$@" 

%post
    chown root:root /usr/bin/sudo
    chmod 4755 /usr/bin/sudo
    chown -R linuxbrew: /usr/local
    chown -R linuxbrew: /home/linuxbrew/
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew
    chown -R linuxbrew: /home/linuxbrew/.linuxbrew/Homebrew

    chmod 755 /usr/local
    chmod 755 /home/linuxbrew/
    chmod 755 /home/linuxbrew/.linuxbrew
    chmod 755 /home/linuxbrew/.linuxbrew/Homebrew

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
    
    su -c 'brew install ruby' linuxbrew
    su -c 'brew install r' linuxbrew
    # Rscript -e 'install.packages("ggplot2"), repos = "http://cran.rstudio.com"); source("https://bioconductor.org/biocLite.R"); biocLite()'
    # Rscript -e 'install.packages("knitr"), repos = "http://cran.rstudio.com"); source("https://bioconductor.org/biocLite.R"); biocLite()'
    # Rscript -e 'install.packages("rmarkdown"), repos = "http://cran.rstudio.com"); source("https://bioconductor.org/biocLite.R"); biocLite()'
    # Rscript -e 'install.packages("tidyverse"), repos = "http://cran.rstudio.com"); source("https://bioconductor.org/biocLite.R"); biocLite()'

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

    su -c 'brew install \
    a5 \
    abacas \
    abyss \
    abyss-explorer \
    ace-corrector' linuxbrew

    su -c 'brew install \
    adam \
    adapterremoval \
    afra \
    amos \
    andi \
    anvio' linuxbrew

    su -c 'brew install \
    aragorn \
    arcs \
    art \
    artemis \
    ascp \
    astral' linuxbrew

    su -c 'brew install \
    augustus \
    bali-phy
    bamhash \
    bamm \
    bamtools \
    bamutil' linuxbrew

    su -c 'brew install \
    bandange \
    barrnap \
    bbtools \
    bcalm \
    bcftools \
    beagle \
    beast' linuxbrew

    su -c 'brew install \
    beast2 \
    bedops \
    bedtools \
    beetl \
    berokka \
    bfc' linuxbrew

    su -c 'brew install \
    bioawk \
    biobloomtools \
    biomake \
    bioperl \
    bison \
    blast' linuxbrew

    su -c 'brew install \
    blast-legacy \
    blat \
    bless \
    bonsai \
    bowtie \
    bowtie2 \
    breseq \
    busco' linuxbrew

    su -c 'brew install \
    bwa \
    cannoli \
    canu \
    cap3 \
    cd-hit \
    cegma \
    celera-assembler' linuxbrew

    su -c 'brew install \
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
    delly' linuxbrew

    su -c 'brew install \
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
    exonerate' linuxbrew

    su -c 'brew install \
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
    fwdpp' linuxbrew

    su -c 'brew install \
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
    impute2' linuxbrew

    su -c 'brew install \
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
    kr' linuxbrew

    su -c 'brew install \
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
    maq' linuxbrew

    su -c 'brew install \
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
    mrbayes' linuxbrew

    su -c 'brew install \
    multi-worm-tracker \
    mummer \
    muscle \
    nano \
    nanopolish \
    ncl \
    newick-utils \
    newicktools \
    nextflow \ 
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
    phyml' linuxbrew

    su -c 'brew install \
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
    r8s' linuxbrew

    su -c 'brew install \
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
    rmblast' linuxbrew

    su -c 'brew install \
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
    seqtk' linuxbrew

    su -c 'brew install \
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
    snp-sites' linuxbrew
    
    su -c 'brew install \
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
    tbb' linuxbrew
    
    su -c 'brew install \
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
    unicycler' linuxbrew

    su -c 'brew install \
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

    su -c 'brew install perl' linuxbrew
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

    su -c 'brew install autoconf' linuxbrew
    pip3 install pysam

%file 
    # runs automatically when the simg is run 
    # python /hello_world.py

%test
    exec R --version

    # Test numpy 
    /usr/bin/python -c "import numpy as np;np.__config__.show()"