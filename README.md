# DYI Compact Carbon Dioxide Sensor
This is a little sensor to do one thing, measuring carbon dioxide (CO₂).
Compact and versatile, it can be integrated in home assistant via ESPhome addon or it can be used as standalone sensor with the integrated OLED display.

These are output from Home assistant and standalone sensor use.

![image](https://github.com/user-attachments/assets/cd0deb60-f2c0-48a8-9633-71669b5ef117)
![image](https://github.com/user-attachments/assets/197fe93d-e885-47ad-9ec9-5b6cf75c0da1)

>[!IMPORTANT]
>## ESP32 YAML File:
>https://github.com/DreadN/co2sensor/blob/main/wemosoled.yaml
>
>## STL files to print Case, cover and sensor internal lock
>https://www.printables.com/model/1319180-compact-co2-sensor-with-oled-display

## Building components:
Heres the shopping cart of things you will need.

- Senseair S8-4B - [Aliexpress](https://it.aliexpress.com/item/1005002961668404.html?spm=a2g0o.productlist.main.1.595d10edwR3ObB&algo_pvid=44fbad28-745e-4e0e-90b8-7248146a09d8&algo_exp_id=44fbad28-745e-4e0e-90b8-7248146a09d8-0&pdp_ext_f=%7B%22order%22%3A%227%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%2126.30%2124.79%21%21%2129.33%2127.65%21%402103856417491526812864680e0788%2112000022975722048%21sea%21IT%214060411391%21X&curPageLogUid=Ww6AxBZZRw9D&utparam-url=scene%3Asearch%7Cquery_from%3A)
- Wemos OLED ESP32 - [Aliexpress](https://it.aliexpress.com/item/1005006216570195.html?spm=a2g0o.productlist.main.6.24c83be7Ty90pz&algo_pvid=453d590f-517b-4825-adaf-4b72fde40c77&algo_exp_id=453d590f-517b-4825-adaf-4b72fde40c77-5&pdp_ext_f=%7B%22order%22%3A%224%22%2C%22eval%22%3A%221%22%7D&pdp_npi=4%40dis%21EUR%216.45%216.45%21%21%217.19%217.19%21%402103956b17491569386441748ecd7a%2112000038604869263%21sea%21IT%214060411391%21X&curPageLogUid=hGldiXjtyOav&utparam-url=scene%3Asearch%7Cquery_from%3A)
- 4x standard Brass Inserts
- 4x M3x40mm screws, cylindrical head
- Micro USB 5W cable (those used to charge old Smartphones)
- Two 2-pin male connector from a PCB pin strip (those coming with ESP32 are ok)
- A floppy disk M3x4 screw and a small o-ring (id 3.5, cs 1) to fix the sensor
- 100mm dupont wire cables - [Aliexpress](https://it.aliexpress.com/item/1005006050213130.html?spm=a2g0o.order_list.order_list_main.24.3f0d3696vC5eVG&gatewayAdapt=glo2ita)
   - one red for 5V out
   - one black for GND
   - some bright colors for UART (used yellow/orange)
   - optional two cables for Senseair calibration (I used two dupont F connector and a created a male jumper)
    ![image](https://github.com/user-attachments/assets/e499864b-d731-47f4-9980-1e78b6d4d0ac)


## Additional tools:
- Soldering station
- Allen Key for M3 screws
- Clippers and cutters for electronics

>[!CAUTION]
># Senseair important notes:
>Before starting to solder and connect wires it's important to consider these three notes.

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
>[!TIP]
>Unless you want a steampunk version of the sensor 😀 you should solder cables exiting on the opposite side of the OLED screen.
 
![image](https://github.com/user-attachments/assets/b7f072cb-ede2-422c-9b27-583f4704a5c2)

## Final Assembly
![image](https://github.com/user-attachments/assets/9f67c6c6-6477-4c82-8a06-a96097f0c152)
![image](https://github.com/user-attachments/assets/36c3a4c3-f153-42c6-966b-a2f49860d342)

