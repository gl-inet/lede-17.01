Overview  
======== 

This repo forks from [LEDE Source Repository](https://git.lede-project.org/source.git), adding patches for  
buildroot、kernel and GL-iNet's new devices to lede-17.01.  

Prerequisites  
=============  

To build your own firmware you need to have access to a Linux, BSD or  
MacOSX system (case-sensitive filesystem required). Cygwin will not be  
supported because of the lack of case sensitiveness in the file system.  
Ubuntu is usually recommended. Examples of package installations:    

```bash  
$ sudo apt-get update
$ sudo apt-get install build-essential subversion libncurses5-dev zlib1g-dev gawk gcc-multilib flex git-core gettext libssl-dev
```  

Download Sources  
================  

```  
$ git clone https://github.com/gl-inet/lede-17.01 && cd lede-17.01
$ ./scripts/feeds update -a
$ ./scripts/feeds install -a
$ ./scripts/feeds install -p gli_pub -a -f -o >/dev/null 2>&1
```  

Make Image  
==========  

Build Quick Image  
-----------------    

Use "make menuconfig" to configure your image.  

Simply running "make" will build your firmware. It will download all sources,  
build the cross-compile toolchain, the kernel and all choosen applications.  

Note that if you have all the source already, just put them in your *lede-17.01/dl*  
folder and you save time to download resource.  

Build Release Image  
-------------------  

If you want to build an image the same as our released firmware, which is available  
to install gli's repo packages via opkg, including webui. This is easy to integrate  
3rd part software into image. For example, building a v2.27 firmware of ar71xx generic:  

```  
$ git checkout v2.27
$ curl -o .config http://www.gl-inet.com/releases/2.27/targets/ar71xx/generic/config.seed
$ make defconfig
$ make PACKAGES="gl-base-files gl-inet gl-modem gl-util"
```  

PACKAGES - Install specified packages to rootfs, push your own ipk packages to  
*lede-17.01/prebuilt/xxx* directory, "xxx" is board specified, like ar71xx and  
ramips and so on.  
