## fast-vm installation

```shell
curl -o /etc/yum.repos.d/fast-vm.repo https://copr.fedorainfracloud.org/coprs/ondrejhome/fast-vm/repo/epel-8/ondrejhome-fast-vm-epel-8.repo
dnf install fast-vm
configure-fast-vm 
```

## adding image
```shell
fast-vm import_image centos-7.6 http://ftp.linux.cz/pub/linux/people/ondrej_famera/fastvm-images/generated/6g__centos-7.6.img.xz https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/centos/xml/centos-6.3-current.xml https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/centos/hacks/6g_centos-7-hacks.sh
fast-vm import_image debian-10.1 http://ftp.linux.cz/pub/linux/people/ondrej_famera/fastvm-images/generated/6g__debian-10.1.img.xz https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/debian/xml/debian-10.xml https://raw.githubusercontent.com/OndrejHome/fast-vm-public-images/master/debian/hacks/debian-10.sh
fast-vm list_images
```

## create VM and run it
```
fast-vm create debian-10.1 20
fast-vm start 20
fast-vm console 20
fast-vm ssh 20
```

fast-vm list
fast-vm list --all
fast-vm list_profiles 
fast-vm create centos-7.6 21
fast-vm start 21
fast-vm console 21
```

