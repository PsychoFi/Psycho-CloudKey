# Psycho-CloudKey
 " We are truly the same, you and I... The world is a more interesting place with people like you in it... " - Psycho Mantis
 
 GOAL: To unlock the ability to add additional functionality to the origiinal Ubiquiti UniFi CloudKey without losing any of the stock functionality. 
       To have my cake and eat it too.
 
 The following is a guide (really no more than just instructions) to enable the UniFi Gen1 CloudKey - hence referred to as UC-CK - to function as a (mostly) normal application server that allows for the installaton and operation of various third-party network services. The stock UC-CK is limited to running just the UniFi Controller software. Like the famous Raspberry Pi, the UC-CK itself is no more than a Single Board Computer powered by an ARM SoC running a Linux Debian based distrobution. With a few small changes, we can unlock the full potential of the UC-CK.
 
### Device Info ###
 The UniFi CloudKey Gen1 is an ARMv7 rev 3 based SBC. The ARM CPU itself is a 4-core 32bit ARMHF capable of running at 1.3ghz but in the UC-CK it is set to operate at 747MHz. UBNT probably limited the UC-CK clock speed to ensure stability and longevity. The cooling is passive and honestly UniFi gear has a reputation for running hot.
# Processor: Mediatek 7623 4-Cores @ 0.7GHz
# Memory: 2017MB
# Storage: Partition 1 - 2.9GB partition that stores the majority of the user file system. [This can fill up fast so plan ahead what you will install.]
          Partition 2 - 11GB partition for the UniFi Controller's storage needs. [This barely gets used as the UniFi Controller doesnt require much space.]
# Expansion: 1 microSDHC slot. Normally this would be used for backing up the UniFi controller but for our purposes it will also work as a work area to perform                                   various tasks. i.e. compiling from source something like Perl or Python. Or for storing a chroot. Or a deboostrap install. 
                              You get the point.
# Network: Ethernet 10/10/1000 w/ PoE support.
# Power: USB-C or PoE
# OS: Debian 8 Jessie with a custom 3.10.x Kernel. It reports as 3.10.20-ubnt-mtk.
# Other: Bluetooth is supported but I have yet to play with any of that functionality.
 
 So an ARMv7 CPU with 2GB of RAM. You might be saying to yourself, "Self. That sounds almost like a Raspberry Pi 3." Well you would be right. Since the UC-CK and    RPi3 both run on a similiar CPU, we can make some small changes to the UC-CK to trick it into allowing us to install software from RPi's APT Repo, as well as standard Debian repos that support ARMHF. Besides the I/O differences, the only thing stopping the UC-CK from running anything we'd want is the old 3.10.x kernel. No headers are available for it so don't expect any Dynamic Kernel Module Support. So no Wireguard and no Docker.
 
 ## Successfully Installed Services ##
 PiHole
 openHAB
 
 ## Pending Success ##
 Home Assistant - Installs but has functionality issues.
 Domocitz - Installs and works OTB but doesn't yet play well with other services. 
 OpenVPN - Install Pending.
 
 ### WARNING  ###
 I'm not responsible for anything you do with your CloudKey. 
 
 ### Suggestions ###
 Memory Card - While you could potentially do everything you need with your UC-CK using the built in storage, it is much easier and pleasant to have a large (32GB) high endurance memory card that you can use for storage intensive tasks like compiling from source. As well as using that space for UniFi backups.
 Thick Paper Clip - If you bork your UC-CK and can't login through SSH to issue the factory reset command, your best option is to kick the UC-CK into Emergency Recovery Mode. From there you can reflash the firmware or try to simple reset it to defaults. 
 
