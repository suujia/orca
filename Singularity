BootStrap: debootstrap
OSVersion: xenial
MirrorURL: http://us.archive.ubuntu.com/ubuntu/

%runscript
	# print out software versions installed by linuxbrew
	find /Software/brew/Cellar -maxdepth 2 -print | sed 's|/Software/brew/Cellar||g' | sed 's|^/||' | grep "/" | sed 's|/|\t|' | sort | awk '{print $1, $2, "Homebrew"}' | column -t | sort -u --ignore-case

%post
    apt-get update \
	&& apt-get install -y --no-install-recommends \
                   curl ca-certificates file g++ git locales make uuid-runtime \
	&& apt-get clean \
        && rm -rf /var/lib/apt/lists/*

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

	apt-get update
	apt-get install -y apt-transport-https build-essential cmake libsm6 libxrender1 libfontconfig1 wget vim git unzip python-setuptools ruby
	apt-get clean
	useradd -m linuxbrew
	su -c 'cd .linuxbrew && git clone https://github.com/Linuxbrew/brew.git' linuxbrew
	su -c '/Software/brew/bin/brew tap homebrew/science' linuxbrew
	su -c '/Software/brew/bin/brew install samtools' linuxbrew
                                                                                                                     
	sed -i 's|PATH=$PATH:/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin|PATH="/home/linuxbrew/.linuxbrew/Homebrew/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"|' /environment
    su -c 'brew doctor' linuxbrew