# SandBox

## SandBox

* [http://www.networkworld.com/article/3061891/intels-edison-board-now-links-up-to-ibms-bluemix-cloud-service.html\#tk.rss\_cloudcomputing](http://www.networkworld.com/article/3061891/intels-edison-board-now-links-up-to-ibms-bluemix-cloud-service.html#tk.rss_cloudcomputing)
* [https://communities.intel.com/docs/DOC-23391](https://communities.intel.com/docs/DOC-23391)
* [https://www.npmjs.com/package/edison-i2c-config](https://www.npmjs.com/package/edison-i2c-config)

  [http://akizukidenshi.com/download/ds/intel/edisonPB331179\_001Edison101Presentation.pdf](http://akizukidenshi.com/download/ds/intel/edisonPB331179_001Edison101Presentation.pdf)

* [http://johnny-five.io/](http://johnny-five.io/)
* [http://www.ros.org/](http://www.ros.org/)
* [http://www.aaeon.com/en/p/3-and-half-inch-sbc-aiot-x1000/](http://www.aaeon.com/en/p/3-and-half-inch-sbc-aiot-x1000/)
* [http://linuxgizmos.com/first-quark-based-smarc-computer-on-module-runs-on-2-watts/](http://linuxgizmos.com/first-quark-based-smarc-computer-on-module-runs-on-2-watts/)
* [http://blogs.intel.com/evangelists/2015/10/02/intel-microsoft-new-experiences/?utm\_source=evangelists.intel.com&utm\_medium=referral&utm\_campaign=Caffelli Intel Evangelists](http://blogs.intel.com/evangelists/2015/10/02/intel-microsoft-new-experiences/?utm_source=evangelists.intel.com&utm_medium=referral&utm_campaign=Caffelli%20Intel%20Evangelists)

how we structure this training?

* Hardware
* OS Specific
  * Linux
  * Other

    [https://0xax.gitbooks.io/linux-insides/content/Concepts/cpumask.html](https://0xax.gitbooks.io/linux-insides/content/Concepts/cpumask.html)

[http://download.intel.com/support/edison/sb/edisonbsp\_ug\_331188007.pdf](http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf) [https://hayestech.files.wordpress.com/2015/01/intel-edison-bsd.pdf](https://hayestech.files.wordpress.com/2015/01/intel-edison-bsd.pdf)

### Process A

[https://downloadcenter.intel.com/download/24357](https://downloadcenter.intel.com/download/24357) File name: edison-src-weekly-68.tgz

```text
xe1gyq@host:~# sudo apt-get install build-essential git diffstat gawk chrpath texinfo libtool gcc-multilib dfu-util screen u-boot-tools

xe1gyq@host:~$ tar xvf edison-src-weekly-68.tgz
xe1gyq@host:~$ ls edison-src
arduino  broadcom_cws  device-software  mw
xe1gyq@host:~$ ./device-software/setup.sh
xe1gyq@host:~$ source poky/oe-init-build-env
xe1gyq@host:~$ ../meta-intel-edison/utils/flash/postBuild.sh
```

[https://scratchbuffer.wordpress.com/2015/09/01/yocto-linux-image-build-for-intel-edison-simple-and-easy/](https://scratchbuffer.wordpress.com/2015/09/01/yocto-linux-image-build-for-intel-edison-simple-and-easy/) [https://wiki.lsr.ei.tum.de/nst/documentation/inteledison](https://wiki.lsr.ei.tum.de/nst/documentation/inteledison)

### Process B

[http://www.embarcados.com.br/intel-edison-yocto-como-construir-sua-propria-distribuicao-linux-embarcado/](http://www.embarcados.com.br/intel-edison-yocto-como-construir-sua-propria-distribuicao-linux-embarcado/) [http://www.embarcados.com.br/raspberry-pi-qt5-yocto-parte-1/](http://www.embarcados.com.br/raspberry-pi-qt5-yocto-parte-1/)

```text
user@host:~$ 
user@host:~$ tar xvf edison-src-weekly-68b.tgz
user@host:~$ cd edison-src
user@host:~$ make setup
user@host:~$ cd out/linux64
user@host:~$ source poky/oe-init-build-env
user@host:~$ bitbake edison-image
user@host:~$ cd out/linux64/build/tmp/deploy/images/edison
user@host:~$ cd meta-intel-edison/utils/flash

edison-src/build/tmp/deploy/images/edison/edison-image-edison.hddimg
```

#### What is it create-debian-image.sh

```text
user@host:~$ edison-src/meta-intel-edison/utils
```

xe1gyq@jessie:~/Downloads/edison-src$ ls arduino bbcache broadcom\_cws device-software Makefile meta-arduino meta-intel-edison mw out pub

xe1gyq@jessie:~/Downloads/edison-src/out/linux64$ ls build poky

```text
xe1gyq@jessie:~/Downloads/edison-src$ ls
arduino  bbcache  broadcom_cws  device-software  Makefile  meta-intel-edison  mw  out  pub
xe1gyq@jessie:~/Downloads/edison-src$ make
Please run "make setup" first
Makefile:106: recipe for target '_check_setup_was_done' failed
make: *** [_check_setup_was_done] Error 1
xe1gyq@jessie:~/Downloads/edison-src$ make setup
Setup buildenv for SDK host linux64
./meta-intel-edison/setup.sh  --dl_dir=/home/xe1gyq/Downloads/edison-src/bbcache/downloads --sstate_dir=/home/xe1gyq/Downloads/edison-src/bbcache/sstate-cache --build_dir=/home/xe1gyq/Downloads/edison-src/out/linux64 --build_name=custom_build_xe1gyq@20151001233406 --sdk_host=linux64
We are building in external mode
Cloning into bare repository 'poky-mirror.git'...
remote: Counting objects: 288590, done.
remote: Compressing objects: 100% (71063/71063), done.
remote: Total 288590 (delta 212301), reused 288186 (delta 211897)
Receiving objects: 100% (288590/288590), 114.57 MiB | 581.00 KiB/s, done.
Resolving deltas: 100% (212301/212301), done.
Checking connectivity... done.
Cloning into bare repository 'meta-mingw-mirror.git'...
remote: Counting objects: 256, done.
remote: Compressing objects: 100% (191/191), done.
remote: Total 256 (delta 98), reused 203 (delta 45)
Receiving objects: 100% (256/256), 62.01 KiB | 0 bytes/s, done.
Resolving deltas: 100% (98/98), done.
Checking connectivity... done.
Cloning into bare repository 'meta-darwin-mirror.git'...
remote: Counting objects: 577, done.
remote: Compressing objects: 100% (329/329), done.
remote: Total 577 (delta 244), reused 522 (delta 189)
Receiving objects: 100% (577/577), 6.90 MiB | 606.00 KiB/s, done.
Resolving deltas: 100% (244/244), done.
Checking connectivity... done.
Cloning into bare repository 'meta-intel-iot-middleware-mirror.git'...
remote: Counting objects: 1008, done.
remote: Compressing objects: 100% (534/534), done.
remote: Total 1008 (delta 506), reused 880 (delta 380)
Receiving objects: 100% (1008/1008), 5.60 MiB | 603.00 KiB/s, done.
Resolving deltas: 100% (506/506), done.
Checking connectivity... done.
Cloning Poky in the /home/xe1gyq/Downloads/edison-src/out/linux64/poky directory
Cloning into 'poky'...
done.
Checking out files: 100% (5016/5016), done.
Note: checking out 'yocto-1.7.2'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 29812e6... busybox: unbreak tar of uncompressed files
Cloning Mingw layer to /home/xe1gyq/Downloads/edison-src/out/linux64/poky/meta-mingw directory from local cache
Cloning into 'meta-mingw'...
done.
Cloning Darwin layer to /home/xe1gyq/Downloads/edison-src/out/linux64/poky/meta-darwin directory from local cache
Cloning into 'meta-darwin'...
done.
Note: checking out '29b5ff31cee24e796f2eb2d2fd1269e3e92c831c'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at 29b5ff3... gcc-runtime: Don't pollute global export namespace
Cloning meta-intel-iot-middleware layer to /home/xe1gyq/Downloads/edison-src/out/linux64/poky/meta-intel-iot-middleware directory from local cache
Cloning into 'meta-intel-iot-middleware'...
done.
Note: checking out 'c6d681475e76107e6c04c5f7a06034dc9e772d1e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b new_branch_name

HEAD is now at c6d6814... upm: Update to 0.3.1
Cloning meta-arduino layer to /home/xe1gyq/Downloads/edison-src directory from GitHub.com/01org/meta-arduino
Cloning into 'meta-arduino'...
remote: Counting objects: 72, done.
remote: Total 72 (delta 0), reused 0 (delta 0), pack-reused 72
Unpacking objects: 100% (72/72), done.
Checking connectivity... done.
Already on '1.6.x'
Your branch is up-to-date with 'origin/1.6.x'.
Applying patch on poky
Initializing yocto build environment
Setting up yocto configuration file (in build/conf/local.conf)
** Success **
SDK will be generated for linux64 host
Now run these two commands to setup and build the flashable image:
cd /home/xe1gyq/Downloads/edison-src/out/linux64
source poky/oe-init-build-env
bitbake edison-image
*************
xe1gyq@jessie:~/Downloads/edison-src$ cd /home/xe1gyq/Downloads/edison-src/out/linux64
xe1gyq@jessie:~/Downloads/edison-src/out/linux64$ source poky/oe-init-build-env

### Shell environment set up for builds. ###

You can now run 'bitbake <target>'

Common targets are:
    core-image-minimal
    core-image-sato
    meta-toolchain
    adt-installer
    meta-ide-support

You can also run generated qemu images with a command like 'runqemu qemux86'
xe1gyq@jessie:~/Downloads/edison-src/out/linux64/build$ bitbake edison-image
WARNING: Host distribution "Debian-8.1" has not been validated with this version of the build system; you may possibly experience unexpected failures. It is recommended that you use a tested distribution.
Parsing recipes: 100% |###################################################################################| Time: 00:02:01
Parsing of 959 .bb files complete (0 cached, 959 parsed). 1364 targets, 117 skipped, 0 masked, 0 errors.
NOTE: Resolving any missing task queue dependencies

Build Configuration:
BB_VERSION        = "1.24.0"
BUILD_SYS         = "i686-linux"
NATIVELSBSTRING   = "Debian-8.1"
TARGET_SYS        = "i586-poky-linux"
MACHINE           = "edison"
DISTRO            = "poky-edison"
DISTRO_VERSION    = "1.7.2"
TUNE_FEATURES     = "m32 core2"
TARGET_FPU        = ""
meta              
meta-yocto        
meta-yocto-bsp    = "(detachedfromyocto-1.7.2):29812e61736a95f1de64b3e9ebbb9c646ebd28dd"
meta-intel-edison-bsp 
meta-intel-edison-distro = "<unknown>:<unknown>"
meta-intel-iot-middleware = "(detachedfromc6d6814):c6d681475e76107e6c04c5f7a06034dc9e772d1e"
meta-intel-arduino = "<unknown>:<unknown>"
meta-arduino      = "1.6.x:541b127163acb243109f07141bf249da2ecdcd9a"

NOTE: Preparing runqueue
NOTE: Executing SetScene Tasks
NOTE: Executing RunQueue Tasks
WARNING: Failed to fetch URL http://zlib.net/pigz/pigz-2.3.1.tar.gz, attempting MIRRORS if available
WARNING: Failed to fetch URL ftp://ftp.debian.org/debian/pool/main/b/base-passwd/base-passwd_3.5.29.tar.gz, attempting MIRRORS if available
WARNING: Failed to fetch URL http://downloads.sourceforge.net/project/libpng/libpng16/1.6.13/libpng-1.6.13.tar.xz, attempting MIRRORS if available
NOTE: validating kernel config, see log.do_kernel_configcheck for details
WARNING: Failed to fetch URL http://www.apache.org/dist/apr/apr-1.5.1.tar.bz2, attempting MIRRORS if available
WARNING: Failed to fetch URL http://www.apache.org/dist/apr/apr-util-1.5.3.tar.gz, attempting MIRRORS if available
WARNING: QA Issue: bluez5: configure was passed unrecognised options: --with-systemdunitdir [unknown-configure-option]
WARNING: Failed to fetch URL http://www.apache.org/dist/subversion/subversion-1.8.9.tar.bz2, attempting MIRRORS if available
WARNING: Failed to fetch URL ftp://ftp.debian.org/debian/pool/main/n/netbase/netbase_5.2.tar.gz, attempting MIRRORS if available
WARNING: Failed to fetch URL ftp://ftp.uni-erlangen.de/pub/Linux/LOCAL/dosfstools/dosfstools-2.11.src.tar.gz, attempting MIRRORS if available
WARNING: busybox: alternative target (/etc/syslog.conf or /etc/syslog.conf.busybox) does not exist, skipping...
WARNING: busybox: NOT adding alternative provide /etc/syslog.conf: /etc/syslog.conf.busybox does not exist
WARNING: alt_link == alt_target: /etc/syslog.conf == /etc/syslog.conf
WARNING: Failed to fetch URL ftp://ftp.debian.org/debian/pool/main/n/net-tools/net-tools_1.60-25.diff.gz;apply=no;name=patch, attempting MIRRORS if available
WARNING: Failed to fetch URL http://dl.lm-sensors.org/i2c-tools/releases/i2c-tools-3.1.1.tar.bz2, attempting MIRRORS if available
WARNING: Failed to fetch URL ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_4.87.tar.bz2, attempting MIRRORS if available
WARNING: Failed to fetch URL ftp://ftp.debian.org/debian/pool/main/d/dpkg/dpkg_1.17.4.tar.xz, attempting MIRRORS if available
WARNING: Failed to fetch URL http://ftp.de.debian.org/debian/pool/main/m/mklibs/mklibs_0.1.39.tar.xz, attempting MIRRORS if available
WARNING: Failed to fetch URL ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-3.01a20.tar.bz2, attempting MIRRORS if available
WARNING: QA Issue: battery-voltage rdepends on libsystemd, but it isn't a build dependency? [build-deps]
WARNING: QA Issue: xdk-daemon requires libdns_sd.so, but no providers in its RDEPENDS [file-rdeps]
WARNING: QA Issue: iotkit-agent requires /bin/bash, but no providers in its RDEPENDS [file-rdeps]
WARNING: QA Issue: pulseaudio-module-console-kit rdepends on consolekit, but it isn't a build dependency? [build-deps]
WARNING: QA Issue: post-install requires /bin/bash, but no providers in its RDEPENDS [file-rdeps]
    WARNING: QA Issue: systemd-kernel-install requires /bin/bash, but no providers in its RDEPENDS [file-rdeps]
WARNING: QA Issue: wpa-supplicant-passphrase rdepends on libcrypto, but it isn't a build dependency? [build-deps]
WARNING: QA Issue: wpa-supplicant rdepends on libcrypto, but it isn't a build dependency? [build-deps]
WARNING: QA Issue: wpa-supplicant rdepends on libssl, but it isn't a build dependency? [build-deps]
NOTE: Tasks Summary: Attempted 3757 tasks of which 13 didn't need to be rerun and all succeeded.

Summary: There were 28 WARNING messages shown.
```

### Links

* [http://www.instructables.com/id/Securing-IoT-applications-built-on-Intel-Galileo-a/](http://www.instructables.com/id/Securing-IoT-applications-built-on-Intel-Galileo-a/)
* [https://communities.intel.com/docs/DOC-23391](https://communities.intel.com/docs/DOC-23391)
* [https://software.intel.com/en-us/articles/intel-edison-developer-resources](https://software.intel.com/en-us/articles/intel-edison-developer-resources)
* [http://download.intel.com/support/edison/sb/edisonbsp\_ug\_331188007.pdf](http://download.intel.com/support/edison/sb/edisonbsp_ug_331188007.pdf)
* [http://drejkim.com/blog/2014/11/22/building-an-edison-image-and-changing-the-root-partition-size/](http://drejkim.com/blog/2014/11/22/building-an-edison-image-and-changing-the-root-partition-size/)
* [https://hayestech.wordpress.com/2015/01/26/building-custom-intel-edison-images/](https://hayestech.wordpress.com/2015/01/26/building-custom-intel-edison-images/)
* [http://www.yoctoproject.org/docs/1.1/yocto-project-qs/yocto-project-qs.html](http://www.yoctoproject.org/docs/1.1/yocto-project-qs/yocto-project-qs.html)
* [http://edplay.weebly.com/how-to/building-linux-for-intel-edison](http://edplay.weebly.com/how-to/building-linux-for-intel-edison)
* [https://scratchbuffer.wordpress.com/2015/07/13/my-personal-guide-to-intel-edison/](https://scratchbuffer.wordpress.com/2015/07/13/my-personal-guide-to-intel-edison/)

## Extra

```bash
xe1gyq@jessie:~/Flash/EdisonSource$ ls
edison_dnx_fwr.bin          edison_ifwi-dbg-04.bin         flashall.bat
edison_dnx_osr.bin          edison_ifwi-dbg-04-dfu.bin     flashall.sh
edison_ifwi-dbg-00.bin      edison_ifwi-dbg-05.bin         FlashEdison.json
edison_ifwi-dbg-00-dfu.bin  edison_ifwi-dbg-05-dfu.bin     helper
edison_ifwi-dbg-01.bin      edison_ifwi-dbg-06.bin         ota_update.scr
edison_ifwi-dbg-01-dfu.bin  edison_ifwi-dbg-06-dfu.bin     package-list.txt
edison_ifwi-dbg-02.bin      edison-image-edison.ext4       u-boot-edison.bin
edison_ifwi-dbg-02-dfu.bin  edison-image-edison.hddimg     u-boot-edison.img
edison_ifwi-dbg-03.bin      edison-iotdk-image-280915.zip  u-boot-envs
edison_ifwi-dbg-03-dfu.bin  filter-dfu-out.js              zip
```

[http://www.wolfram.com/intel-edison/](http://www.wolfram.com/intel-edison/) [https://downloadcenter.intel.com/search?keyword=edison](https://downloadcenter.intel.com/search?keyword=edison)

Setup

* Configure Wireless LAN

```text
apt-get update
apt-get install git
apt-get usb-modeswitch
apt-get install build-essential g++ automake autoconf gnu-standards autoconf-doc libtool gettext autoconf-archive
apt-get install wvdial
apt-get install bzip2
```

#### Links

* [https://github.com/wifidog/wifidog-auth/blob/master/INSTALL](https://github.com/wifidog/wifidog-auth/blob/master/INSTALL)
* [http://dev.wifidog.org/wiki/doc/install/debian](http://dev.wifidog.org/wiki/doc/install/debian)

### 3G Modem

#### Debian Jessie x86

```text
xe1gyq@jessie:~$ lsusb
Bus 001 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 006 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 007 Device 003: ID 1bbb:011e T & A Mobile Phones 

[  422.300054] usb 7-3: new high-speed USB device number 2 using ehci-pci
[  422.434543] usb 7-3: New USB device found, idVendor=1bbb, idProduct=f017
[  422.434547] usb 7-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  422.434550] usb 7-3: Product: Mobile Broad Band
[  422.434552] usb 7-3: Manufacturer: USBModem
[  422.786231] usb-storage 7-3:1.0: USB Mass Storage device detected
[  422.786448] scsi6 : usb-storage 7-3:1.0
[  422.786541] usb-storage 7-3:1.1: USB Mass Storage device detected
[  422.786587] scsi7 : usb-storage 7-3:1.1
[  422.786674] usbcore: registered new interface driver usb-storage
[  423.221714] usb 7-3: USB disconnect, device number 2
[  426.436043] usb 7-3: new high-speed USB device number 3 using ehci-pci
[  426.570781] usb 7-3: New USB device found, idVendor=1bbb, idProduct=011e
[  426.570785] usb 7-3: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  426.570788] usb 7-3: Product: Mobile Broad Band
[  426.570791] usb 7-3: Manufacturer: USBModem
[  426.574356] usb-storage 7-3:1.2: USB Mass Storage device detected
[  426.574424] scsi8 : usb-storage 7-3:1.2
[  426.679993] usbcore: registered new interface driver usbserial
[  426.680219] usbcore: registered new interface driver usbserial_generic
[  426.680236] usbserial: USB Serial support registered for generic
[  426.696159] usbcore: registered new interface driver option
[  426.696178] usbserial: USB Serial support registered for GSM modem (1-port)
[  426.696297] option 7-3:1.0: GSM modem (1-port) converter detected
[  426.696397] usb 7-3: GSM modem (1-port) converter now attached to ttyUSB0
[  426.696437] option 7-3:1.1: GSM modem (1-port) converter detected
[  426.696512] usb 7-3: GSM modem (1-port) converter now attached to ttyUSB1
[  426.696554] option 7-3:1.3: GSM modem (1-port) converter detected
[  426.696635] usb 7-3: GSM modem (1-port) converter now attached to ttyUSB2
[  426.714412] usbcore: registered new interface driver cdc_wdm
[  426.767392] qmi_wwan 7-3:1.4: cdc-wdm0: USB WDM device
[  426.767604] qmi_wwan 7-3:1.4 wwan0: register 'qmi_wwan' at usb-0000:00:1d.7-3, WWAN/QMI device, 9a:a4:5e:7f:54:07
[  426.767630] usbcore: registered new interface driver qmi_wwan
[  427.573530] scsi 8:0:0:0: Direct-Access     USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
[  427.574461] sd 8:0:0:0: Attached scsi generic sg1 type 0
[  427.577271] sd 8:0:0:0: [sdb] Attached SCSI removable disk

[ 7259.343698] usb 7-3: GSM modem (1-port) converter now attached to ttyUSB6
```

\[ 7259.345290\] qmi\_wwan 7-3:1.4: cdc-wdm0: USB WDM device \[ 7259.345547\] qmi\_wwan 7-3:1.4 wwan0: register 'qmi\_wwan' at usb-0000:00:1d.7-3, WWAN/QMI device, 9a:a4:5e:7f:54:07 \[ 7260.341716\] scsi 11:0:0:0: Direct-Access USBModem MMC Storage 2.31 PQ: 0 ANSI: 2 \[ 7260.342729\] sd 11:0:0:0: Attached scsi generic sg1 type 0 \[ 7260.346072\] sd 11:0:0:0: \[sdb\] Attached SCSI removable disk \[ 7520.623662\] wlan0: deauthenticating from f8:01:13:a8:2b:40 by local choice \(Reason: 3=DEAUTH\_LEAVING\) \[ 7520.669720\] cfg80211: Calling CRDA to update world regulatory domain \[ 7520.731811\] cfg80211: World regulatory domain updated: \[ 7520.731815\] cfg80211: DFS Master region: unset \[ 7520.731817\] cfg80211: \(start\_freq - end\_freq @ bandwidth\), \(max\_antenna\_gain, max\_eirp\), \(dfs\_cac\_time\) \[ 7520.731819\] cfg80211: \(2402000 KHz - 2472000 KHz @ 40000 KHz\), \(N/A, 2000 mBm\), \(N/A\) \[ 7520.731821\] cfg80211: \(2457000 KHz - 2482000 KHz @ 40000 KHz\), \(N/A, 2000 mBm\), \(N/A\) \[ 7520.731823\] cfg80211: \(2474000 KHz - 2494000 KHz @ 20000 KHz\), \(N/A, 2000 mBm\), \(N/A\) \[ 7520.731825\] cfg80211: \(5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO\), \(N/A, 2000 mBm\), \(N/A\) \[ 7520.731828\] cfg80211: \(5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO\), \(N/A, 2000 mBm\), \(0 s\) \[ 7520.731829\] cfg80211: \(5490000 KHz - 5730000 KHz @ 160000 KHz\), \(N/A, 2000 mBm\), \(0 s\) \[ 7520.731831\] cfg80211: \(5735000 KHz - 5835000 KHz @ 80000 KHz\), \(N/A, 2000 mBm\), \(N/A\) \[ 7520.731833\] cfg80211: \(57240000 KHz - 63720000 KHz @ 2160000 KHz\), \(N/A, 0 mBm\), \(N/A\)

```text
lsusb
Bus 007 Device 006: ID 1bbb:011e T & A Mobile Phones 

usb-devices
T:  Bus=07 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1bbb ProdID=011e Rev=00.00
S:  Manufacturer=USBModem
S:  Product=Mobile Broad Band
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan
```

#### Debian Whezzy Intel Edison

```text
[  200.177110] usb 1-1.2: new high-speed USB device number 4 using dwc3-host
[  200.203207] usb 1-1.2: New USB device found, idVendor=1bbb, idProduct=f017
[  200.203240] usb 1-1.2: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[  200.203261] usb 1-1.2: Product: Mobile Broad Band
[  200.203279] usb 1-1.2: Manufacturer: USBModem
[  200.207677] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[  200.208398] scsi0 : usb-storage 1-1.2:1.0
[  200.209556] usb-storage 1-1.2:1.1: USB Mass Storage device detected
[  200.209970] scsi1 : usb-storage 1-1.2:1.1
[  201.208324] scsi 1:0:0:0: CD-ROM            USBModem MMC Storage      2.31 PQ: 0 ANSI: 2
[  201.210949] sr0: scsi-1 drive
[  201.210973] cdrom: Uniform CD-ROM driver Revision: 3.20
[  201.212360] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  201.213405] sr 1:0:0:0: Attached scsi generic sg0 type 5

apt-get install ppp
wget "http://www.sakis3g.com/downloads/sakis3g.tar.gz" -O sakis3g.tar.gz
tar -xzvf sakis3g.tar.gz
chmod +x sakis3g
./sakis3g --interactive

root@ubilinux:~# modprobe usbserial vendor=0x1bbb product=0x0017
root@ubilinux:~# lsmod
Module                  Size  Used by
ftdi_sio               40121  0 
uvcvideo               71516  0 
videobuf2_vmalloc      13003  1 uvcvideo
videobuf2_memops       13001  1 videobuf2_vmalloc
videobuf2_core         37707  1 uvcvideo
usb_f_acm              14335  1 
u_serial               18582  6 usb_f_acm
g_multi                70813  0 
libcomposite           39245  2 usb_f_acm,g_multi
bcm_bt_lpm             13676  0 
bcm4334x              578947  0 
gedit /etc/udev/rules.d/50-myrules.rules
ATTRS{idVendor}=="1bbb",ATTRS{idProduct}=="0017", RUN+="/sbin/modprobe usbserial vendor=0x1bbb product=0x0017"

cat /sys/kernel/debug/usb/devices | more
T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1bbb ProdID=f017 Rev= 0.00
S:  Manufacturer=USBModem
S:  Product=Mobile Broad Band
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms


http://www.draisberghof.de/usb_modeswitch/

nano /lib/udev/rules.d/40-usb_modeswitch.rules
# Alcatel
ATTRS{idVendor}=="1bbb", ATTRS{idProduct}=="011e", RUN+="usb_modeswitch '%b/%k'"
```

nano /etc/usb\_modeswitch.d/1bbb\:f017

```text
# Alcatel Onetouch 3G module
#
DefaultVendor=0x1bbb
DefaultProduct=0xf017
TargetVendor=0x1bbb
#TargetProduct=0xf017
TargetProduct=0x0000
#MessageContent="55534243123456782400000080000685000000240000000000000000000000"
CheckSuccess=20
MessageContent="55534243123456788000000080000606f50402527000000000000000000000"
```

* [http://www.sakis3g.com/](http://www.sakis3g.com/)
* [https://wiki.archlinux.org/index.php/USB\_3G\_Modem](https://wiki.archlinux.org/index.php/USB_3G_Modem)
* [http://www.draisberghof.de/usb\_modeswitch/bb/viewtopic.php?f=4&t=1935](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?f=4&t=1935)
* [http://www.draisberghof.de/usb\_modeswitch/bb/viewtopic.php?t=952](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=952)
* [https://lawrencematthew.wordpress.com/2013/08/07/connect-raspberry-pi-to-a-3g-network-automatically-during-its-boot/](https://lawrencematthew.wordpress.com/2013/08/07/connect-raspberry-pi-to-a-3g-network-automatically-during-its-boot/)

### Issues

```text
root@ubilinux:~/wifidog-auth# apt-get install postgresql-8.1
E: Package 'postgresql-8.1' has no installation candidate
```

