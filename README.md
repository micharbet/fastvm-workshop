# fast-vm workshop resource

[presentation](fastvm-openalt2019.odp)

## fast-vm installation

- Fedora 30
```shell
curl -o /etc/yum.repos.d/fast-vm.repo https://copr.fedorainfracloud.org/coprs/ondrejhome/fast-vm/repo/fedora-30/ondrejhome-fast-vm-fedora-30.repo
dnf install fast-vm
```

- CentOS 8
```shell
curl -o /etc/yum.repos.d/fast-vm.repo https://copr.fedorainfracloud.org/coprs/ondrejhome/fast-vm/repo/epel-8/ondrejhome-fast-vm-epel-8.repo
dnf install fast-vm
```

- Debian
```shell
apt-get install gdebi-core
wget https://github.com/OndrejHome/fast-vm/releases/download/1.6/fast-vm_1.6_all-debian10.deb
gdebi fast-vm_1.6_all-debian10.deb
apt-get install libguestfs-tools zstd
```

- Create free volume group if you don't have one
```shell
dd if=/dev/zero of=/your/path/fvm.dd bs=1M count=17000
losetup -f /your/path/fvm.dd
losetup -a
pvcreate /dev/loop0
vgcreate fvm /dev/loop0
vgs
```

- One-shot setup
```shell
configure-fast-vm 
```

## adding image
```shell
fast-vm import_image centos-7.6 \
 http://ftp.linux.cz/pub/linux/people/ondrej_famera/fastvm-images/generated/6g__centos-7.6.img.xz \
 https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/centos/xml/centos-6.3-current.xml \
 https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/centos/hacks/6g_centos-7-hacks.sh

fast-vm import_image debian-10.1 \
 http://ftp.linux.cz/pub/linux/people/ondrej_famera/fastvm-images/generated/6g__debian-10.1.img.xz \
 https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/debian/xml/debian-10.xml \
 https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/debian/hacks/debian-10.sh

fast-vm list_images
```

## create VM and run it
```shell
fast-vm create debian-10.1 20
fast-vm start 20
fast-vm console 20
fast-vm ssh 20
```
Note: the number '20' denotes your new VM, numbers can be between 20 and 220. The number
is also the last octet of IP address. By default 192.168.22.20

root's password is `testtest`


## get information about virtual machines
```shell
fast-vm list
fast-vm list --all
fast-vm list_profiles 
virsh list --all
lvs
```

