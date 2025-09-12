# Setting up bochs: 

Use the command below to download and compile bochs: 

```shell
cd /tmp
wget https://sourceforge.net/projects/bochs/files/bochs/2.6/bochs-2.6.tar.gz
tar xf bochs-2.6.tar.gz
cd bochs-2.6
sh .conf.linux
make -j$(nproc)
sudo make install
```

Then, you have to copy `/usr/share/doc/bochs/bochsrc-sample.txt` to your working folder. 

Rename `bochsrc-sample.txt` to `bochsrc.disk`. 

Use the command below to create a hard disk image for BeyondOS. 

``` shell
bximage
```

Follow the instruct in bximage, and type these options: 

``` shell
hd
flat
60
hd60M.img
```

At the end, you have to position 'ata0-master: ' and modified the line in bochsrc.disk to: 

```
ata0-master: type=disk, mode=flat, path="hd60M.img"
```