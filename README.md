# Install open source NVIDIA driver on Debian 10
## NOTE BEFORE WE BEGIN

Most desktop environments come with the open source drivers preinstalled.
Also make sure that your sources.list file looks like this
```
# See https://wiki.debian.org/SourcesList for more information.
deb http://deb.debian.org/debian buster main contrib
deb-src http://deb.debian.org/debian buster main contrib

deb http://deb.debian.org/debian buster-updates main contrib
deb-src http://deb.debian.org/debian buster-updates main contrib

deb http://security.debian.org/debian-security/ buster/updates main contrib
deb-src http://security.debian.org/debian-security/ buster/updates main contrib
```

## The steps 

Set root password
```
sudo -i
passwd
```
It will ask you to type a new sudo password.

Use root account
```
su
```
OR
```
sudo -i
```
First install these packages
```
sudo apt -y install xorg xserver-xorg-video-nouveau mesa libglu libglvnd firmware-linux build-essential gcc-multilib dracut
```

Remove the blacklist file if present
```
sudo rm -rf /etc/modprobe.d/blacklist.conf
```

Rebuild the kernel

```
sudo dracut -v /boot/initramfs-$(uname -r).img $(uname -r)
```

Next reboot

```
sudo reboot
```
