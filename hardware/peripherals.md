# Peripherals

## Embedded MultiMediaCard \(eMMC\)

> The eMMC architecture puts the MMC components \(flash memory plus controller\) into a small ball grid array \(BGA\) IC package for use in circuit boards as an embedded non-volatile memory system. Wikipedia

[Embedded MMC](https://en.wikipedia.org/wiki/MultiMediaCard#eMMC)

## Wi-Fi / BlueTooth

> The host processor on the Intel® Edison development board is connected to a Broadcom\* BCM43340 combo chip via UART \(uart0 mapped to /dev/MFD0\) as transport layer and uses additional GPIOs to handle power \(on, reset, etc.\), OOB \( out-of-band\) signaling for UART to support low power mode. ...
>
> Broadcom BCM43341 ... Single Chip, Dual-Band \(2.4 GHz / 5 GHz\) 802.11 g/n MAC/Baseband/Radio with Integrated Bluetooth 4.0, NFC + FM Receiver

* [Broadcom BCM43341](https://www.broadcom.com/products/wireless-connectivity/bluetooth/bcm43341)

### Bluetooth

> Bluetooth is a wireless technology standard for exchanging data over short distances \(using short-wavelength UHF radio waves in the ISM band from 2.4 to 2.485 GHz\[4\]\) from fixed and mobile devices, and building personal area networks \(PANs\). Wikipedia

* [Bluetooth Wikipedia](https://en.wikipedia.org/wiki/Bluetooth)
* [Intel® Edison Board Getting Started with Bluetooth](https://software.intel.com/en-us/articles/intel-edison-board-getting-started-with-bluetooth)
* [Intel® Edison Bluetooth Guide](http://download.intel.com/support/edison/sb/edisonbluetooth_331704004.pdf)

## DF40 Series 70-Pin Connector

> 0.4 mm pitch, 1.5 mm Stacking Height, Slim FPC to Board Connectors

* [DF40 Series](https://www.hirose-connectors.com/connectors/H204SeriesListCompare.aspx?snprm=DF40)

## I2C

### Arduino Breakout Board

```bash
root@edison:~# i2cdetect -y -r 1
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: UU UU UU UU -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
70: -- -- -- -- -- -- -- --
```

### Sparkfun Breakout Board

```bash
root@edison:~# i2cdetect -y -r 1
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
40: -- -- -- -- -- -- -- -- 48 -- -- -- -- -- -- --
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
60: 60 -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
70: -- -- -- -- -- -- -- --
```

