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
    su -c 'brew tap brewsci/bio' linuxbrew
    
    su -c 'brew install ruby' linuxbrew
    su -c 'brew install r' linuxbrew
    Rscript -e 'install.packages(c("ggplot2", "knitr", "rmarkdown", "tidyverse"), repos = "http://cran.rstudio.com"); source("https://bioconductor.org/biocLite.R"); biocLite()'
   
    su -c 'brew install expat' linuxbrew
    su -c 'brew install libxml2' linuxbrew
    su -c 'brew install miller' linuxbrew

    su -c 'brew install automake' linuxbrew
    su -c 'brew install berkeley-db' linuxbrew
    su -c 'brew install jdk' linuxbrew
    su -c 'brew install less' linuxbrew
    su -c 'brew install numpy' linuxbrew
    su -c 'brew install r' linuxbrew
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
    bali-phy \
    bamutil \
    barrnap \
    bamhash \
    bamm \
    bamtools' linuxbrew

    # sudo: effective uid is not 0
    su -c 'brew install adam' linuxbrew
    su -c 'brew install amos' linuxbrew

    # no available formula 
    # su -c 'brew install bam-readcount' linuxbrew
    # su -c 'brew install bam2wig' linuxbrew
    # su -c 'brew install bandange' linuxbrew
    # su -c 'brew install novoalign' linuxbrew
    # su -c 'brew install pysam' linuxbrew

    # the post-install step did not complete 
    # su -c 'brew install abricate' linuxbrew

    # conflicting versions of dependencies isl, isl@0.18, gcc@6, gcc
    # su -c 'brew install atram' linuxbrew

    su -c 'brew install bbtools' linuxbrew
    su -c 'brew install bcalm' linuxbrew
    su -c 'brew install bcftools' linuxbrew
    su -c 'brew install beagle' linuxbrew
    su -c 'brew install beast' linuxbrew
    su -c 'brew install beast2' linuxbrew
    su -c 'brew install bedops' linuxbrew
    su -c 'brew install bedtools' linuxbrew
    su -c 'brew install beetl' linuxbrew
    su -c 'brew install berokka' linuxbrew
    su -c 'brew install bfc' linuxbrew
    su -c 'brew install bioawk' linuxbrew
    su -c 'brew install biobloomtools' linuxbrew
    su -c 'brew install biomake' linuxbrew
    su -c 'brew install bioperl' linuxbrew
    su -c 'brew install bison' linuxbrew
    su -c 'brew install blast' linuxbrew
    su -c 'brew install blast-legacy' linuxbrew
    su -c 'brew install blat' linuxbrew
    su -c 'brew install bless' linuxbrew
    su -c 'brew install bonsai' linuxbrew
    su -c 'brew install bowtie' linuxbrew
    su -c 'brew install bowtie2' linuxbrew
    su -c 'brew install breseq' linuxbrew
    su -c 'brew install busco' linuxbrew
    su -c 'brew install bwa' linuxbrew
    su -c 'brew install cannoli' linuxbrew
    su -c 'brew install canu' linuxbrew
    su -c 'brew install cap3' linuxbrew
    su -c 'brew install cd-hit' linuxbrew
    su -c 'brew install cegma' linuxbrew
    su -c 'brew install celera-assembler' linuxbrew
    su -c 'brew install centrifuge' linuxbrew
    su -c 'brew install cerulean' linuxbrew
    su -c 'brew install circlator' linuxbrew
    su -c 'brew install circos' linuxbrew
    su -c 'brew install clark' linuxbrew
    su -c 'brew install clonalframeml' linuxbrew
    su -c 'brew install clonehd' linuxbrew
    su -c 'brew install clustal-omega' linuxbrew
    su -c 'brew install clustal-w' linuxbrew
    su -c 'brew install cmake' linuxbrew
    su -c 'brew install consel' linuxbrew
    su -c 'brew install curl' linuxbrew
    su -c 'brew install cutadapt' linuxbrew
    su -c 'brew install daligner' linuxbrew
    su -c 'brew install dazz_db' linuxbrew
    su -c 'brew install delly' linuxbrew
    su -c 'brew install dextractor' linuxbrew
    su -c 'brew install diamond' linuxbrew
    su -c 'brew install dida' linuxbrew
    su -c 'brew install discovar' linuxbrew
    su -c 'brew install disty' linuxbrew
    su -c 'brew install dsh-bio' linuxbrew
    su -c 'brew install dsk' linuxbrew
    su -c 'brew install dwgsim' linuxbrew
    su -c 'brew install e-mem' linuxbrew
    su -c 'brew install easel' linuxbrew
    su -c 'brew install edirect' linuxbrew
    su -c 'brew install elph' linuxbrew
    su -c 'brew install ema' linuxbrew
    su -c 'brew install emacs' linuxbrew
    su -c 'brew install emboss' linuxbrew
    su -c 'brew install exabayes' linuxbrew
    su -c 'brew install exonerate' linuxbrew
    su -c 'brew install fasta' linuxbrew
    su -c 'brew install fastani' linuxbrew
    su -c 'brew install fastml' linuxbrew
    su -c 'brew install fastp' linuxbrew
    su -c 'brew install fastq-tools' linuxbrew
    su -c 'brew install fastqc' linuxbrew
    su -c 'brew install fasttree' linuxbrew
    su -c 'brew install fastuniq' linuxbrew
    su -c 'brew install fastx_toolkit' linuxbrew
    su -c 'brew install fermi' linuxbrew
    su -c 'brew install fermi-lite' linuxbrew
    su -c 'brew install fermi2' linuxbrew
    su -c 'brew install fermikit' linuxbrew
    su -c 'brew install figtree' linuxbrew
    su -c 'brew install finch-rs' linuxbrew
    su -c 'brew install flash' linuxbrew
    su -c 'brew install flex' linuxbrew
    su -c 'brew install flye' linuxbrew
    su -c 'brew install fqzcomp' linuxbrew
    su -c 'brew install freebayes' linuxbrew
    su -c 'brew install freec' linuxbrew
    su -c 'brew install fsa' linuxbrew
    su -c 'brew install fwdpp' linuxbrew
    su -c 'brew install gatb' linuxbrew
    su -c 'brew install gatk' linuxbrew
    su -c 'brew install geneid' linuxbrew
    su -c 'brew install genewise' linuxbrew
    su -c 'brew install genome-painter' linuxbrew
    su -c 'brew install genometools' linuxbrew
    su -c 'brew install gepard' linuxbrew
    su -c 'brew install gfalint' linuxbrew
    su -c 'brew install gfakluge' linuxbrew
    su -c 'brew install gingr' linuxbrew
    su -c 'brew install glimmerhmm' linuxbrew
    su -c 'brew install gmap-gsnap' linuxbrew
    su -c 'brew install grabix' linuxbrew
    su -c 'brew install graphviz' linuxbrew
    su -c 'brew install gsl' linuxbrew
    su -c 'brew install gzstream' linuxbrew
    su -c 'brew install harfbuzz' linuxbrew
    su -c 'brew install hisat' linuxbrew
    su -c 'brew install hisat2' linuxbrew
    su -c 'brew install hlaminer' linuxbrew
    su -c 'brew install hmmer' linuxbrew
    su -c 'brew install hmmer2' linuxbrew
    su -c 'brew install htsbox' linuxbrew
    su -c 'brew install htslib' linuxbrew
    su -c 'brew install humann2' linuxbrew
    su -c 'brew install idba' linuxbrew
    su -c 'brew install igv' linuxbrew
    su -c 'brew install igvtools' linuxbrew
    su -c 'brew install impute2' linuxbrew
    su -c 'brew install infernal' linuxbrew
    su -c 'brew install iqtree' linuxbrew
    su -c 'brew install ispcr' linuxbrew
    su -c 'brew install iva' linuxbrew
    su -c 'brew install jellyfish' linuxbrew
    su -c 'brew install jpeg' linuxbrew
    su -c 'brew install jspecies' linuxbrew
    su -c 'brew install k8' linuxbrew
    su -c 'brew install kaiju' linuxbrew
    su -c 'brew install kallisto' linuxbrew
    su -c 'brew install kat' linuxbrew
    su -c 'brew install kent-tools' linuxbrew
    su -c 'brew install kma' linuxbrew
    su -c 'brew install kmacs' linuxbrew
    su -c 'brew install kmc' linuxbrew
    su -c 'brew install kmergenie' linuxbrew
    su -c 'brew install kmerstream' linuxbrew
    su -c 'brew install kollector' linuxbrew
    su -c 'brew install kr' linuxbrew
    su -c 'brew install kraken' linuxbrew
    su -c 'brew install last' linuxbrew
    su -c 'brew install lastz' linuxbrew
    su -c 'brew install libbigwig' linuxbrew
    su -c 'brew install libpll' linuxbrew
    su -c 'brew install libsequence' linuxbrew
    su -c 'brew install libtool' linuxbrew
    su -c 'brew install light-assembler' linuxbrew
    su -c 'brew install lighter' linuxbrew
    su -c 'brew install links-scaffolder' linuxbrew
    su -c 'brew install lofreq' linuxbrew
    su -c 'brew install lrsim' linuxbrew
    su -c 'brew install lsd' linuxbrew
    su -c 'brew install lua' linuxbrew
    su -c 'brew install lumpy-sv' linuxbrew
    su -c 'brew install macse' linuxbrew
    su -c 'brew install mafft' linuxbrew
    su -c 'brew install magic-blast' linuxbrew
    su -c 'brew install makedepend' linuxbrew
    su -c 'brew install maker' linuxbrew
    su -c 'brew install man-db' linuxbrew
    su -c 'brew install mapsembler2' linuxbrew
    su -c 'brew install maq' linuxbrew
    su -c 'brew install mash' linuxbrew
    su -c 'brew install mcl' linuxbrew
    su -c 'brew install megahit' linuxbrew
    su -c 'brew install meme' linuxbrew
    su -c 'brew install metaphlan' linuxbrew
    su -c 'brew install methpipe' linuxbrew
    su -c 'brew install mhap' linuxbrew
    su -c 'brew install minced' linuxbrew
    su -c 'brew install minia' linuxbrew
    su -c 'brew install miniasm' linuxbrew
    su -c 'brew install minimap' linuxbrew
    su -c 'brew install minimap2' linuxbrew
    su -c 'brew install mir-prefer' linuxbrew
    su -c 'brew install mitofy' linuxbrew
    su -c 'brew install mlst' linuxbrew
    su -c 'brew install mosdepth' linuxbrew
    su -c 'brew install mothur' linuxbrew
    su -c 'brew install mp-est' linuxbrew
    su -c 'brew install mpboost' linuxbrew
    su -c 'brew install mrbayes' linuxbrew
    su -c 'brew install multi-worm-tracker' linuxbrew
    su -c 'brew install mummer' linuxbrew
    su -c 'brew install muscle' linuxbrew
    su -c 'brew install nano' linuxbrew
    su -c 'brew install nanopolish' linuxbrew
    su -c 'brew install ncl' linuxbrew
    su -c 'brew install newick-utils' linuxbrew
    su -c 'brew install newicktools' linuxbrew
    su -c 'brew install nextflow' linuxbrew 
    su -c 'brew install novoalign' linuxbrew
    su -c 'brew install ntcard' linuxbrew
    su -c 'brew install nxtrim' linuxbrew
    su -c 'brew install oases' linuxbrew
    su -c 'brew install oma' linuxbrew
    su -c 'brew install orfm' linuxbrew
    su -c 'brew install orthofinder' linuxbrew
    su -c 'brew install paml' linuxbrew
    su -c 'brew install pandaseq' linuxbrew
    su -c 'brew install panito' linuxbrew
    su -c 'brew install parallel' linuxbrew
    su -c 'brew install parsnp' linuxbrew
    su -c 'brew install pathd8' linuxbrew
    su -c 'brew install pathvisio' linuxbrew
    su -c 'brew install pcre' linuxbrew
    su -c 'brew install pear' linuxbrew
    su -c 'brew install phipack' linuxbrew
    su -c 'brew install phlawd' linuxbrew
    su -c 'brew install phylip' linuxbrew
    su -c 'brew install phyml' linuxbrew
    su -c 'brew install phyutility' linuxbrew
    su -c 'brew install phyx' linuxbrew
    su -c 'brew install picard-tools' linuxbrew
    su -c 'brew install piler' linuxbrew
    su -c 'brew install pilercr' linuxbrew
    su -c 'brew install pilon' linuxbrew
    su -c 'brew install pixman' linuxbrew
    su -c 'brew install pkg-config' linuxbrew
    su -c 'brew install plink' linuxbrew
    su -c 'brew install poa' linuxbrew
    su -c 'brew install porechop' linuxbrew
    su -c 'brew install portcullis' linuxbrew
    su -c 'brew install prank' linuxbrew
    su -c 'brew install prodigal' linuxbrew
    su -c 'brew install prokka' linuxbrew
    su -c 'brew install proteinortho' linuxbrew
    su -c 'brew install psmc' linuxbrew
    su -c 'brew install quast' linuxbrew
    su -c 'brew install quest' linuxbrew
    su -c 'brew install quickmerge' linuxbrew
    su -c 'brew install quicktree' linuxbrew
    su -c 'brew install quorum' linuxbrew
    su -c 'brew install r8s' linuxbrew
    su -c 'brew install racon' linuxbrew
    su -c 'brew install rampart' linuxbrew
    su -c 'brew install rapidnj' linuxbrew
    su -c 'brew install raxml' linuxbrew
    su -c 'brew install raxml-ng' linuxbrew
    su -c 'brew install ray' linuxbrew
    su -c 'brew install rcorrector' linuxbrew
    su -c 'brew install readline' linuxbrew
    su -c 'brew install readseq' linuxbrew
    su -c 'brew install readsim' linuxbrew
    su -c 'brew install realphy' linuxbrew
    su -c 'brew install recon' linuxbrew
    su -c 'brew install repeatmasker' linuxbrew
    su -c 'brew install repeatmodeler' linuxbrew
    su -c 'brew install repeatscout' linuxbrew
    su -c 'brew install rmblast' linuxbrew
    su -c 'brew install rna-star' linuxbrew
    su -c 'brew install rnammer' linuxbrew
    su -c 'brew install ropebwt2' linuxbrew
    su -c 'brew install rtg-tools' linuxbrew
    su -c 'brew install salmon' linuxbrew
    su -c 'brew install sambamba' linuxbrew
    su -c 'brew install samblaster' linuxbrew
    su -c 'brew install samclip' linuxbrew
    su -c 'brew install samtools' linuxbrew
    su -c 'brew install samtools@0.1' linuxbrew
    su -c 'brew install scarpa' linuxbrew
    su -c 'brew install sdsl-lite' linuxbrew
    su -c 'brew install seq-gen' linuxbrew
    su -c 'brew install seqan' linuxbrew
    su -c 'brew install seqkit' linuxbrew
    su -c 'brew install seqtk' linuxbrew
    su -c 'brew install sequel' linuxbrew
    su -c 'brew install sga' linuxbrew
    su -c 'brew install shovill' linuxbrew
    su -c 'brew install shrimp' linuxbrew
    su -c 'brew install sickle' linuxbrew
    su -c 'brew install simulate-pcr' linuxbrew
    su -c 'brew install skesa' linuxbrew
    su -c 'brew install skewer' linuxbrew
    su -c 'brew install smalt' linuxbrew
    su -c 'brew install snap' linuxbrew
    su -c 'brew install snoscan' linuxbrew
    su -c 'brew install snp-dists' linuxbrew
    su -c 'brew install snp-sites' linuxbrew
    su -c 'brew install snpeff' linuxbrew
    su -c 'brew install soapdenovo' linuxbrew
    su -c 'brew install solexaqa' linuxbrew
    su -c 'brew install sortmerna' linuxbrew
    su -c 'brew install spaced' linuxbrew
    su -c 'brew install spades' linuxbrew
    su -c 'brew install spici' linuxbrew
    su -c 'brew install sqlite' linuxbrew
    su -c 'brew install squeakr' linuxbrew
    su -c 'brew install squeezambler' linuxbrew
    su -c 'brew install sratoolkit' linuxbrew
    su -c 'brew install ssake' linuxbrew
    su -c 'brew install stringtie' linuxbrew
    su -c 'brew install swarm' linuxbrew
    su -c 'brew install szip' linuxbrew
    su -c 'brew install tagdust' linuxbrew
    su -c 'brew install tasr' linuxbrew
    su -c 'brew install tbb' linuxbrew
    su -c 'brew install tbl2asn' linuxbrew
    su -c 'brew install tigmint' linuxbrew
    su -c 'brew install tophat' linuxbrew
    su -c 'brew install trans-abyss' linuxbrew
    su -c 'brew install transdecoder' linuxbrew
    su -c 'brew install transrate-tools' linuxbrew
    su -c 'brew install treepl' linuxbrew
    su -c 'brew install trf' linuxbrew
    su -c 'brew install trimadap' linuxbrew
    su -c 'brew install trimal' linuxbrew
    su -c 'brew install trimmomatic' linuxbrew
    su -c 'brew install trinity' linuxbrew
    su -c 'brew install trnascan' linuxbrew
    su -c 'brew install unicycler' linuxbrew
    su -c 'brew install uniqtag' linuxbrew
    su -c 'brew install uproc' linuxbrew
    su -c 'brew install vague' linuxbrew
    su -c 'brew install varscan' linuxbrew
    su -c 'brew install varsim' linuxbrew
    su -c 'brew install vcake' linuxbrew
    su -c 'brew install vcflib' linuxbrew
    su -c 'brew install vcftools' linuxbrew
    su -c 'brew install velvet' linuxbrew
    su -c 'brew install velvetoptimiser' linuxbrew
    su -c 'brew install viennarna' linuxbrew
    su -c 'brew install vsearch' linuxbrew
    su -c 'brew install vt' linuxbrew
    su -c 'brew install weblogo' linuxbrew
    su -c 'brew install wiggletools' linuxbrew
    su -c 'brew install yaha' linuxbrew

    su -c 'brew install perl' linuxbrew
    PERL5LIB=/home/linuxbrew/perl5/lib/perl5
    echo 'PERL5LIB='$PERL5LIB >> /etc/environment

    su -c 'brew install autoconf' linuxbrew
    
%file 
    # runs automatically when the simg is run 
    # python /hello_world.py

%test
    exec R --version

    # Test numpy 
    /usr/bin/python -c "import numpy as np;np.__config__.show()"