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

    mkdir /home/linuxbrew/.linuxbrew/bin \
	&& ln -s ../Homebrew/bin/brew /home/linuxbrew/.linuxbrew/bin/ \
	&& chown -R linuxbrew: /home/linuxbrew/.linuxbrew \
	&& cd /home/linuxbrew/.linuxbrew/Homebrew \
	&& git remote set-url origin https://github.com/Linuxbrew/brew.git

    cd /home/linuxbrew 
    export PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH \
	export SHELL=/bin/bash
    export USER=linuxbrew

    export HOMEBREW_NO_ANALYTICS=1 HOMEBREW_NO_AUTO_UPDATE=1 
    su -c 'brew tap homebrew/core' linuxbrew
    rm -rf ~/.cache

    # test brew install brewsci tools 
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew
    su -c 'brew install \
    matplotlib \
    nextflow' linuxbrew
