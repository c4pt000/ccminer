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


https://github.com/KlausT/ccminer

```



original source
https://github.com/tpruvot/ccminer
