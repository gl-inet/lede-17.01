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

