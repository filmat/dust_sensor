## Howto: dust sensor HW

### Overview

This project is an open hardware project aimed for intermediate software developers and electronics engineers (as well as others, provided they've got someone of the electronics background at hand).
The idea behind the project is to provide _**cheap and easy to build**_ **dust sensor** that will measure **PM2.5, PM10**, Temperature and Humidity, display those on the LCD and be able to send the values onto dedicated server (e.g. http get).

Here's how the prototype looks like. 
![alt tag](https://cloud.githubusercontent.com/assets/10147619/21928626/397b864e-d98c-11e6-9f66-f164af51738c.JPG)

We've succesfully build few of those already. Using simple plexi enclosure. And they work like a charm.

### Parts list

In order to build one of your own, you'll need following pieces of HW:
* PCB
In this git one can find _kicad-ESP8266_ and _GERBERS_ directories. This is a schematics for PCB used in our project.
Please refer to [PCB](#pcb) section, there will be more about that there.
* PCD8544 48x84 pixels LCD display
Please note, that there're few versions of the Nokia 5110 LCD boards. One will need one with following order of GOLDPINs:
  * 1 - RST
  * 2 - CE
  * 3 - DC
  * 4 - DIN
  * 5 - CLK
  * 6 - VCC
  * 7 - LIGHT
  * 8 - GND
  
As for example one in the middle in following pictures:

![alt tag](https://cloud.githubusercontent.com/assets/10147619/21928618/3952b46c-d98c-11e6-8f49-6d78fa65f966.JPG)![alt tag](https://cloud.githubusercontent.com/assets/10147619/21928623/39577998-d98c-11e6-83f4-8a9756973731.JPG)

Other two will require either some type of wire instead of just goldpins to connect proper inputs/outputs (the one on the left) or may cause the backlight of the LCD to be always ON (one on the right; not sure why though).
Approx cost: <$2

* AM2302/DHT22 digital-output relative humidity & temperature sensor

 This is an easy to get item. One can also consider using lower-cost lower-precission DHT11. 
 Further reading: [Digital relative humidity & temperature sensor AM2302/DHT22](https://cdn-shop.adafruit.com/datasheets/Digital+humidity+and+temperature+sensor+AM2302.pdf)
 
 Approx cost: <$2

* SDS011 Laser PM2.5 Sensor

 This is the most expensive and most important part of the device. It's easily available on the internet. Best prices spoted in China ;-) 
 Further reading: [Laser PM2.5 Sensor specification](http://inovafitness.com/software/SDS011%20laser%20PM2.5%20sensor%20specification-V1.3.pdf)
 
 Approx cost: $22-$25
 
* ESP8266-12F (optionally ESP8266-12E) MCU

 Please be carefull when buying ESP8266, a _heart of the device_. You'll need very specific version of it: ESP-12F. You can optionally replace it with ESP-12E, which is better available in Europe, but it is not FCC approved and may cause some problems due to this and the fact it's got a little bit worse antena. More details: [ESP8266 Wiki](https://en.wikipedia.org/wiki/ESP8266)
 
 Approx cost: <$2
 
* PCF8574AT: Remote 8-bit I/O expander for I2C-bus with interrupt

 Expander is needed, hence we've used all the GPIO ports of ESP-12E/F. This is due to the fact, that the SDS011 uses UART to communicate with the external world (needs 2 pins of ESP) and there's LCD & THT on top of that. The extender is talking with the ESP using only two pins over I2C protocol.
 
 Approx cost: TODO

* optional: Plexi enclosure, screws, etc - to keep it all together

 This is optional, but we've put the drawings for both bottom and top of the enclosure in this git. You may find it [here](https://github.com/kadamski/dust_sensor/tree/master/enclosure)
 
 Approx cost: TODO

#### PCB

### Putting things together

### Getting firmware
