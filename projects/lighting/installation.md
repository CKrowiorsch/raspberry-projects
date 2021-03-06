# Installtionsprozess LED-Strip

* Setup raspberry
* Update System
* Install Python + pip `sudo apt-get install python3-pip python3-rpi.gpio`
* einschalten IC2 +  SPI in `sudo raspi-config`
  * install IC2 Libs `sudo apt-get install -y python-smbus i2c-tools`
  * Check IC2 `sudo i2cdetect -y 1`
  * Check SPI `ls -l /dev/spidev*`
* Second SPI `dtoverlay=spi1-3cs`
* Python-Libaries
  * `pip3 install RPI.GPIO adafruit-blinka`
  * `sudo pip3 install rpi_ws281x adafruit-circuitpython-neopixel`

## Check Installation

```python
import board
import digitalio
import busio

print("Hello blinka!")

# Try to great a Digital input
pin = digitalio.DigitalInOut(board.D4)
print("Digital IO ok!")

# Try to create an I2C device
i2c = busio.I2C(board.SCL, board.SDA)
print("I2C ok!")

# Try to create an SPI device
spi = busio.SPI(board.SCLK, board.MOSI, board.MISO)
print("SPI ok!")

print("done!")
```

## Program Leds

```python
import board
import neopixel
pixels = neopixel.NeoPixel(board.D18, 30) # Raspberry Pi wiring!

# Set Color
pixels[0] = (0,255,0)
# Set Brightness
pixels.brightness = 0.5
```

## Sources

<https://learn.adafruit.com/adafruit-neopixel-uberguide/python-circuitpython#python-installation-of-neopixel-library-17-9>
