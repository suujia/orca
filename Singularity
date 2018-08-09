BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://us.archive.ubuntu.com/ubuntu/

%runscript
	# print out software versions installed by linuxbrew
	find /Software/Cellar -maxdepth 2 -print | sed 's|/Software/brew/Cellar||g' | sed 's|^/||' | grep "/" | sed 's|/|\t|' | sort | awk '{print $1, $2, "Homebrew"}' | column -t | sort -u --ignore-case

%post
	sed -i 's/$/ universe/' /etc/apt/sources.list
	locale-gen "en_US.UTF-8"
	dpkg-reconfigure locales
	export LANGUAGE="en_US.UTF-8"
	echo 'LANGUAGE="en_US.UTF-8"' >> /etc/default/locale
	echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale
    echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers

    mkdir /Software
	chmod 777 /tmp
	chmod +t /tmp
	chmod 777 /Software
	useradd -m linuxbrew

    apt-get update \
        && apt-get install -y --no-install-recommends \
                fonts-dejavu-core \
                python-setuptools \
        && rm -rf /var/lib/apt/lists/*

	apt-get install -y apt-transport-https build-essential cmake curl libsm6 libxrender1 libfontconfig1 wget vim git unzip python-setuptools ruby
	su -c 'cd /Software && git clone https://github.com/Linuxbrew/brew.git' linuxbrew

    PATH=/Software/bin:/Software/sbin:$PATH
    echo 'PATH='$PATH >> /etc/environment

    su -c 'brew update' linuxbrew
    su -c 'brew tap brewsci/base' linuxbrew
    su -c 'brew tap brewsci/science' linuxbrew
    su -c 'brew tap brewsci/bio' linuxbrew

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