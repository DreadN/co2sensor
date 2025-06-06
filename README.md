# DYI Compact Carbon Dioxide Sensor
This is a little sensor to do one thing, measuring carbon dioxide (CO₂).
Compact and versatile, it can be integrated in home assistant via ESPhome addon or it can be used as standalone sensor with the integrated OLED display.

## ESP32 YAML File:
https://github.com/DreadN/co2sensor/blob/main/wemosoled.yaml

## STL files to print Case, cover and sensor internal locker
https://www.printables.com/model/1319180-compact-co2-sensor-with-oled-display

## Building components:
Heres the shopping cart of things you will need.

- Senseair S8-4B - Aliexpress
- Wemos OLED ESP32 - Aliexpress
- 4x standard Brass Inserts
- 4x M3x40mm screws, cylindrical head
- Micro USB 5W cable (those used to charge old Smartphones)
- Two 2-pin male connector from a PCB pin strip (those coming with ESP32 are ok)
- A floppy disk M3x4 screw and a small o-ring (id 3.5, cs 1) to fix the sensor
- 100mm dupont wire cables - Aliexpress
   - one red for 5V out
   - one black for GND
   - some bright colors for UART (used yellow/orange)
   - optional two cables for Senseair calibration (I used two dupont F connector and a created a male jumper)
    ![image](https://github.com/user-attachments/assets/e499864b-d731-47f4-9980-1e78b6d4d0ac)

 

## Additional tools:
- Soldering station
- Allen Key for M3 screws
- Clippers and cutters for electronics

# ------------------ WARNING ------------------ Read Below before start connecting things ------------------ WARNING ------------------

# Senseair important notes:
Before starting to solder and connect wires it's important to consider these three notes.

1. The sensor has no power inversion protection, so after installing the two pin male connectors on the Senseair, the first thing to do is take a red nail polish and mark the 5V DC pin to avoid inverting +/- power connections. Power inversion will fry the sensor and 25€ will go into the trashcan.
    ![image](https://github.com/user-attachments/assets/74b9426b-9bd1-4497-9c15-85780cb7b134)
    Image: use red nail polish to mark the 5V soldered pins in on the Senseair.
 
2. The sensor is very power efficient, but uses an IR laser to measure CO₂,  so it will pulse every 30 seconds drawing power with peak of 1.5W, adding the power of the ESP32, with WiFi and OLED you will need a 5W USB outlet with a good cable, otherwise it could be unstable.
 
3. RX and TX pins have to be crossed. It took me some time before realizing what we did when we play Doom in high scohool computer room with crossed 9pin serial cables.
Crossed cables have Rx/Tx inverted on one side, so:
    - ESP32 RX goes to sensor TX
    - ESP32 TX goes to sensor RX
 

## Used these pins:
All on the same side to better route cables in the sensor container.
- pin 3 (RX)
- pin 1 (TX)
- GND pin
- 5V pin
See image below for better clarity.
Note: Unless you want a steampunk version of the sensor 😀 you should solder cables exiting on the opposite side of the OLED screen.
 
![image](https://github.com/user-attachments/assets/b7f072cb-ede2-422c-9b27-583f4704a5c2)
