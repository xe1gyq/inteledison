# The Setup

## The Setup

> For a more detailed training on Intel Edison Yocto Linux Distribution please follow [The IoT Learning Initiative Embedded Linux](https://theiotlearninginitiative.gitbooks.io/embedded-linux/content/)

Time

* 30 minutes

Requirements

* Laptop
* Internet Connection
* Intel Edison
* [Grove Indoor Environment Kit for Intel® Edison](https://www.seeedstudio.com/item_detail.html?p_id=2427)

## Agenda

* Flashing
  * Installer
  * Serial Clients
* Booting
  * Kernel Version
  * WiFi
  * Open Package Management

## Flashing

### Installer

* Download the specific installer from [Intel Edison Installers](https://software.intel.com/en-us/iot/hardware/edison/downloads)
  * Double click
    * Select "USB drivers installed"
    * Finish
  * Firmware version installed: not detected. Latest available: 201606061707
    * Flash Firmware
      * C:\Intel\Edison\Image\edison-image-20160606
      * Use existing image located at 

### Serial Clients

* Putty @ Windows
  * Session Connection Type: Serial
  * Session Serial Linea: COMx
  * Session Speed: 115200
  * Connection Serial Flow Control: None
* Screen \|\| Minicom @ Linux
  * Session Connection Type: Serial
  * Session Serial Linea: /dev/tttyUSBx
  * Session Speed: 115200
  * Connection Serial Flow Control: None

## Booting

```bash
Poky (Yocto Project Reference Distro) 1.7.3 edison ttyMFD2                      

edison login: root                                                              
Last login: Mon Jun  6 21:33:16 UTC 2016 on ttyMFD2
```

### Kernel Version

Check your kernel version

```bash
root@edison:~# uname -r                                                         
3.10.98-poky-edison+                                                            
root@edison:~#
```

### WiFi

Configure your Edison WiFi network

```bash
root@edison:~# configure_edison --wifi
Configure Edison: WiFi Connection

Scanning: 1 seconds left  

0 :     Rescan for networks
1 :     Exit WiFi Setup
2 :     Manually input a hidden SSID
3 :     CACUNAT
4 :     INFINITUMf89t
5 :     INFINITUM09E845
6 :     17057Abril
7 :     INFINITUMndjj
8 :     INFINITUMfjph


Enter 0 to rescan for networks.
Enter 1 to exit.
Enter 2 to input a hidden network SSID.
Enter a number between 3 to 8 to choose one of the listed network SSIDs: 8
Is INFINITUMfjph correct? [Y or N]: Y
Password must be between 8 and 63 characters.
What is the network password?: **********
Initiating connection to INFINITUMfjph. Please wait...                          
Attempting to enable network access, please check 'wpa_cli status' after a minu.
Done. Please connect your laptop or PC to the same network as this device and g.
Warning: SSH is not yet enabled on the wireless interface. To enable SSH access.
root@edison:~#
```

```bash
root@edison:~# ping -c 2 8.8.8.8                                                
PING 8.8.8.8 (8.8.8.8): 56 data bytes                                           
64 bytes from 8.8.8.8: seq=0 ttl=59 time=151.659 ms                             
64 bytes from 8.8.8.8: seq=1 ttl=59 time=43.713 ms                              

--- 8.8.8.8 ping statistics ---                                                 
2 packets transmitted, 2 packets received, 0% packet loss                       
round-trip min/avg/max = 43.713/97.686/151.659 ms                               
root@edison:~#
```

## Text Editors

### vi

> vi /ˈviːˈaɪ/ is a screen-oriented text editor originally created for the Unix operating system. The portable subset of the behavior of vi and programs based on it, and the ex editor language supported within these programs, is described by \(and thus standardized by\) the Single Unix Specification and POSIX. [Wikipedia Vi](https://en.wikipedia.org/wiki/Vi)

* [Gentoo Vi Learning](https://wiki.gentoo.org/wiki/Vim/Guide)
* [Wikibooks Vi Learning](https://en.wikibooks.org/wiki/Learning_the_vi_Editor)

```bash
    root@board:~# vi hellovi.txt
    Press "i"
    Write some text
    Press "ESC" then ":" then "wq" then "Enter"
    root@board:~#
```

### nano

> nano is a text editor for Unix-like computing systems or operating environments using a command line interface. It emulates the Pico text editor, part of the Pine email client, and also provides additional functionality. In contrast to Pico, nano is licensed under the GNU General Public License \(GPL\). Released as free software by Chris Allegretta in 1999, today nano is part of the GNU Project. [Wikipedia GNU Nano](https://en.wikipedia.org/wiki/GNU_nano)

See if you can install nano command line editor

```bash
    root@board:~# opkg install nano
    Installing nano (2.0.1-r0) on root.
    Downloading http://repo.opkg.net/edison/repo/core2-32/nano_2.0.1-r0_core2-32.ipk.
    Configuring nano.
    root@board:~# nano hello.txt
    Write some text
    Ctrl-X
    root@board:~#
```

```bash
    root@board:~# vi hellonano.txt
    Write some text
    Press "CTRL" + "X" then "Enter" then "Y" then "ENTER"
    root@board:~#
```

## Open Package Management

Update Opkg Repositories

```bash
root@edison:~# opkg update
Downloading http://iotdk.intel.com/repos/1.5/intelgalactic/Packages.
Updated list of available packages in /var/lib/opkg/iotkit.
root@edison:~#
```

Enable a Opkg feed and update package list, we will not upgrade to avoid consuming disk space

```bash
root@edison:~# vi /etc/opkg/base-feeds.conf
```

```bash
src/gz all http://repo.opkg.net/edison/repo/all
src/gz edison http://repo.opkg.net/edison/repo/edison
src/gz core2-32 http://repo.opkg.net/edison/repo/core2-32
```

```bash
root@edison:~# opkg update
Downloading http://repo.opkg.net/edison/repo/all/Packages.gz.
Inflating http://repo.opkg.net/edison/repo/all/Packages.gz.
Updated list of available packages in /var/lib/opkg/all.
Downloading http://repo.opkg.net/edison/repo/edison/Packages.gz.
Inflating http://repo.opkg.net/edison/repo/edison/Packages.gz.
Updated list of available packages in /var/lib/opkg/edison.
Downloading http://repo.opkg.net/edison/repo/core2-32/Packages.gz.
Inflating http://repo.opkg.net/edison/repo/core2-32/Packages.gz.
Updated list of available packages in /var/lib/opkg/core2-32.
Downloading http://iotdk.intel.com/repos/1.5/intelgalactic/Packages.
Updated list of available packages in /var/lib/opkg/iotkit.
root@edison:~#
```

