# We Are Bimbo

## We Are Bimbo

## Requirements

* Who We Are!
  * Name your team \(1 minutes\)
  * Choose a slogan \(1 minutes\)
  * Select your Specialists \(2 minutes\)
    * Hardware
    * Embedded Software
    * Cloud
    * Marketing
  * Identify your project name
    * Bimbo Marinela
    * Bimbo Barcel
    * Bimbo Ricolino
* Hardware
  * Laptop
  * Internet Connection
  * Intel Edison 
  * [Grove Indoor Environment Kit for Intel® Edison](https://www.seeedstudio.com/item_detail.html?p_id=2427)
* Challenge
  * Let's integrate all components
  * Deliver data to our "Somos Bimbo" Dashboard by changing "ProjectName" to your "BimboProject"
  * Change the message from ""Hi! I'm Main!" to "BimboProject"

## Hardware Specialist

* [Grove Indoor Environment Kit for Intel® Edison](https://www.seeedstudio.com/item_detail.html?p_id=2427)
  * [Grove - Button](http://wiki.seeedstudio.com/wiki/Grove_-_Button)

    ![](http://wiki.seeedstudio.com/images/c/ca/Button.jpg)

  * [Grove - Light Sensor](http://www.seeedstudio.com/wiki/Grove_-_Light_Sensor)

    ![](https://raw.githubusercontent.com/SeeedDocument/Grove_Light_Sensor/master/images/cover.jpg)

  * [Grove - Relay](https://wiki.seeedstudio.com/wiki/Grove_-_Relay)

    ![](http://wiki.seeedstudio.com/images/3/34/Twig-Relay.jpg)

  * [Grove - LCD RGB Backlight](http://www.seeedstudio.com/wiki/Grove_-_LCD_RGB_Backlight)

    ![](https://raw.githubusercontent.com/SeeedDocument/Grove_LCD_RGB_Backlight/master/images/intro.jpg)

## Embedded Software Specialist

```bash
...
[  OK  ] Reached target Multi-User System.
         Starting Redis Server...
[  OK  ] Started Redis Server.

Poky (Yocto Project Reference Distro) 1.7.3 edison ttyMFD2

edison login:
```

Enter your username as root, no password is required

```bash
edison login: root
root@edison:~#
```

Shutdown usb0 interface

```text
root@edison:~# ifconfig usb0 down
```

Configure your WiFi

```bash
root@edison:~# configure_edison --wifi
```

```bash
Configure Edison: WiFi Connection

Scanning: 1 seconds left

0 :     Rescan for networks
1 :     Exit WiFi Setup
2 :     Manually input a hidden SSID
3 :     Guest
4 :     TP-LINK_2A2C7A
5 :     LabWLAN
6 :     EmployeeHotspot
7 :     TSNOfficeWLAN
8 :     RSN2OfficeWLAN
9 :     IOT-Lab


Enter 0 to rescan for networks.
Enter 1 to exit.
Enter 2 to input a hidden network SSID.
Enter a number between 3 to 9 to choose one of the listed network SSIDs: 6
Is EmployeeHotspot correct? [Y or N]: Y
Please enter the network username: hs_11342026_2
What is the network password?: ********
Initiating connection to EmployeeHotspot. Please wait...
Attempting to enable network access, please check 'wpa_cli status' after a minute to confirm.
Done. Please connect your laptop or PC to the same network as this device and go to http://10.170.32.8 or http://edison.local in your browser.
Warning: SSH is not yet enabled on the wireless interface. To enable SSH access to this device via wireless run configure_edison --password first.
root@edison:~#
```

Go to your working directory

```bash
root@edison:~# ls
IntelEdisonDemos  openstack
root@edison:~# cd IntelEdisonDemos/SomosBimbo/
root@edison:~/IntelEdisonDemos/SomosBimbo# ls
bimbo........       iot101inc.py  requirements.opkg  setup.sh
credentials.config  main.py       requirements.pip
root@edison:~/IntelEdisonDemos/SomosBimbo# python main.py
...
...
/usr/lib/python2.7/site-packages/urllib3/util/ssl_.py:318: SNIMissingWarning: An HTTPS request has been made, but the SNI (Subject Name Indication) extension to TLS is not available on this platform. This may cause the server to present an incorrect TLS certificate, which can cause validation failures. You can upgrade to a newer version of Python to solve this. For more information, see https://urllib3.readthedocs.io/en/latest/security.html#snimissingwarning.
  SNIMissingWarning
/usr/lib/python2.7/site-packages/urllib3/util/ssl_.py:122: InsecurePlatformWarning: A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail. You can upgrade to a newer version of Python to solve this. For more information, see https://urllib3.readthedocs.io/en/latest/security.html#insecureplatformwarning.
  InsecurePlatformWarning
...
...
```

## Cloud Specialist

* Install Telegram 
* Search and start a conversation with your Bot
  * BimboMarinelaBot
  * BimboBarcelBot
  * BimboRicolinoBot
* Interact with your bot using 3 commands
  * /light
  * /message
  * /relay

## Marketing Specialist

* Discuss with your team a possible project to use IoT Technologies
* Present to all the audience 

