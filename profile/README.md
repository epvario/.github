# [EPVario]  state of the art open-source E-Paper Variometer for Paragliding

EPVario is a powerful open source variometer for paragliding, designed to be mounted on your risers.

Core component is a RP2040 microcontroller, the flagship chip designed by Raspberry Pi in the UK, and a WeAct Studio, 2.9 Inch, Epaper module providing a future proof hardware platform with excellent readability, even in direct sunlight.

Full access to the design files of the 3D printed case offer great options for other mounting systems on cockpits or shoudler straps for tandem pilots.

The main component, a single PCB holding most components, can be ordered fully assembled at PCB manufacturers easily through the provided KiCAD design files.

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
<img width="252" alt="image" src="https://github.com/user-attachments/assets/1f4ca641-3fc2-4881-8fe6-9fa85e84d0f9" />

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

### Part list:
- epVario PCB
- WeAct Studio 2.9" EPaper Module
- Walksnail WS-M181 GPS + compass
- EEMB LP603449 1100mAh lipo battery (51x35x6.3mm)
- Adafruit 4227 1W 8 Ohm Speaker or similiar (30x20mm)
- 3D printed case

### Instructions:
#### build the code:
#### get the parts:
#### print the case:
#### assembly:
#### initial setup (v0.9.2):
- the current filesystem crate supports only FAT32 without MBR!
- start the device in flash/bootsel mode press and hold the power button and volume up button for 5 seconds
- connect the device to a PC or mobile phone
- copy a firmare.uf2 file to mounted mass storage device
- after upload the vario will automatically reboot and can be disconnected

#### usage (v0.9.2):
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
  - After 10min of runtime, the screen will be flushed (once drawn black and white) to reduce ghosting on the e-Paper screen.
- **Landing** will be detected if groundspeed is less than <2m/s for 15 seconds
  - The vario will now finish the IGC logging and display your flight statistics for 2 minutes
  - if a shutdown will be initiated while stats are shown, they will be preserved on the screen after turning off
- After 2 minutes are elapsed, the vario will continue in takeoff-detection mode
  - if a shutdown will be initiated in this state, the screen will be cleared    

#### Troubleshooting & Updating: 
- press and hold the power and volume up button for 15 seconds to perform a hard reset if necessary
- when turned off, press and hold the power button and volume up button for 5 seconds to enter flashing/bootsel mode.
  - a mass storage device does now appear when plugged into a computer or phone, copy a firmware.uf2 file here to upgrade your device

#### ... coming soon:
- Altitude above groundlevel
- variometer histogram
- Flightlevel warnings
- browse flight history and statistics on device
- FANET integration
- UI improvements and more :)
