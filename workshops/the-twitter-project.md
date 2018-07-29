# The Twitter Project

## The Twitter Project

Time

* 90 minutes

Requirements

* Laptop
* Internet Connection
* Intel Edison
* Twitter Account
* [Grove Indoor Environment Kit for Intel® Edison](https://www.seeedstudio.com/item_detail.html?p_id=2427)
  * [Grove - Button](http://www.seeedstudio.com/wiki/Grove_-_Button)

    ![](http://www.seeedstudio.com/wiki/images/thumb/c/ca/Button.jpg/300px-Button.jpg)

  * [Grove - LCD RGB Backlight](http://www.seeedstudio.com/wiki/Grove_-_LCD_RGB_Backlight)

    ![](http://www.seeedstudio.com/wiki/images/thumb/0/03/Serial_LEC_RGB_Backlight_Lcd.jpg/500px-Serial_LEC_RGB_Backlight_Lcd.jpg)

## Agenda

* Twitter
* Grove Starter Kit Plus
  * Grove – Button
  * Grove - LCD RGB Backlight
* Core Library + Your Project
  * Source Code Cloning
  * Dependencies Setup
  * Credentials Setup
  * Your Twitter Code
* Challenge

## Twitter

> Twitter is an online social networking service that enables users to send and read short 140-character messages called "tweets". Registered users can read and post tweets, but those who are unregistered can only read them. [Wikipedia](https://en.wikipedia.org/wiki/Twitter)

[Twitter Homepage](https://twitter.com/)

### Important Notes about Twitter!

* Make sure your tweet is not the same to the previous one, have a minor difference e.g.
  * "01 Testing Tweet \#IntelEdison \#IAmIntel"
  * "02 Testing Tweet \#IntelEdison \#IAmIntel"
* Make sure the time between tweets is within the limits

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

## Core Library + Your Project

### Source Code Cloning

```bash
root@edison:~# cd
root@edison:~# mkdir myproject
root@edison:~# cd myproject/
root@edison:~/myproject# git clone https://github.com/xe1gyq/core.git
Cloning into 'core'...
remote: Counting objects: 1109, done.
remote: Compressing objects: 100% (171/171), done.
remote: Total 1109 (delta 93), reused 0 (delta 0), pack-reused 924
Receiving objects: 100% (1109/1109), 217.79 KiB | 0 bytes/s, done.
Resolving deltas: 100% (605/605), done.
Checking connectivity... done.
root@edison:~/myproject#
```

### Dependencies Setup

```bash
root@edison:~/myproject# pip install twython
```

### Credentials Setup

```bash
root@edison:~/myproject# credentials.config
```

```bash
# Twitter
#
# Go to dev.twitter.com and sign up
# Go to Tools -> Manage Your Apps (Application Management)
# Create a New Application and go to "Keys and Access Tokens" tab
# Generate and get under Application Settings section:
#  Consumer Key (API Key), Consumer Secret (API Secret)
# Generate and get under Your Access Token section
#  Access Token and Access Token Secret
# Give Access Level "Read and Write"
[twitter]
consumer_key = 
consumer_secret = 
access_token = 
access_token_secret =
```

### Your Twitter Code

```bash
root@edison:~/myproject# nano twittersample.py
```

```python
#!/usr/bin/python

import ConfigParser
import os

from twython import Twython

class xTwitter(object):

    def __init__(self):

        self.configuration = ConfigParser.ConfigParser()
        self.directorycurrent = os.path.dirname(os.path.realpath(__file__))
        self.configuration.read(self.directorycurrent + '/configuration/credentials.config')
        self.consumer_key = self.configuration.get('twitter','consumer_key')
        self.consumer_secret = self.configuration.get('twitter','consumer_secret')
        self.access_token = self.configuration.get('twitter','access_token')
        self.access_token_secret = self.configuration.get('twitter','access_token_secret')
        self.twythonid = Twython(self.consumer_key, \
                                 self.consumer_secret, \
                                 self.access_token, \
                                 self.access_token_secret)

    def tweet(self, status="", media=None):
        if media:
            photo = open(media,'rb')
            self.twythonid.update_status_with_media(media=photo, status=status)
        else:
            self.twythonid.update_status(status=status)

if __name__ == "__main__":

    idTwitter = xTwitter()
    idTwitter.tweet('#TheIoTLearningInitiative Testing Time')
```

```bash
root@edison:~# python twittersample.py
```

Look at your Twitter account...

### Challenge

> Create an application using Twitter, Button and LCD... Button can be used to push a tweet \(Core library usage will be enough\) and LCD can be used to display latest tweet \(direct usage of Twython API is required\)

