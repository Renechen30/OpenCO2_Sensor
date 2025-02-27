# OpenCO2 Sensor using ESP32 and SCD4x

![alt text](https://github.com/davidkreidler/OpenCO2_Sensor/raw/main/pictures/Header.png)
 
OpenCO2 Sensor is an Arduino IDE compatible Repository for an E-Ink Indoor air quality CO2 Sensor using the ESP32-S2 and an RBG LED.

## Buy it [here on Tindie](https://www.tindie.com/products/davidkreidler/open-co2-sensor/)

Especially in winter, when the windows are closed, a reminder to ventilate regularly is useful for health, 
comfort and well-being. Poor indoor air quality can lead to decreased productivity and learning disabilities.
Therefore, I developed an ESP32-S2 project that uses an E-Ink display to show the indoor CO2 content. 
Comparable commercial meters cost significantly more and have fewer features.

# CO2 sensor
With the SCD40, Sensirion offers a completely new miniaturized CO2 sensor based on the photoacoustic sensor principle.
The integrated, industry-leading humidity and temperature sensor offers high accuracy with low power consumption.

# Clear E-Ink display
1.54" in size, with 200x200 pixel resolution and low power consumption with wide viewing angle. Per partial refresh, readings are updated every five seconds.

# RGB LED
For displaying the air quality as a traffic light (green, yellow, red, magenta). Brightness and color are adjustable via software.

# 3D-printed housing
size: 47 x 41 x 24 mm
* [3D File BACK](https://raw.githubusercontent.com/davidkreidler/OpenCO2_Sensor/main/case/BACK.obj)
* [3D File FRONT](https://raw.githubusercontent.com/davidkreidler/OpenCO2_Sensor/main/case/FRONT.obj)

Use "Save as" to download the files.

![alt text](https://github.com/davidkreidler/OpenCO2_Sensor/raw/main/pictures/drawing.png)

# Wi-Fi
By means of the ESP32-S2 processor on a self-designed PCB, an APP connection via software update is planned.
Thus, push notifications windows (open / close) and long-term measurements are possible.

# Update to the latest release

1. Download and unzip [esptool](https://github.com/espressif/esptool)
2. Download the all `.bin` files from the latest [release](https://github.com/davidkreidler/OpenCO2_Sensor/releases)
3. Make sure, that the power switch is in the `ON` position (down)
4. Plug a data USB-C cable into your PC and the Sensor
5. Hold the Button on the backside of the CO2 Sensor near the USB-C port and push simultaneously the reset ↪️ Button
6. Release the reset ↪️ Button first and then the other one
7. Run the following commands in the folder containing the `.bin` and `esptool`
   port for Windows: `COM7` or Linux: `/dev/ttyUSB0`|`/dev/ttyACM0`
```
$ python3 -m pip install pyserial
$ python3 esptool.py --chip esp32s2 --port [COM7|/dev/ttyUSB0|/dev/ttyACM0] --baud 921600 --before default_reset --after hard_reset write_flash -z --flash_mode dio --flash_freq 80m --flash_size 4MB 0xe000 boot_app0.bin 0x1000 co2_scd4x.ino.bootloader.bin 0x10000 co2_scd4x.ino.bin 0x8000 co2_scd4x.ino.partitions.bin
```
7. Afterwards push the reset ↪️ Button

# Installation

1. Copy the esp32-waveshare-epd Folder to your `Arduino/libraries/`
2. [Install the ESP32-S2 support for Arduino IDE](https://espressif-docs.readthedocs-hosted.com/projects/arduino-esp32/en/latest/installing.html)
3. Choose `ESP32S2 Dev Module` under `Tools -> Boards -> ESP32 Arduino`
4. Connect the Sensor as described in step "Programming via Arduino IDE" and choose the new Port under `Tools -> Boards -> Port`

# Dependencies

* [Adafruit DotStar version 1.1.5](https://github.com/adafruit/Adafruit_DotStar/tree/1.1.5)
* [Sensirion Core](https://github.com/Sensirion/arduino-core)
* [Sensirion I2C SCD4x Arduino Library](https://github.com/Sensirion/arduino-i2c-scd4x)

# Programming via Arduino IDE

* Make sure, that the power switch is in the `ON` position (down)
* Plug a data USB cable into your PC and the Sensor
* Hold the Button on the backside of the CO2 Sensor near the USB-C port and push simultaneously the reset ↪️ Button
* Release the reset ↪️ Button first and then the other one

* Click `Upload` in the Arduino IDE and wait
* Afterwards push the reset ↪️ Button

# German translation OpenCO2 Sensor

Vor allem im Winter bei geschlossenen Fenstern ist eine Erinnerung, regelmäßig zu lüften, sinnvoll für die Gesundheit, 
den Komfort und das Wohlbefinden. Schlechte Raumluftqualität kann zu verminderter Produktivität und Lernstörungen führen.
Daher habe ich ein ESP32-S2 Hobby Projekt entwickelt, welches mittels eines E-Ink Displays den CO2 Gehalt der Luft anzeigt. 
Vergleichbare kommerzielle Messgeräte kosten deutlich mehr und besitzen weniger Features.

# CO2-Sensor
Mit dem SCD40 bietet Sensirion einen völlig neuen miniaturisierten CO2-Sensor, welcher auf dem photoakustischen Sensorprinzip basiert.
Der integrierte, branchenführende Feuchte- und Temperatursensor bietet eine hohe Genauigkeit bei einem geringen Energieverbrauch.

# Klares E-Ink-Display
1,54” groß, mit einer Auflösung von 200x200 Pixeln und niedrigem Stromverbrauch bei breitem Betrachtungswinkel. Per partiellem Refresh werden die Messwerte alle fünf Sekunden aktualisiert.

# RGB-LED
Zur Darstellung der Luftqualität als Ampel (grün / gelb / rot). Helligkeit und Farbe sind per Software einstellbar.

# 3D-Gedrucktes Gehäuse
Größe: 47 x 41 x 24 mm
* [3D File BACK](https://raw.githubusercontent.com/davidkreidler/OpenCO2_Sensor/main/case/BACK.obj)
* [3D File FRONT](https://raw.githubusercontent.com/davidkreidler/OpenCO2_Sensor/main/case/FRONT.obj)

Benutze "Speichern unter" um die Dateien herunter zu laden.

# WLAN
Mittels des ESP32-S2 Prozessors auf einem selbst designten PCB ist eine APP Anbindung per Software Update geplant.
Somit sind Push Benachrichtigungen Fenster (auf / zu) und Langzeitmessungen möglich.

![alt text](https://github.com/davidkreidler/OpenCO2_Sensor/raw/main/pictures/animation.gif)

![alt text](https://github.com/davidkreidler/OpenCO2_Sensor/raw/main/pictures/schematic.png)

![alt text](https://github.com/davidkreidler/OpenCO2_Sensor/raw/main/pictures/pcb.png)
