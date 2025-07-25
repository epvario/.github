# Open-source e-Paper Variometer for Paragliding

<img align="right" height="200" alt="403388137-8c4eb38d-10e6-4f49-a6d1-fa12b550919c" src="https://github.com/user-attachments/assets/311c134d-0fa0-4c66-8a85-0490252111ef" />


EPVario is an open source and open hardware variometer for paragliding, designed to be mounted on your risers, its just above 80g. 

Core component is a RP2040 microcontroller, the flagship chip designed by Raspberry Pi in the UK, and a WeAct Studio, 2.9 Inch, Epaper module providing a future proof hardware platform with excellent readability, even in direct sunlight.

Full access to the design files of the 3D printed case offer great options for other mounting systems on cockpits or shoudler straps for tandem pilots.

The main component, a single PCB holding most components, can be ordered fully assembled at PCB manufacturers easily through the provided KiCAD design files.

Join us on telegram here: https://t.me/+4pXlLXE_beo4ZTI0

![image](https://github.com/user-attachments/assets/b1dfbc78-c23f-4806-93fc-69b596cbea38)

<img width="800" alt="image" src="https://github.com/user-attachments/assets/4dd2d3aa-1ad8-4e8d-8e13-0699db8e57dd" />


### Software Features:
- Firmware written in **RUST**, providing great memory safety, fast code execution and a broad compatibility and easy to ugprade
  - just drag and drop a firmware file to the USB connected vario from your PC or mobile
- Numerical Variometer on the display
- Altitude aMSL
- Groundspeed and Glideratio
- Compass with flight direction
- Windspeed- and direction estimator
- FAI CIVL approved IGC tracklog signing (G-record)
- Flight and Landing detection, Flighttimer and Post-Flight Statistics
<img width="250" alt="image" src="https://github.com/user-attachments/assets/be6a5a36-a03f-4e30-9590-4b452bdb9be1" />

### Hardware Features:
- **RP2040**, dual-core Arm Cortex-M0+ processor
- power saving Epaper, WeAct Studio **2.9 Inch Epaper** Module
- 3.3V architecture using TPS6303 voltage regulator
- **L5M6DS3** IMU for accelerometer and gyro data fusion
- **BMP280** pressure sensor 
- **M10UBX** GPS module (supporting GLONASS, BDSB, GALILEO, SBAS, QZSS)
- QMC5883 compass
- **MicroSD** cardslot for flight path logging
- **1W speaker** for excellent acustic (30x20cm)
- **USB-C** connector
- MAX90357AEWL+T speaker amplifier
- integrated **1100mAh Lipo**
- USB-C lipo charger (MCP73871)
- user interface with 3 buttons 
- compact size and low weight
- 3D printed case with multiple attachment options
- 80-85g
- more than 15h runtime
<img width="250" alt="image" src="https://github.com/user-attachments/assets/7cce3a8f-e439-465d-8b93-4244affa9d08" />

### Part list:
- epVario PCB
- WeAct Studio 2.9" EPaper Module
- Walksnail WS-M181 GPS + compass
- EEMB LP603449 1100mAh lipo battery (51x35x6.3mm)
- Adafruit 4227 1W 8 Ohm Speaker or similiar (30x20mm)
- microSD card, not larger than 32GB (preferably SanDisk)
- 3D printed case

### Instructions:
#### Build the code:
#### Get the parts:
#### Print the case:
#### Assembly:
#### Initial setup (v0.1.3):
- Format the SD card with FAT32
- optional: place a textfile named "config.txt" with a JSON content like:  
  - ```
    {"pilot_name": "your name",
    "glider_type":"myWing",
    "utc_time_offset": "+0200",
    "startup_volume": "Medium",
    "display_version": 1}
    ```
  - _more options parameters to come_
  - **always supply all parameters!**
- start the device in flash/bootsel mode by pressing and hold the volume up and power button for 5 seconds
- connect the device to a PC or mobile phone
- drag and drop the firmare.uf2 file to the mounted mass storage device named "RPI-RP2"
- once uploaded, the vario will automatically reboot and can be disconnected

#### Usage (v0.1.2):
- Press and hold the upper, power button for 3 seconds to turn the device on or off
- Use the side buttons to increase or decrease the volume level
- **Takeoff:** detection will now determine your location and altitude via GPS
  - the SAT count on the top left will increase & the Flighttimer will show "locating"
  -  Flighttimer will show "--:--:--" once location is complete
  - At this stage the vario will buffer a tracklog until takeoff is detected
    - A groundspeed of >2m/s for a duration of 5 seconds will start the flighttimer (preserving the time&data before)
- **Flying:**
  - The compass element will start working once a heading is obtained
  - The wind estimator will deliver data (and continue updating) once a full cycle has been flown
    - The gathered data will outage after 10min, so the information might disappear when flying into a single direction for longer time
  - After each 10min, the screen will be flushed (once drawn black and white) and draw a clear display on the e-Paper screen.
- **Landing** will be detected if groundspeed is less than <2m/s for 15 seconds
  - The vario will now finish the IGC logging and display your flight statistics until any of the volume buttons is pressed

#### Troubleshooting & Updating: 
- hard reset:
  - press and hold the power and volume up button for 15 seconds to perform a hard reset if necessary
- firmware upgrade:
  - when turned off, press and hold the power button and volume up button for 5 seconds to enter flashing/bootsel mode.
  - a mass storage device does now appear when plugged into a computer or phone, copy a firmware.uf2 file here to upgrade your device

#### Release Notes:
- v0.1.3
  - new: ... 
- v0.1.2
  - new: button tones
  - new: takeoff and landing tones
  - new: offset for UTC clock, default +0200, config: utc_time_offset
  - new: max g_force on stats screen
  - new: show post flight stats until a button is pressed or shutdown is initiated
  - fix: initial ghosting after power on
- v0.1.1
  - new: improve IGC B-record
  - fix: formatting of windspeed estimator causing device freeze
- v0.1.0 
  - initial release

#### ... coming soon:
- Altitude above groundlevel
- variometer graph
- browse flight history and statistics on device
- Flightlevel warnings
- FANET integration
- UI improvements and more :)
