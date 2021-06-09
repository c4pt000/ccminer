# ccminer

to build from source                                  
#attention moves gcc as a build system back to fedora 28 and alot of the installed system that depends on gcc
#best done from a docker image or KVM image otherwise,

moves the installed build system back to fedora 28, (building with nvcc nvidia-compiler to match working gcc version that "nvcc" requires)
```
if you have rpmfusion installed
wget https://rpmfusion.org/keys?action=AttachFile&do=get&target=RPM-GPG-KEY-rpmfusion-free-fedora-28
mv RPM-GPG-KEY-rpmfusion-free-fedora-28 /etc/pki/rpm-gpg/
dnf module --releasever=28 --setopt=module_platform_id=platform:f28 disable libgit2:0.26
dnf module --releasever=28 --setopt=module_platform_id=platform:f28 enable libgit2:0.27

some packages might have to be force removed if there are conflicts (use extreme caution)
dnf install --releasever=28 --setopt=module_platform_id=platform:f28 gcc --allowerasing --best
wget https://developer.download.nvidia.com/compute/cuda/repos/fedora33/x86_64/cuda-fedora33.repo
mv cuda-fedora33.repo /etc/yum.repos.d/
yum install cuda nvidia-driver -y
export PATH=/usr/local/cuda-11.3/bin:${PATH:+:${PATH}}
git clone https://github.com/c4pt000/ccminer
cd ccminer
sh autogen.sh
./configure --prefix=/usr
make -j24
make -j24 install

```

Based on Christian Buchner's &amp; Christian H.'s CUDA project, no more active on github since 2014.

Check the [README.txt](README.txt) for the additions

BTC donation address: 1AJdfCpLWPNoAMDfHF1wD5y8VgKSSTHxPo (tpruvot)

A part of the recent algos were originally written by [djm34](https://github.com/djm34) and [alexis78](https://github.com/alexis78)

This variant was tested and built on Linux (ubuntu server 14.04, 16.04, Fedora 22 to 25)
It is also built for Windows 7 to 10 with VStudio 2013, to stay compatible with Windows 7 and Vista.

Note that the x86 releases are generally faster than x64 ones on Windows, but that tend to change with the recent drivers.

The recommended CUDA Toolkit version was the [6.5.19](http://developer.download.nvidia.com/compute/cuda/6_5/rel/installers/cuda_6.5.19_windows_general_64.exe), but some light algos could be faster with the version 7.5 and 8.0 (like lbry, decred and skein).

About source code dependencies
------------------------------

This project requires some libraries to be built :

- OpenSSL (prebuilt for win)
- Curl (prebuilt for win)
- pthreads (prebuilt for win)

The tree now contains recent prebuilt openssl and curl .lib for both x86 and x64 platforms (windows).

To rebuild them, you need to clone this repository and its submodules :
    git clone https://github.com/peters/curl-for-windows.git compat/curl-for-windows


Compile on Linux
----------------

Please see [INSTALL](https://github.com/tpruvot/ccminer/blob/linux/INSTALL) file or [project Wiki](https://github.com/tpruvot/ccminer/wiki/Compatibility)
