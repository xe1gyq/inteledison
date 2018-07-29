# Power Management IC

> Edison uses the Texas Instruments \*SNB9024 Power Management Integrated Circuit \(PMIC\). The SNB9024 PMIC is for mobile application processors platforms with high feature integration in order to minimize system board area. It includes subsystems for voltage regulation, A/D conversion, GPIOs, and RTC. The SNB9024 device is controlled and programmed using an I2C interface. There is also a serial voltage ID interface between the SOC and PMIC for handling core voltage rail settings as well as system control signals.
>
> The Intel® Edison board has a known error on all UARTs. When Edison goes into low power sleep, the UART internal FIFO and interface is powered down. Therefore, a two-wire UART \(Rx/Tx\) will lose the first received character whenever Edison is in sleep mode. In order to avoid this condition, when sleep mode is enabled, a four-wire UART \(Rx, Tx, CTS, and RTS\) is required.

## SNB9024 Datasheet Availability

Taken from Intel forums...

> Thank you for contacting TI Semiconductor Support. Unfortunately, since this is a non-distributor item, there is no documentation available for the SNB9024 device \(datasheets, user guides, etc.\).

* [TI SNB9024 power management IC Data Sheet](https://communities.intel.com/thread/58627?start=0&tstart=0)

## Power Consumption

* [Measured power consumption of Intel Edison](https://scivision.co/measured-power-consumption-of-intel-edison/)

