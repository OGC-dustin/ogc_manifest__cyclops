# OGC.Engineering
### ogc_manifest__cyclops - repo manifest for the cyclops project
developer contact: dustin ( at ) ogc.engineering

---

## Yocto Development Machine ( targeting Kirkstone branch )
* Ubuntu 22.04 LTS
* Install essential packages
```
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python>
sudo locale-gen en_US.UTF-8
```

## Yocto Development Environment
* Use Google's repo tool to reference this manifest and get all associated repositories
* https://git-repo.info/en/docs/multi-repos/overview/
````
repo init -u https://github.com/OGC-dustin/ogc_manifest__cyclops.git -b kirkstone -m default.xml
repo sync
````
* source the poky build environment ( will put you in the build folder ) ( TODO: customize environment as noted below )
```
source sources/poky/oe-init-build-env
```
* add layers ( TODO: automate when sourcing environment )
```
bitbake-layers add-layer ../sources/meta-raspberrypi
bitbake-layers add-layer ../sources/ogc_yocto_customization__hostname
bitbake-layers add-layer ../sources/ogc_yocto_customization__psplash
```
* customize machine in conf/local.conf ( TODO: automate when sourcing environment )
```
MACHINE ?= "raspberrypi"
```
* build minimal image ( fetch first, then build in case of fetch errors )
```
time bitbake core-image-minimal --runall=fetch
time bitbake core-image-minimal
```
* write final image to sdcard ( verify location before using this CLI entry )
```
sudo bmaptool copy tmp/deploy/images/raspberrypi/core-image-minimal-raspberrypi.wic.bz2 /dev/mmcblk0
```
