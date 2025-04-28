original project at: https://github.com/madewhatnow/TFmini-I2C-Python

compatible with a TF mini and TF mini plus I2C
## Basic usage

The TFmini_I2C.py file contains the necessary definitions and examples.

A sensor is initalized by passing the identifier for the I2C bus and the sensor address:
```
 Sensor0 = TFminiI2C()
```
Reading the sensor is very simple and fast. The first command reads the full return of the sensor and returns four values:
```
  print(Sensor0.readAll())
```

The second command performs the same read, but only returns the distance measurement as a single value. Standard unit is cm, but can be changed to mm, see further below.
```
  print(Sensor0.readDistance())
```
## Changing settings

Once a sensor is intialized, settings can be adjusted:
```
  Sensor0.setUnit(0x00)
  Sensor0.setRange(0x07)
```
The first command changes the sensor output to millimeter (instead of centimeter), the second changes the standard automatic range settings (short, medium or long range) to a fixed range. 

Similarly, both a 'soft' reset (to activate settings) or a 'reset to manufacturer default' can be called:
```
  Sensor1.reset()
  Sensor1.resetdefault()
```
The standard I2C address of the sensor is 0x10, but can be changed in the range from 0x10 to 0x78. The manual suggests that a soft reset is sufficient to activate the change, in my hands a power cycle is required. The address change is permanent, and survives both types of reset.
```
  Sensor0.setAddress(0x11)
```

Reading the sensor is fast. On a Raspberry Pi 4, the distance values for 3 different sensors are returned in around 4 milliseconds total. 

Enjoy!






