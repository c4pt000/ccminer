# ccminer

export PATH=/usr/local/cuda-11.3/bin:${PATH:+:${PATH}}   is part of PATH in /root/.bashrc


to build from source                                  
```
mkdir /opt/TMP-ccminer
yum install libcurl-devel -y
docker run -it -d -v /opt/TMP-ccminer:/opt/TMP-ccminer c4pt/ccminer-cuda-build-env
docker exec -it <docker_vm_sha256> bash
cd ccminer
sh build.sh
./ccminer                       # (mixture of fedora 28, fedora 34 libs)
checkinstall --install=no --exclude=/sys/fs/selinux -D
alien --scripts --to-rpm ccminer*.deb
cp -rf *deb *rpm /opt/TMP-ccminer/
exit
cd /opt/TMP-ccminer
yum install ccminer


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


