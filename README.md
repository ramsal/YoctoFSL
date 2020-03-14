# YoctoFSL


## Proceso de Yocto con Variscite FSL

### Entorno
```
Máquina Ubuntu 16

$ sudo apt-get install gawk wget git diffstat unzip texinfo gcc-multilib \
build-essential chrpath socat cpio python python3 python3-pip python3-pexpect \
xz-utils debianutils iputils-ping libsdl1.2-dev xterm

$ sudo apt-get install autoconf libtool libglib2.0-dev libarchive-dev python-git \
sed cvs subversion coreutils texi2html docbook-utils python-pysqlite2 \
help2man make gcc g++ desktop-file-utils libgl1-mesa-dev libglu1-mesa-dev \
mercurial automake groff curl lzop asciidoc u-boot-tools dos2unix mtd-utils pv \
libncurses5 libncurses5-dev libncursesw5-dev libelf-dev zlib1g-dev
```
### Instalación 
```
$ git config --global user.name "Your Name"
$ git config --global user.email "Your Email"

$ mkdir ~/bin (this step may not be needed if the bin folder already exists)
$ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
$ export PATH=~/bin:$PATH
```

```
$ mkdir ~/var-fsl-yocto
$ cd ~/var-fsl-yocto
$ repo init -u https://github.com/varigit/variscite-bsp-platform.git -b fsl-sumo -m imx-4.14.98-2.0.1_patch-var01.xml
$ repo sync -j4
```

```
$ cd ~/var-fsl-yocto
$ MACHINE=imx8qm-var-som DISTRO=fsl-imx-xwayland . var-setup-release.sh -b build_xwayland

//Without Qt content:
$ bitbake fsl-image-gui

//Or with Qt content:
$ bitbake fsl-image-qt5
```

### Estructura principal 
```
~/var-fsl-yocto
.
├── build_xwayland
│   ├── cache
│   ├── conf
│   │   ├── bblayers.conf
│   │   ├── bblayers.conf.org
│   │   ├── bitbake-cookerdaemon.log
│   │   ├── local.conf
│   │   ├── local.conf.org
│   │   └── templateconf.cfg
│   ├── sources
│   │   ├──base
│   │   ├──meta-browser 
│   │   ├──meta-freescale
│   │   ├──meta-freescale-distro
│   │   ├──meta-freescale-3rdparty  
│   │   ├──meta-fsl-bsp-release  
│   │   ├──meta-openembedded 
│   │   ├──poky
│   │   ├──meta-qt5 
│   │   ├──meta-swupdate          
│   │   ├──meta-variscite-imx
```
