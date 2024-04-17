# debian-setup
```
sudo apt install debootstrap
```
Debootstrap : 
```
cd ~/SANDBOX
sudo -s
mkdir -p $pwd/Focal
export MY_CHROOT=~/SANDBOX/Focal/
sudo debootstrap --arch=amd64 focal $MY_CHROOT  http://archive.ubuntu.com/ubuntu/
```
watch it download focal

now, you have a ubuntu focal inside a debian

After that we need some setup for process, system input, hosts, etc.
Make sure you are still in current shell, and as a root

```
echo "proc $MY_CHROOT/proc proc defaults 0 0" >> /etc/fstab
mount proc $MY_CHROOT/proc -t proc
echo "sysfs $MY_CHROOT/sys sysfs defaults 0 0" >> /etc/fstab
mount sysfs $MY_CHROOT/sys -t sysfs
cp /etc/hosts $MY_CHROOT/etc/hosts
cp /proc/mounts $MY_CHROOT/etc/mtab
```

after that, exit from root shell

```
exit
```

let's check our new ubuntu 20.04

```
sudo chroot Focal
```


add user :
```
adduser foccy
usermod -aG sudo foccy
```



fix sources list :
```
sudo nano /etc/apt/sources.list
```
then add :
```
deb http://archive.ubuntu.com/ubuntu focal main restricted multiverse universe
```

then update :
```
sudo apt update
```

install something from new source : 
'''
sudo apt install neofetch kitty
'''


ricing up ; 
nano ~/.bashrc
su ficcy

nano /home/foccy/.bashrc 
cd ~
neofetch

you need to mount :
- tmp
- dev
- tmp/pts
- sudo mount -o bind /home/hifzhil/SANDBOX/Focal/home/foccy/ /home/hifzhil/Foccy/

 and adding a LOCAL: to xhost by 
 xhost + LOCAL:

after that install this required server :
sudo apt-get install -y xserver-xorg

adding this file to fstab :



