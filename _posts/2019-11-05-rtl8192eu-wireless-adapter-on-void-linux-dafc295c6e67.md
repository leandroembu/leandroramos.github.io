---
layout:	"post"
categories:	"blog"
title:	"RTL8192EU Wireless Adapter on Void Linux"
date:	2019-11-05
thumbnail:	/img/1*i6_3pAYsDtbF6E2YIlLfcQ.png
author:	
---

* * *

![](/img/1*i6_3pAYsDtbF6E2YIlLfcQ.png)

Void Linux with XFCE

The TP-LINK TL-WN821N wireless adapter (chipset RTL8192EU) doesn't work by
default, so I have adapted the steps in <https://github.com/Mange/rtl8192eu-
linux-driver> (made for Debian/Ubuntu)to work on Void Linux.

 **Important:** I 'll be using _sudo_ to do it, because I don 't like to use
the root login for everything.

* * *

#### Installing dependencies

    
    
    sudo xbps-install git linux-headers base-devel dkms

#### Cloning the Github repository

    
    
    git clone <https://github.com/Mange/rtl8192eu-linux-driver>

#### Accessing the driver directory

    
    
    cd rtl8192eu-linux-driver

#### Adding the driver to DKMS

Please don't forget to type the dot (.) in the command below

    
    
    sudo dkms add .

![](/img/0*5KHurknw5La5FAZb.png)

#### Building and installing the driver

    
    
    sudo dkms install rtl8192eu/1.0

![](/img/0*gz15t_8v4nijcugv.png)

#### Blacklisting the generic Realtek driver

    
    
    echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf

#### Creating the modules-load directory

    
    
    sudo mkdir /etc/modules-load.d

#### Forcing RTL8192EU Driver to be active from boot

    
    
    echo -e "8192eu\n\nloop" | sudo tee /etc/modules-load.d/rtl8192eu.conf

#### Updating changes to GRUB

    
    
    sudo update-grub

![](/img/0*wfBvVDERwMFoRiJI.png)

#### Updating changes to initramfs

    
    
    sudo dracut --force

![](/img/0*ZmrGusUgQk7eDSTr.png)

#### Rebooting the system

    
    
    sudo reboot

#### Conclusion

If you have any questions or find any error, please let me know in the
comments. See you!

