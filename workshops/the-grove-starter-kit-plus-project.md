# The Grove Starter Kit Plus Project

## The Grove Starter Kit Plus Workshop

Time

* 90 minutes

Requirements

* Laptop
* Internet Connection
* Intel Edison
* [Grove Indoor Environment Kit for Intel® Edison](https://www.seeedstudio.com/item_detail.html?p_id=2427)
  * [Grove – Button](http://www.seeedstudio.com/wiki/Grove_-_Button)

    ![](http://www.seeedstudio.com/wiki/images/thumb/c/ca/Button.jpg/300px-Button.jpg)

  * [Grove - Touch Sensor](http://www.seeedstudio.com/wiki/Grove_-_Touch_Sensor)
  * [Grove - Buzzer](http://www.seeedstudio.com/wiki/Grove_-_Buzzer)

    ![](http://www.seeedstudio.com/wiki/images/thumb/e/ed/Buzzer1.jpg/400px-Buzzer1.jpg)

  * [Grove - Rotary Angle Sensor\(P\)](http://www.seeedstudio.com/wiki/Grove_-_Rotary_Angle_Sensor)

    ![](http://www.seeedstudio.com/wiki/images/thumb/a/af/Grove_-_Rotary_Angle_Sensor_%28P%29.jpg/400px-Grove_-_Rotary_Angle_Sensor_%28P%29.jpg)

  * [Grove - Light Sensor](http://www.seeedstudio.com/wiki/Grove_-_Light_Sensor)

    ![](http://www.seeedstudio.com/wiki/images/thumb/1/1c/Twig-Light.jpg/500px-Twig-Light.jpg)

  * [Grove - Temperature Sensor](http://www.seeedstudio.com/wiki/Grove_-_Temperature_Sensor)

    ![](http://www.seeedstudio.com/wiki/images/thumb/b/b0/Temperature1.jpg/400px-Temperature1.jpg)
* [Grove - LCD RGB Backlight](http://www.seeedstudio.com/wiki/Grove_-_LCD_RGB_Backlight)

  ![](http://www.seeedstudio.com/wiki/images/thumb/0/03/Serial_LEC_RGB_Backlight_Lcd.jpg/500px-Serial_LEC_RGB_Backlight_Lcd.jpg)

## Agenda

* [Grove – Button](http://www.seeedstudio.com/wiki/Grove_-_Button)
* [Grove - Touch Sensor](http://www.seeedstudio.com/wiki/Grove_-_Touch_Sensor)
* [Grove - Buzzer](http://www.seeedstudio.com/wiki/Grove_-_Buzzer)
* [Grove - Rotary Angle Sensor\(P\)](http://www.seeedstudio.com/wiki/Grove_-_Rotary_Angle_Sensor)
* [Grove - Light Sensor](http://www.seeedstudio.com/wiki/Grove_-_Light_Sensor)
* [Grove - Temperature Sensor](http://www.seeedstudio.com/wiki/Grove_-_Temperature_Sensor)
* [Grove - LCD RGB Backlight](http://www.seeedstudio.com/wiki/Grove_-_LCD_RGB_Backlight)

## Grove Starter Kit Plus

### Grove – Button

> Author: Sarah Knepper [sarah.knepper@intel.com](mailto:sarah.knepper@intel.com) Copyright \(c\) 2014 Intel Corporation.

* [UPM Python Grove Button](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/grovebutton.py)

```bash
root@edison:~# vi button.py
```

```python
import time
import pyupm_grove as grove

# Create the button object using GPIO pin 2
button = grove.GroveButton(2)

# Read the input and print, waiting one second between readings
while 1:
    print button.name(), ' value is ', button.value()
    time.sleep(1)

# Delete the button object
del button
```

```bash
root@edison:~# python button.py
```

### Grove - Touch Sensor

> Author: Sarah Knepper [sarah.knepper@intel.com](mailto:sarah.knepper@intel.com) Copyright \(c\) 2014 Intel Corporation.

* [UPM Python Grove Button](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/grovebutton.py)

```bash
root@edison:~# vi touch.py
```

```python
import time
import pyupm_grove as grove

# Create the button object using GPIO pin 3
touch = grove.GroveButton(3)

# Read the input and print, waiting one second between readings
while 1:
    print touch.name(), ' value is ', touch.value()
    time.sleep(1)

# Delete the touch object
del touch
```

```bash
root@edison:~# python touch.py
```

### Grove - Buzzer

> Author: Sarah Knepper [sarah.knepper@intel.com](mailto:sarah.knepper@intel.com) Copyright \(c\) 2015 Intel Corporation.

* [UPM Python Grove Buzzer](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/buzzer.py)

```bash
root@edison:~# vi buzzer.py
```

```python
import time
import pyupm_buzzer as upmBuzzer

# Create the buzzer object using GPIO pin 4
buzzer = upmBuzzer.Buzzer(4)

chords = [upmBuzzer.DO, upmBuzzer.RE, upmBuzzer.MI, upmBuzzer.FA, 
          upmBuzzer.SOL, upmBuzzer.LA, upmBuzzer.SI, upmBuzzer.DO, 
          upmBuzzer.SI];

# Print sensor name
print buzzer.name()

# Play sound (DO, RE, MI, etc.), pausing for 0.1 seconds between notes
for chord_ind in range (0,7):
    # play each note for one second
    print buzzer.playSound(chords[chord_ind], 1000000)
    time.sleep(0.1)

print "exiting application"

# Delete the buzzer object
del buzzer
```

```bash
root@edison:~# python buzzer.py
```

### Grove - Rotary Angle Sensor\(P\)

> Author: Mihai Tudor Panu [mihai.tudor.panu@intel.com](mailto:mihai.tudor.panu@intel.com) Copyright \(c\) 2014 Intel Corporation.

* [UPM Python Rotary Angle Sensor\(P\)](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/groverotary.py)

```bash
root@edison:~# vi .py
```

```python
from time import sleep
import pyupm_grove as grove

# New knob on AIO pin 0
knob = grove.GroveRotary(0)

# Loop indefinitely
while True:

    # Read values
    abs = knob.abs_value()
    absdeg = knob.abs_deg()
    absrad = knob.abs_rad()

    rel = knob.rel_value()
    reldeg = knob.rel_deg()
    relrad = knob.rel_rad()

    print "Abs values: %4d" % int(abs) , " raw %4d" % int(absdeg), "deg = %5.2f" % absrad , " rad ",
    print "Rel values: %4d" % int(rel) , " raw %4d" % int(reldeg), "deg = %5.2f" % relrad , " rad"

    # Sleep for 2.5 s
    sleep(2.5)
```

```bash
root@edison:~# python .py
```

### Grove - Light Sensor

> Author: Sarah Knepper [sarah.knepper@intel.com](mailto:sarah.knepper@intel.com) Copyright \(c\) 2014 Intel Corporation.

* [UPM Python Grove Light](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/grovelight.py)

```bash
root@edison:~# vi light.py
```

```python
import time
import pyupm_grove as grove

# Create the light sensor object using AIO pin 1
light = grove.GroveLight(1)

# Read the input and print both the raw value and a rough lux value,
# waiting one second between readings
while 1:
    print light.name() + " raw value is %d" % light.raw_value() + \
        ", which is roughly %d" % light.value() + " lux";
    time.sleep(1)

# Delete the light sensor object
del light
```

```bash
root@edison:~# python light.py
```

### Grove - Temperature Sensor

> Author: Brendan Le Foll [brendan.le.foll@intel.com](mailto:brendan.le.foll@intel.com) Contributions: Sarah Knepper [sarah.knepper@intel.com](mailto:sarah.knepper@intel.com) Copyright \(c\) 2014 Intel Corporation.

* [UPM Python Grove Temp](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/grovetemp.py)

```bash
root@edison:~# vi temperature.py
```

```python
import time
import pyupm_grove as grove

# Create the temperature sensor object using AIO pin 2
temp = grove.GroveTemp(2)
print temp.name()

# Read the temperature ten times, printing both the Celsius and
# equivalent Fahrenheit temperature, waiting one second between readings
for i in range(0, 10):
    celsius = temp.value()
    fahrenheit = celsius * 9.0/5.0 + 32.0;
    print "%d degrees Celsius, or %d degrees Fahrenheit" \
        % (celsius, fahrenheit)
    time.sleep(1)

# Delete the temperature sensor object
del temp
```

```bash
root@edison:~# python temperature.py
```

### Grove - LCD RGB Backlight

> Author: Brendan Le Foll [brendan.le.foll@intel.com](mailto:brendan.le.foll@intel.com) Copyright \(c\) 2014 Intel Corporation.

* [UPM Python Grove LCD RGB Backlight](https://github.com/intel-iot-devkit/upm/blob/master/examples/python/jhd1313m1-lcd.py)

```bash
root@edison:~# vi lcd.py
```

```python
import pyupm_i2clcd as lcd

# Initialize Jhd1313m1 at 0x3E (LCD_ADDRESS) and 0x62 (RGB_ADDRESS) 
myLcd = lcd.Jhd1313m1(0, 0x3E, 0x62)

myLcd.setCursor(0,0)
# RGB Blue
#myLcd.setColor(53, 39, 249)

# RGB Red
myLcd.setColor(255, 0, 0)

while True:
    myLcd.write('Hello World')
    myLcd.setCursor(1,2)
    myLcd.write('Hello World')
```

```bash
root@edison:~# python lcd.py
```

### Challenge

Create an application using all components...

