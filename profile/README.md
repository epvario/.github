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

## ... comming soon:

#### Features:
- Altitude above groundlevel
- Flightlevel warnings
- FANET integration
- Access logged flights through the buttons
- UI improvements and more :)

#### Instructions:
##### build the code:

##### get the parts:

##### print the case:

##### assembly and initial configuration:

##### usage:
