BootStrap: docker
From: vanessa/singularity-scientific-example

%post
	sed -i 's/$/ universe/' /etc/apt/sources.list
	locale-gen "en_US.UTF-8"
	dpkg-reconfigure locales
	export LANGUAGE="en_US.UTF-8"
	echo 'LANGUAGE="en_US.UTF-8"' >> /etc/default/locale
	echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale
    echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers

	chmod 777 /tmp
	chmod +t /tmp
	chmod 777 /home/linuxbrew/
	useradd -m linuxbrew
    
    apt-get update \
        && apt-get install -y --no-install-recommends \
                fonts-dejavu-core \
                python-setuptools \
        && rm -rf /var/lib/apt/lists/*

    su -c '/Software/brew/bin/brew tap homebrew/science' linuxbrew
	su -c '/Software/brew/bin/brew install samtools' linuxbrew

    PATH=/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment

    # brew can't be run as root, use as linuxbrew user
    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/base' linuxbrew
    su -c 'brew tap brewsci/science' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew

    su -c 'brew install \
        autoconf \
        automake \
        berkeley-db \
        less \
        libxml2 \
        matplotlib \
        miller \
        numpy' linuxbrew