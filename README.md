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
repo init -u https://github.com/OGC-dustin/ogc_manifest__cyclops.git
repo sync
````
* source the poky build environment ( will put you in the build folder )
```
source sources/poky/oe-init-build-env
```



## 
